<script>
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';
    import Scroller from "@sveltejs/svelte-scroller";
    import * as d3 from 'd3';
  
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
            content: `This project involves an in-depth exploratory data analysis of a Recipes and Ratings dataset. By applying various statistical methods and visualization techniques, I uncovered insightful trends and patterns that could significantly impact culinary practices and preferences.`,
            imageUrl: 'path/to/your/project1/image.png',
            imageClass: 'project-image',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://keenans04.github.io/RecipesAndRatings/'
        },
        {
            title: 'Recipes and Ratings Pipelines and Modeling Project',
            content: `Focusing on automating data processing and modeling for the Recipes and Ratings dataset, this project streamlines the workflow through pipelines. The goal was to enhance efficiency and reproducibility, ensuring that the data analysis process is more structured and accessible.`,
            imageUrl: 'path/to/your/project2/image.png', 
            imageClass: 'project-image',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://keenans04.github.io/WhatsTheRating/'
        },
        {
            title: 'LeGOAT: The LeBron James\'s Career Narrative',
            content: `A captivating scrollytelling narrative that explores the illustrious career of LeBron James. Using D3.js for interactive storytelling, this project presents LeBron's journey from a promising young talent to one of the greatest basketball players of all time.`,
            imageUrl: 'path/to/your/project3/image.png',
            imageClass: 'project-image',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://keenans04.github.io/LeGOAT/'
        },
        {
            title: 'PowerAtlas: Navigating Global Energy Consumption',
            content: `PowerAtlas offers an immersive exploration of global energy consumption patterns through interactive data visualizations. This project was designed to provide insights into how different countries consume energy, using advanced data analysis and D3.js to create an engaging, interactive web experience. It highlights the disparities in energy usage and the impact of renewable energy sources across the globe.`,
            imageUrl: 'path/to/your/poweratlas/image.png',
            imageClass: 'project-image',
            technologies: 'Technologies used: Python, Pandas, Matplotlib, Seaborn',
            link: 'https://keenans04.github.io/PowerAtlas/'
        },
        {
            title: 'Valorant EDA: Analyzing the Skill Gap',
            content: `This exploratory data analysis (EDA) dives deep into the competitive world of Valorant, analyzing the skill gap between individual players from different regions. By scrutinizing player data and performance metrics, this project sheds light on the factors that contribute to a player's success and how different regions compare in terms of skill level and competitive play style.`,
            imageUrl: 'path/to/your/valoranteda/image.png',
            imageClass: 'project-image',
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
      <section class="hero">
        <h1>Ansh Mujral: About Me</h1>
        <h2 class='subhead'>Hi! Welcome to my website. I am a second-year Data Science major at UC San Diego.<br><br>
            My journey in Data Science and Machine Learning is fueled by a profound passion, and my goal is to leverage these skills for the betterment of society. If you have any questions, comments, or simply want to engage in a conversation, feel free to drop me an email. I'm always open to connecting and discussing the exciting world of data!</h2>
        <!-- <img src='images/lob.webp' alt='LeBron James' class="header-image"/> -->
      </section>
        {#each sections as section, i}
        <section class="scrollable-section">
            {#if i+1 === index}
            <div class="content" in:fade={{duration: 400 }} out:fade={{duration: 500 }}>
                {#if section.imageUrl}
                <img src={section.imageUrl} alt={section.title} class="project-image"/>
                {/if}
                <div class="project-description">
                    <h1 class='title-content'>{section.title}</h1>
                    <p>{section.content}</p>
                    <p>{section.technologies}</p>
                    <a href={section.link} target="_blank" rel="noopener noreferrer">Check out My Project Here!</a>
                </div>
            </div>
            {/if}
        </section>
        {/each}
      <section class="container">
        <div class="map-accolades">
            <div class="map-container" in:fade={{duration: 700 }} out:fade={{duration: 500 }}>
                <h1>Contact Me</h1>
            </div>
            <div class="conclusion" in:fade={{duration: 700 }} out:fade={{duration: 500 }}>
                <h2 class="conc-title">Conclusion</h2>
                <!-- <p class='left'>LeBron came into the NBA with great expectations, and for the first part of his career he performed up to par with some of the greats in the game. But to solidify his legacy as a true legend of the sport, he needed to start winning more. Therefore he switched teams and worked together with other stars to win his first two championships with the Miami Heat. After completing everything in the books, LeBron wanted a name for himself and his city, and in his path stood the Warriors dynasty. Against all odds, he still ended up overcoming the Warriors to win a championship for his home team. In recent times, LeBron has done philanthropic work with his I Promise School and focused more on his family in LA. LeBron is the definition of growth, hard work, talent, and perseverance, and his journey proves just why he is the basketball GOAT.</p> -->
            </div>
        </div>
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
      font-family: 'Yantramanav', sans-serif;
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
  
    .foreground {
      width: 100%;
      margin: 0 auto;
      height: auto;
      position: relative;
    }
  
    .hero h1 {
      font-size: 3em;
    }
  
    .hero img {
      max-width: 100%; 
      max-height: 60vh; 
      object-fit: contain;
    }

    .hero{
        color: white;
    }
  
    .content {
      height: 93vh;
      width: 45vw;
      position: absolute;
      left: 53%;
      border: black 2px solid;
      border-radius: 5px;
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
  
    .left{
      text-align: center;
      font-size: 20px;
      margin-top: 20px;
      padding-left: 10px;
      padding-right: 10px;
    }
  
    .header-image{
      animation: slideInBottom 0.5s ease-out forwards;
      height: 60%;
      margin: 10px;
    }
  
    .cavaliers-image{
      max-width: 80%; 
      max-height: 40vh; 
      object-fit: contain;
      margin-top: 10px;
    }
    .draft-image{
      max-width: 80%; 
      max-height: 30vh; 
      object-fit: contain;
      margin-top: 10px;
    }
    .heat-image{
      max-width: 80%; 
      max-height: 40vh; 
      object-fit: contain;
    }
    .cavaliers-image{
      max-width: 80%; 
      max-height: 45vh; 
      object-fit: contain;
    }
    .la-image{
      max-width: 80%; 
      max-height: 30vh; 
      object-fit: contain;
    }
    .origins-image{
      max-width: 80%; 
      max-height: 60vh; 
      object-fit: contain;
      margin-top: 10px;
    }
    .container {
      display: grid;
      grid-template-columns: 3fr 1fr; 
      grid-template-rows: auto 1fr;
      gap: 20px;
      height: 95vh;
    }
  
    .map-accolades {
        display: flex;
        flex-direction: column;
        margin-top: -30px;
    }
  
    .map-container {
        animation: fadeIn 0.5s ease-out forwards;
        margin-bottom: 20px;
    }
  
    .map-container, .conclusion {
        flex-grow: 1;
    }
  
    .accolades-list {
        animation: slideInLeft 0.5s ease-out forwards;
        background-color: rgba(255, 255, 255, 0.5);
        border-radius: 8px;
        height: 95vh;
        padding-left: 20px;
        padding-right: 20px;
        text-align: left;
    }
  
    .conclusion {
        animation: slideInBottom 0.5s ease-out forwards;
        background-color: rgba(255, 255, 255, 0.5);
        border-radius: 8px;
        padding: 10px;
        margin-bottom: 10px;
    }
    h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 3em; 
      font-weight: 700;
      letter-spacing: 2px;
    }
    .annotation {
      margin-top: -40px;
      padding: 10px;
    }
    .conc-title{
      margin-bottom: -7px;
      margin-top: 3px;
    }
    .title-content{
      padding-left: 5px;
      padding-right: 5px;
    }
  
  </style>
  