<script>
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';
    import Scroller from "@sveltejs/svelte-scroller";
  
    let count, index, offset, progress;
    index = 0;
    let width, height;
  
    let visualizations_hidden = true;
    $: {
      if (index === 0 || index > sections.length) {
        visualizations_hidden = true;
      } else if (offset > .6) {
        visualizations_hidden = false;
      }
    }
  
    let sections = [
        {
            title: 'Recipes and Ratings Exploratory Data Analysis Project',
            content: `yap`,
            // content: `This project involves an in-depth exploratory data analysis of a Recipes and Ratings dataset. By applying various statistical methods and visualization techniques, I uncovered insightful trends and patterns that could significantly impact culinary practices and preferences.`,
            imageUrl: 'RReda.png',
            imageClass: 'project-image',
            projTitle: 'Check out my Recipes and Ratings EDA here!',
            id: 'project1',
            technologies: 'Technologies used: yap',
            link: 'https://keenans04.github.io/RecipesAndRatings/'
        },
        {
            title: 'Recipes and Ratings Pipelines and Modeling Project',
            // content: `Focusing on automating data processing and modeling for the Recipes and Ratings dataset, this project streamlines the workflow through pipelines. The goal was to enhance efficiency and reproducibility, ensuring that the data analysis process is more structured and accessible.`,
            content: `yap`,
            imageUrl: 'RRmodel.png', 
            imageClass: 'project-image',
            projTitle: 'Check out my Recipes and Ratings Model here!',
            id: 'project2',
            technologies: 'Technologies used: yap',
            link: 'https://keenans04.github.io/WhatsTheRating/'
        },
        {
            title: 'LeGOAT: The LeBron James\'s Career Narrative',
            // content: `A captivating scrollytelling narrative that explores the illustrious career of LeBron James. Using D3.js for interactive storytelling, this project presents LeBron's journey from a promising young talent to one of the greatest basketball players of all time.`,
            content: `yap`,
            imageUrl: 'LeGoat.png',
            imageClass: 'project-image',
            projTitle: 'Check out my Lebron James Narrative here!',
            id: 'project3',
            technologies: 'Technologies used: yap',
            link: 'https://keenans04.github.io/LeGOAT/'
        },
        {
            title: 'PowerAtlas: Navigating Global Energy Consumption',
            // content: `PowerAtlas offers an immersive exploration of global energy consumption patterns through interactive data visualizations. This project was designed to provide insights into how different countries consume energy, using advanced data analysis and D3.js to create an engaging, interactive web experience. It highlights the disparities in energy usage and the impact of renewable energy sources across the globe.`,
            content: `yap`,
            imageUrl: 'PowerAtlas.png',
            imageClass: 'project-image',
            projTitle: 'Check out my PowerAtlas here!',
            id: 'project4',
            technologies: 'Technologies used: yap',
            link: 'https://keenans04.github.io/PowerAtlas/'
        },
        {
            title: 'Valorant EDA: Analyzing the Skill Gap',
            // content: `This exploratory data analysis (EDA) dives deep into the competitive world of Valorant, analyzing the skill gap between individual players from different regions. By scrutinizing player data and performance metrics, this project sheds light on the factors that contribute to a player's success and how different regions compare in terms of skill level and competitive play style.`,
            content: `yap`,
            imageUrl: 'LeGoat.png',
            imageClass: 'project-image',
            projTitle: 'Check out my Valorant EDA here!',
            id: 'project5',
            technologies: 'Technologies used: yap',
            link: 'https://github.com/ansh-mujral/Valorant_EDA' 
        },
        {
            title: 'Contact Me',
            type: 'contact',
            content: `Your descriptive text here. Feel free to reach out through any of the following methods:`,
            contactMethods: [
                { name: 'Email', icon: 'fas fa-envelope', link: 'mailto:amujral@ucsd.edu' },
                { name: 'LinkedIn', icon: 'fab fa-linkedin', link: 'https://www.linkedin.com/in/amujral/' },
                { name: 'GitHub', icon: 'fab fa-github', link: 'https://github.com/ansh-mujral' },
                { name: 'Resume', icon: 'fas fa-file-text-o', link: 'AnshMujralResume_Mar2024.pdf' },
            ]
        }
    ];
  
  </script>
  
  <Scroller
    top={0.0}
    bottom={1}
    threshold={1}
    bind:count
    bind:index
    bind:offset
    bind:progress
  >
    <div class="background" slot="background" bind:clientWidth={width} bind:clientHeight={height}>
      <div style="transition: opacity 0.5s; opacity: {visualizations_hidden ? 0 : 1}">
      </div>
    </div>
      
    <div class="foreground" slot="foreground">
        <section id="about-me" class="hero">
            <h1 class="name" >Ansh Mujral: About Me</h1>
            <div class="about-me-grid">
                <div class="about-me-column">
                    <h2>Interests and Hobbies</h2>
                    <p>Your interests and hobbies here.</p>
                </div>
                <div class="about-me-column">
                    <h2>About Me</h2>
                    <p>Your basic description here.</p>
                    <img class="me" src="me.png" alt="Ansh Mujral">
                </div>
                <div class="about-me-column">
                    <h2>Experiences</h2>
                    <p>Your experiences here.</p>
                </div>
            </div>
        </section>
        {#each sections as section, i}
        <section class="scrollable-section">
            {#if section.type === 'contact'}
              {#if i+1 === index}
                    <div class="content" in:fade={{duration: 400}} out:fade={{duration: 500}}>
                        <h1 class='title-content'>{section.title}</h1>
                        <p>{section.content}</p>
                        <div class="contact-methods">
                            {#each section.contactMethods as method}
                                <div class="contact-method">
                                    <a href={method.link} title={method.name}><i class={method.icon}></i> {method.name}</a>
                                </div>
                            {/each}
                        </div>
                    </div>
                {/if}
              {:else}
                {#if i+1 === index}
                    <div class="content" in:fade={{duration: 400}} out:fade={{duration: 500}}>
                        <div class="project-description">
                            <h1 class='title-content'>{section.title}</h1>
                            <p>{section.content}</p>
                            <p>{section.technologies}</p>
                            <a href={section.link} target="_blank" rel="noopener noreferrer">Check out My Project Here!</a>
                            <br>
                            {#if section.imageUrl}
                                <img src={section.imageUrl} alt={section.title} class="project-image"/>
                            {/if}
                        </div>
                    </div>
                {/if}
            {/if}
        </section>
        {/each}
    </div>
  </Scroller>
  
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');
    @import 'https://fonts.googleapis.com/css?family=Shrikhand|Yantramanav';
    @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&display=swap');
  
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes slideInLeft {
      from { transform: translateX(-100%); }
      to { transform: translateX(0); }
    }
    @keyframes slideInBottom {
      from { transform: translateY(100%); }
      to { transform: translateY(0); }
    }
  
    @keyframes slideInFromLeft {
      from { transform: translateX(-100%); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }
  
    @keyframes slideInFromTop {
      from { transform: translateY(-100%); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }
  
    :global(body) {
        background: linear-gradient(to right, #c89f76, #dbc6a5, #d2b48d); 
    }
    .about-me-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 20px;
        padding: 20px;
        animation: slideInBottom 0.75s ease-out forwards;
    }

    .name{
      animation: slideInFromTop 0.75s ease-out forwards;
    }
    /* #about-me{
      animation: slideInFromLeft 1s ease-out forwards;
    } */

    .about-me-column {
        background-color: rgba(255, 255, 255, 0.7);
        border-radius: 15px;
        padding: 20px;
        text-align: center;
        border: black 2px solid;
    }
    .contact-description {
        background-color: rgba(255, 255, 255, 0.8);
        margin: 20px 0;
        padding: 15px;
        border-radius: 10px;
    }

    .contact-methods {
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
        padding: 20px;
        border-radius: 10px;
    }

    .contact-method {
        /* margin: 10px;
        padding: 15px; */
    }

    .contact-method a {
        text-decoration: none;
        color: #007bff; 
        display: flex;
        align-items: center;
        gap: 10px;
    }

    .contact-method a:hover {
        color: #0056b3;
        text-decoration: underline;
    }
    
    .subhead {
      animation: slideInFromTop 0.5s ease-out forwards;
    }

    section {
      font-family: 'Monaco', sans-serif;
      height: 100vh;
      text-align: center;
      max-width: 100%; 
      color: black;
      padding: 2em;
      margin: 0 0 0 0;
      border-radius: 6px;
    }
  
    .scrollable-section {
      position: sticky;
      top: 0;
    }

    .project-image {
        max-height: 50vh;
    }
  
    .foreground {
      width: 100%;
      margin: 0 auto;
      height: auto;
      position: relative;
    }
  
    .hero h1 {
      font-size: 3em;
    }

    .hero{
        color: black;
    }
  
    .content {
      height: 93vh;
      width: 95vw;
      position: absolute;
      border: black 2px solid;
      border-radius: 16px;
      background-color: rgba(255, 255, 255, 0.5);
    }
  
    .content h1 {
      font-size: 2em;
      margin-top: 20px;
    }
  
    .content h1 {
      font-size: 2em;
      margin-top: 20px;
    }

    .content img{
        padding: 10px;
    }
    .me {
      height: 40vh;
    }

    .container {
      height: 95vh;
    }
    h1 {
      font-family: 'Monaco', sans-serif;
      font-size: 3em; 
      font-weight: 700;
      letter-spacing: 2px;
    }
    .title-content{
      padding-left: 5px;
      padding-right: 5px;
    }
    .dropdown {
    position: fixed;
    top: 0;
    right: 0;
    padding: 20px;
    }

    .container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: 10px;
  padding: 40px;
  justify-items: center;
  align-items: center;
}

.contact-item {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  padding: 20px;
  background-color: rgba(255, 255, 255, 0.7);
  border-radius: 15px;
  margin: 5px; 
  width: calc(50% - 10px);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.contact-link {
  color: #007bff;
  text-decoration: none;
  font-weight: bold;
  margin-top: 15px;
}
  
  </style>
  