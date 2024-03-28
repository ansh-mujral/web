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

    // function navigateToSection(sectionIndex) {
    //     index = sectionIndex;
    // }

    // let dropdownOpen = false;
  
    // function toggleDropdown() {
    //     dropdownOpen = !dropdownOpen;
    // }
  
    let sections = [
        {
            title: 'Recipes and Ratings Exploratory Data Analysis Project',
            content: `This project involves an in-depth exploratory data analysis of a Recipes and Ratings dataset. By applying various statistical methods and visualization techniques, I uncovered insightful trends and patterns that could significantly impact culinary practices and preferences.`,
            imageUrl: 'RReda.png',
            imageClass: 'project-image',
            id: 'project1',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://keenans04.github.io/RecipesAndRatings/'
        },
        {
            title: 'Recipes and Ratings Pipelines and Modeling Project',
            content: `Focusing on automating data processing and modeling for the Recipes and Ratings dataset, this project streamlines the workflow through pipelines. The goal was to enhance efficiency and reproducibility, ensuring that the data analysis process is more structured and accessible.`,
            imageUrl: 'RRmodel.png', 
            imageClass: 'project-image',
            id: 'project2',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://keenans04.github.io/WhatsTheRating/'
        },
        {
            title: 'LeGOAT: The LeBron James\'s Career Narrative',
            content: `A captivating scrollytelling narrative that explores the illustrious career of LeBron James. Using D3.js for interactive storytelling, this project presents LeBron's journey from a promising young talent to one of the greatest basketball players of all time.`,
            imageUrl: 'LeGoat.png',
            imageClass: 'project-image',
            id: 'project3',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://keenans04.github.io/LeGOAT/'
        },
        {
            title: 'PowerAtlas: Navigating Global Energy Consumption',
            content: `PowerAtlas offers an immersive exploration of global energy consumption patterns through interactive data visualizations. This project was designed to provide insights into how different countries consume energy, using advanced data analysis and D3.js to create an engaging, interactive web experience. It highlights the disparities in energy usage and the impact of renewable energy sources across the globe.`,
            imageUrl: 'PowerAtlas.png',
            imageClass: 'project-image',
            id: 'project4',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://keenans04.github.io/PowerAtlas/'
        },
        {
            title: 'Valorant EDA: Analyzing the Skill Gap',
            content: `This exploratory data analysis (EDA) dives deep into the competitive world of Valorant, analyzing the skill gap between individual players from different regions. By scrutinizing player data and performance metrics, this project sheds light on the factors that contribute to a player's success and how different regions compare in terms of skill level and competitive play style.`,
            imageUrl: 'LeGoat.png',
            imageClass: 'project-image',
            id: 'project5',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://github.com/ansh-mujral/Valorant_EDA' 
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
        <!-- <div class="dropdown">
            <button class="dropbtn" on:click={toggleDropdown}>Menu</button>
            {#if dropdownOpen}
                <div class="dropdown-content">
                    {#each sections as section, i}
                        <a href="javascript:void(0)" on:click={() => {navigateToSection(i); toggleDropdown();}}>{section.title}</a>
                    {/each}
                </div>
            {/if}
        </div> -->
      <section id="about-me" class="hero">
        <h1>Ansh Mujral: About Me</h1>
        <h2 class='subhead'>Hi! Welcome to my website. I am a second-year Data Science major at UC San Diego.<br><br>
            My journey in Data Science and Machine Learning is fueled by a profound passion, and my goal is to leverage these skills for the betterment of society. If you have any questions, comments, or simply want to engage in a conversation, feel free to drop me an email. I'm always open to connecting and discussing the exciting world of data!</h2>
      </section>
        {#each sections as section, i}
        <section class="scrollable-section">
            {#if i+1 === index}
            <div class="content" id={section.id} in:fade={{duration: 400 }} out:fade={{duration: 500 }}>
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
        </section>
        {/each}
        <!-- <section class="container">
            <div>
                <h1>Contact Me</h1>
            </div>
            <div class="contact-item">
                <h2>Email Me</h2>
                <a href="mailto:amujral@ucsd.edu" class="contact-link">Send an Email</a>
            </div>
            <div class="contact-item">
                <h2>GitHub</h2>
                <a href="https://github.com/ansh-mujral" class="contact-link">Visit GitHub</a>
            </div>
            <div class="contact-item">
                <h2>Resume</h2>
                <a href="path/to/your/resume.pdf" class="contact-link" target="_blank">View Resume</a> 
            </div>
            <div class="contact-item">
                <h2>LinkedIn</h2>
                <a href="https://www.linkedin.com/in/amujral/" class="contact-link">Connect on LinkedIn</a>
            </div>
        </section> -->
        <section id="contact">
            <div>
                <h1>Contact Me!</h1>
                <p>some yap</p>
            </div>
            <footer>
                <ul class="icons">
                    <li><a href="mailto:amujral@ucsd.edu" title="Email"><i class="fas fa-envelope"></i></a></li>
                    <li><a href="https://www.linkedin.com/in/amujral/" title="LinkedIn"><i class="fab fa-linkedin"></i></a></li>
                    <li><a href="https://github.com/ansh-mujral" title="Github"><i class="fab fa-github"></i></a></li>
                    <li><a href="AnshMujralResume_Mar2024.pdf" title="Resume"><i class="fas fa-file-text"></i></a></li>
                </ul>
            </footer>
        </section>
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
        background: linear-gradient(to right, #0f0c29, #302b63, #24243e);
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
        color: white;
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

    .container {
      /* display: grid;
      grid-template-columns: 3fr 1fr; 
      grid-template-rows: auto 1fr;
      gap: 20px; */
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

    .dropbtn {
    background-color: #4CAF50;
    color: white;
    padding: 16px;
    font-size: 16px;
    border: none;
    cursor: pointer;
    }

    /* Dropdown Content */
    .dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
    z-index: 1;
    }

    /* Links inside the dropdown */
    .dropdown-content a {
    color: black;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
    }

    /* Change color of dropdown links on hover */
    .dropdown-content a:hover {background-color: #f1f1f1}

    /* Show the dropdown menu on hover */
    .dropdown:hover .dropdown-content {
    display: block;
    }

    /* Change the background color of the dropdown button when the dropdown content is shown */
    .dropdown:hover .dropbtn {
    background-color: #3e8e41;
    }

    .container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: 10px; /* Reduced gap between the boxes */
  padding: 40px; /* Padding for the outer container */
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
  margin: 5px; /* Ensures boxes are closer together */
  width: calc(50% - 10px); /* Adjusts width for closer proximity */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.contact-link {
  color: #007bff;
  text-decoration: none;
  font-weight: bold;
  margin-top: 15px;
}

/* h1 {
  grid-column: 1 / -1;
  text-align: center;
  color: white; 
} */
  
  </style>
  