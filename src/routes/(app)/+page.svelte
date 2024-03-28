<script>
  import { fade } from 'svelte/transition';
  import { onMount } from 'svelte';

  onMount(() => {
    const jq = window.$;

    const svg = document.querySelector('svg.squiggle');
    const path = svg.querySelector('path');

    const scroll = () => {
      const distance = window.scrollY;
      const totalDistance = document.body.clientHeight - window.innerHeight;
      const percentage = distance / totalDistance;
      const pathLength = path.getTotalLength();
      path.style.strokeDasharray = `${pathLength}`;
      path.style.strokeDashoffset = `${pathLength * (1 - percentage)}`;
      console.log(pathLength)
    };

    scroll();
    window.addEventListener('scroll', scroll);

    
  var terms = ["website built", "admin dashboard built", "online presence built", "website google indexed", "brand known"];

function rotateTerm() {
  var ct = jq("#rotate").data("term") || 0;
  jq("#rotate").data("term", ct == terms.length -1 ? 0 : ct + 1).text(terms[ct]).fadeIn()
              .delay(2000).fadeOut(200, rotateTerm);
}
jq(rotateTerm);

  });
  
</script>
<style>

  /* Preload Merriweather font */
  @import url('https://fonts.googleapis.com/css2?family=Merriweather:ital,wght@0,300;0,400;0,700;0,900;1,300;1,400;1,700;1,900&display=swap') preload;

  /* Apply Merriweather font to the heading */
  .merriweather-font {
    font-family: 'Merriweather', serif;
  }

  /* Define hover effect for the heading */


/* gradient source: https://uigradients.com/#Wiretap */
/* decreased transparency to 80% */
/* Define keyframes for the highlight growth */


/* Apply the animation to the highlight class */
@keyframes highlight-grow {
  0% {
    filter: hue-rotate(0deg);
    transform: scale(0);
  }
  100% {
    filter: hue-rotate(360deg);
    transform: scale(1);
  }
}
.highlight-marker {
  font-weight: bolder;
  background: linear-gradient(104deg, rgba(0, 255, 255, 0) 0.9%, rgba(0, 255, 255, 1.25) 2.4%, rgba(0, 255, 255, 0.5) 5.8%, rgba(0, 255, 255, 0.1) 93%, rgba(0, 255, 255, 0.7) 96%, rgba(0, 255, 255, 0) 98%), linear-gradient(183deg, rgba(0, 255, 255, 0) 0%, rgba(0, 255, 255, 0.3) 7.9%, rgba(0, 255, 255, 0) 15%);
  padding: 0.2em 13.7px;
  -webkit-box-decoration-break: clone;
  margin: 0;
  border-radius: 7.5px;
  text-shadow: -12px 12px 9.8px rgba(0, 255, 255, 0.7), 21px -18.1px 7.3px rgba(255, 255, 255, 1), -18.1px -27.3px 30px rgba(255, 255, 255, 1);
}


.highlight {
  background-image: linear-gradient(to right, 
                      #ffffff, /* White */
                      #4286f4, /* Blue */
                      #7c3aed, /* Purple */
                      #00ffff, /* Cyan */
                      #ffffff /* White */);
  border-radius: 6px;
  padding: 3px 6px;
  animation: highlight-grow 3s linear infinite; /* Adjust duration and timing function as needed */
  backdrop-filter: blur(100px); /* Adjust the blur radius as needed */
}


.border-gradient {
  border-style: solid;
  border-width: 4px;
  border-image: linear-gradient(to right, 
  rgba(135, 206, 235, 1),
      rgba(0, 191, 255, 1),
      rgba(135, 206, 235, 1),
      rgba(0, 255, 255, 1),
      rgba(0, 191, 255, 1),
      rgba(135, 206, 235, 1),
      rgba(135, 206, 235, 1)) 1;
}


body {
  background-color: #110e17;
}


body {
  background-color: #110e17;
}

svg.squiggle {
    position: absolute;
    z-index: 0;
    top: 0;
    left: 50%; /* Center the squiggle horizontally */
    transform: translateX(-50%); /* Center the squiggle horizontally */
    width: 100%; /* Make the squiggle span the entire width of the viewport */
    max-width: 100%; /* Ensure the squiggle does not exceed the viewport width */
    height: auto; /* Automatically adjust the height based on the width */
  }

  @media (max-width: 768px) {
    svg.squiggle {
      top: 20%; /* Adjust the vertical position for smaller screens */
      width: 150%; /* Increase the width to cover a larger portion of the viewport */
      transform: translate(-25%, -50%); /* Adjust the horizontal and vertical position */
    }
  }


  .js-nametag{
  position: absolute;
}
.js-nametag:nth-child(1){
  animation-name: fade;
  animation-fill-mode: both;
  animation-iteration-count: infinite;
  animation-duration: 5s;
  animation-direction: alternate-reverse;  
}


.js-nametag:nth-child(2){
  animation-name: fade;
  animation-fill-mode: both;
  animation-iteration-count: infinite;
  animation-duration: 5s;
  animation-direction: alternate;
}

@keyframes fade{
    0%,50% {
      opacity: 0;
}
    100%{
      opacity: 1;
  }
}
</style>
  <main class="pt-8 bg-white">

    <div class="px-4 py-12">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div class="text-center md:text-left ml-4 mt-16">
          <h1 class="text-6xl font-bold mb-4 merriweather-font">You have a <span class="highlight">business.</span></h1>

          <h1 class="text-6xl font-bold mb-4 merriweather-font">We have <span class = "highlight">solutions.</span></h1>
        <!-- <p>This is some <span class="brushed-highlight">highlighted text</span>.</p> -->
        <div class = "relative">
        <p class = " font-bold mb-4 text-xl">Take your brand online, <br> With a single click. </p>
        <p> Get your  <span id="rotate">this</span></p>
      </div>

          <div class="pt-8">
            <button class="bg-blue-500 text-white px-4 py-2 rounded-full">Watch Video</button>

          </div>
      </div>

        <div class="relative">
          <img src="Screenshot_24.jpg" alt="Person" class="w-full rounded-lg" transition:fade>          <div class="absolute top-0 right-0 -mt-8 mr-8">
            <div class="w-16 h-16 rounded-full bg-blue-500"></div>
            <div class="w-8 h-8 rounded-full bg-teal-500 absolute -top-2 -right-2"></div>
          </div>
        </div>
      </div>
  


      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-12">
        <!-- Left side grid -->
        <div class="md:col-span-1">
          <div class="grid grid-cols-2 gap-4">
            <div class="border border-gradient bg-white rounded-lg shadow-md p-6 aspect-w-1 aspect-h-1">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" width="64" height="64" class="mb-4">
                <path d="M6.72 26.2c-0.040 0-0.080 0-0.12 0-0.28-0.040-0.48-0.2-0.64-0.44l-1.96-3.56-3.56-1.96c-0.24-0.12-0.4-0.36-0.44-0.64s0.040-0.52 0.24-0.72l1.8-1.8c0.2-0.2 0.48-0.28 0.76-0.24l2.040 0.36 2.68-2.68-6.48-3.2c-0.24-0.12-0.4-0.36-0.48-0.64s0.040-0.56 0.24-0.76l2-2c0.2-0.2 0.52-0.28 0.8-0.24l8.48 2.2 2.96-2.96c1.040-1.040 3.48-1.8 4.72-0.56 0.56 0.56 0.76 1.48 0.56 2.52-0.16 0.84-0.6 1.64-1.12 2.16l-2.96 2.96 2.2 8.48c0.080 0.28 0 0.6-0.24 0.8l-2 2c-0.2 0.2-0.48 0.28-0.76 0.24s-0.52-0.2-0.64-0.48l-3.2-6.48-2.68 2.68 0.36 2.040c0.040 0.28-0.040 0.56-0.24 0.76l-1.8 1.8c-0.080 0.28-0.28 0.36-0.52 0.36zM2.24 19.28l2.8 1.52c0.16 0.080 0.24 0.2 0.32 0.32l1.52 2.8 0.68-0.68-0.32-2.040c-0.040-0.28 0.040-0.56 0.24-0.76l3.84-3.84c0.2-0.2 0.48-0.28 0.76-0.24s0.52 0.2 0.64 0.48l3.2 6.48 0.8-0.8-2.2-8.48c-0.080-0.28 0-0.6 0.24-0.8l3.28-3.28c0.6-0.6 0.92-1.96 0.56-2.32s-1.72 0-2.32 0.56l-3.28 3.28c-0.2 0.2-0.52 0.28-0.8 0.24l-8.52-2.2-0.8 0.8 6.48 3.2c0.24 0.12 0.4 0.36 0.48 0.64s-0.040 0.56-0.24 0.76l-3.84 3.84c-0.2 0.2-0.48 0.28-0.76 0.24l-2.040-0.36-0.72 0.64z"></path>
              </svg>
              <h3 class="text-xl font-bold mb-2">Digital Strategies</h3>
              <p>Develop effective digital strategies tailored to your business goals.</p>
            </div>
            <div class="bg-white border-4 border-gradient rounded-lg shadow-md p-6 aspect-w-1 aspect-h-1">
              <svg width="40px" height="40px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="mb-4">
                <path d="M9 13.2222L10.8462 15L15 11M8.4 19C5.41766 19 3 16.6044 3 13.6493C3 11.2001 4.8 8.9375 7.5 8.5C8.34694 6.48637 10.3514 5 12.6893 5C15.684 5 18.1317 7.32251 18.3 10.25C19.8893 10.9449 21 12.6503 21 14.4969C21 16.9839 18.9853 19 16.5 19L8.4 19Z" stroke="#000000" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              <h3 class="text-xl font-bold mb-2">Design & Develop</h3>
              <p>Create captivating designs and develop high-quality digital products.</p>
            </div>

            <div class="bg-white border border-gradient rounded-lg shadow-md p-6 aspect-w-1 aspect-h-1">
  <svg width="40px" height="40px" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" class="mb-4">
    <g>
      <path d="M12,8c1.9,0,3.5,1.3,3.9,3.1c0.1,0.5,0.7,0.9,1.2,0.7c0.5-0.1,0.9-0.7,0.7-1.2C17.2,7.8,14.8,6,12,6c-3.3,0-6,2.7-6,6    c0,3.1,2.4,5.7,5.5,6c0,0,0.1,0,0.1,0c0.5,0,0.9-0.4,1-0.9c0.1-0.5-0.4-1-0.9-1.1c-2-0.2-3.7-2-3.7-4C8,9.8,9.8,8,12,8z"/>
      <path d="M12,20c-4.4,0-8-3.6-8-8s3.6-8,8-8c4.2,0,7.7,3.3,8,7.5c0,0.6,0.5,1,1.1,0.9c0.6,0,1-0.5,0.9-1.1C21.6,6.1,17.3,2,12,2    C6.5,2,2,6.5,2,12s4.5,10,10,10c0.6,0,1-0.4,1-1S12.6,20,12,20z"/>
      <path d="M21.3,14.5c-0.1-0.1-0.3-0.2-0.4-0.2l-6.5-2.2c-0.6-0.2-1.3,0-1.8,0.5c-0.5,0.5-0.6,1.2-0.3,1.8l3,6.6    c0.3,0.6,0.9,1,1.5,1c0.1,0,0.2,0,0.3,0c0.8-0.1,1.3-0.7,1.4-1.5l0.3-2.4l2-0.6c0.6-0.2,1.1-0.7,1.2-1.4    C22.1,15.5,21.8,14.8,21.3,14.5z M18.1,16.2c-0.7,0.2-1.1,0.7-1.2,1.4l-0.2,1.5l-2.2-4.9l4.8,1.6L18.1,16.2z"/>
    </g>
  </svg>
  <h3 class="text-xl font-bold mb-2">Digital Marketing</h3>
  <p>Implement effective digital marketing campaigns to drive growth.</p>
</div>
            
<div class="bg-white border border-gradient rounded-lg shadow-md p-6 aspect-w-1 aspect-h-1">
  <svg width="40px" height="40px" viewBox="0 0 20 20" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" class="mb-4">
    <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
      <g id="Dribbble-Light-Preview" transform="translate(-340.000000, -7599.000000)" fill="#000000">
        <g id="icons" transform="translate(56.000000, 160.000000)">
          <path d="M296.744,7457.45798 C296.262,7457.45798 295.872,7457.06594 295.872,7456.58142 C295.872,7456.0969 296.262,7455.70587 296.744,7455.70587 C297.226,7455.70587 297.616,7456.0969 297.616,7456.58142 C297.616,7457.06594 297.226,7457.45798 296.744,7457.45798 M294.072,7459 C299.15,7459 298.833,7456.78649 298.833,7456.78649 L298.827,7454.49357 L293.982,7454.49357 L293.982,7453.80499 L300.751,7453.80499 C300.751,7453.80499 304,7454.17591 304,7449.02614 C304,7443.87636 301.165,7444.0583 301.165,7444.0583 L299.472,7444.0583 L299.472,7446.44873 C299.472,7446.44873 299.563,7449.29855 296.682,7449.29855 L291.876,7449.29855 C291.876,7449.29855 289.176,7449.25533 289.176,7451.9222 L289.176,7456.33112 C289.176,7456.33112 288.766,7459 294.072,7459 M291.257,7440.54202 C291.739,7440.54202 292.128,7440.93406 292.128,7441.41858 C292.128,7441.9031 291.739,7442.29413 291.257,7442.29413 C290.775,7442.29413 290.385,7441.9031 290.385,7441.41858 C290.385,7440.93406 290.775,7440.54202 291.257,7440.54202 M293.928,7439 C288.851,7439 289.168,7441.21351 289.168,7441.21351 L289.174,7443.50643 L294.019,7443.50643 L294.019,7444.19501 L287.249,7444.19501 C287.249,7444.19501 284,7443.82409 284,7448.97386 C284,7454.12364 286.836,7453.9417 286.836,7453.9417 L288.528,7453.9417 L288.528,7451.55127 C288.528,7451.55127 288.437,7448.70145 291.319,7448.70145 L296.124,7448.70145 C296.124,7448.70145 298.824,7448.74467 298.824,7446.0778 L298.824,7441.66888 C298.824,7441.66888 299.234,7439 293.928,7439" id="python-\[#127\]"></path>
        </g>
      </g>
    </g>
  </svg>
  <h3 class="text-xl font-bold mb-2">Software Development</h3>
  <p>Build robust and scalable software solutions for your business.</p>
</div>
          </div>
        </div>
    
      
        <!-- Right side filler text -->
        <div class="bg-white rounded-lg shadow-md p-6 md:col-span-1">
          <h3 class="text-xl font-bold mb-2">Why Take Your Business Online?</h3>
          <p>There are numerous compelling reasons why bringing your business online can benefit you:</p>
          <ul class="list-disc pl-6">
            <li class="mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block mr-2 text-blue-500" viewBox="0 0 20 20" fill="currentColor">
                <path d="M10 2a8 8 0 0 0-8 8c0 4.418 3.582 8 8 8s8-3.582 8-8a8 8 0 0 0-8-8zm0 14a6 6 0 1 1 0-12 6 6 0 0 1 0 12z"/>
              </svg>
              <strong>Global Reach:</strong> By establishing an online presence, your business can reach a global audience, breaking geographical barriers and expanding your customer base.
            </li>
            <li class="mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block mr-2 text-blue-500" viewBox="0 0 20 20" fill="currentColor">
                <path d="M10 2a8 8 0 0 0-8 8c0 4.418 3.582 8 8 8s8-3.582 8-8a8 8 0 0 0-8-8zm0 14a6 6 0 1 1 0-12 6 6 0 0 1 0 12z"/>
              </svg>
              <strong>24/7 Availability:</strong> Unlike brick-and-mortar stores, an online presence allows your business to operate 24/7, catering to customers at any time, from anywhere.
            </li>
            <li class="mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block mr-2 text-blue-500" viewBox="0 0 20 20" fill="currentColor">
                <path d="M10 2a8 8 0 0 0-8 8c0 4.418 3.582 8 8 8s8-3.582 8-8a8 8 0 0 0-8-8zm0 14a6 6 0 1 1 0-12 6 6 0 0 1 0 12z"/>
              </svg>
              <strong>Cost-Effectiveness:</strong> Setting up and maintaining an online platform is often more cost-effective than traditional methods, reducing overhead costs associated with physical locations.
            </li>
            <li class="mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block mr-2 text-blue-500" viewBox="0 0 20 20" fill="currentColor">
                <path d="M10 2a8 8 0 0 0-8 8c0 4.418 3.582 8 8 8s8-3.582 8-8a8 8 0 0 0-8-8zm0 14a6 6 0 1 1 0-12 6 6 0 0 1 0 12z"/>
              </svg>
              <strong>Enhanced Visibility:</strong> Being online increases your visibility through search engines, social media, and other digital channels, making it easier for potential customers to discover your brand.
            </li>
            <li class="mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block mr-2 text-blue-500" viewBox="0 0 20 20" fill="currentColor">
                <path d="M10 2a8 8 0 0 0-8 8c0 4.418 3.582 8 8 8s8-3.582 8-8a8 8 0 0 0-8-8zm0 14a6 6 0 1 1 0-12 6 6 0 0 1 0 12z"/>
              </svg>
              <strong>Improved Customer Engagement:</strong> Online platforms enable direct communication with customers, facilitating feedback, inquiries, and personalized interactions, enhancing overall customer experience.
            </li>
            <li class="mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block mr-2 text-blue-500" viewBox="0 0 20 20" fill="currentColor">
                <path d="M10 2a8 8 0 0 0-8 8c0 4.418 3.582 8 8 8s8-3.582 8-8a8 8 0 0 0-8-8zm0 14a6 6 0 1 1 0-12 6 6 0 0 1 0 12z"/>
              </svg>
              <strong>Data Insights:</strong> Digital platforms provide valuable insights into customer behavior, preferences, and trends, allowing for data-driven decision-making and targeted marketing strategies.
            </li>
          </ul>
          <p>Embracing the digital realm is not just a trend but a strategic imperative for businesses looking to thrive in the modern marketplace.</p>
        </div>
        
        
      </div>
      
  
      <div class="text-center mt-12">
        <h2 class="text-3xl font-bold mb-4">Level up your business with the <span class = "highlight-marker">power of software</span></h2>
        <p class="mb-6">Work With Our Team To Create Digital <br> Solutions to Increase Customer Engagement online & offline.</p>
        <button class="bg-blue-500 text-white px-4 py-2 rounded">Learn More</button>
      </div>
  
      <div class="mt-12">
        <h2 class="text-3xl pb-8 font-bold mb-4 text-center">We utilize the latest tools to ensure you are always up and running </h2>
        <div class="flex justify-between mt-4">
          <div class="flex items-center justify-center w-1/5">
            <img src="react-svgrepo-com.svg" alt="ReactJS" class="h-24 max-w-full">
          </div>
          <div class="flex items-center justify-center w-1/5">
            <img src="svelte-16-svgrepo-com.svg" alt="Sveltekit" class="h-24 max-w-full">
          </div>
          <div class="flex items-center justify-center w-1/5">
            <img src="tailwind-svgrepo-com.svg" alt="Tailwind CSS" class="h-24 max-w-full">
          </div>
          <div class="flex items-center justify-center w-1/5">
            <img src="vercel-logo-svgrepo-com.svg" alt="Vercel" class="h-24 max-w-full">
          </div>
          <div class="flex items-center justify-center w-1/5">
            <img src="aws-svgrepo-com.svg" alt="Amazon Web Services" class="h-24 max-w-full">
          </div>
          <div class="flex items-center justify-center w-1/5">
            <img src="django-fill-svgrepo-com.svg" alt="Django" class="h-24 max-w-full">
          </div>
        </div>
      </div>
      
  
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-12">
        <div class="relative">
          <img src="person2.jpg" alt="Person" class="w-full rounded-lg" transition:fade>
          <div class="absolute bottom-0 left-0 -mb-8 ml-8">
            <div class="w-16 h-16 rounded-full bg-teal-500"></div>
            <div class="w-8 h-8 rounded-full bg-blue-500 absolute -bottom-2 -left-2"></div>
          </div>
        </div>
        <div class="text-center md:text-left">
          <h2 class="text-3xl font-bold mb-4">Take A Look At The Featured Case Studies</h2>
          <p class="mb-6">From Concept To Market: Our Agile Approach <br> For Superior Performance</p>
          <button class="bg-blue-500 text-white px-4 py-2 rounded">Case Study</button>
        </div>
      </div>
    </div>
  
    <footer class="bg-blue-500 text-white py-8 px-4">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-4">
        <div>
          <h4 class="text-lg font-bold mb-2">Services</h4>
          <ul>
            <li>Branding</li>
            <li>Marketing</li>
            <li>Web Development</li>
            <li>Social Media Marketing</li>
            <li>Digital Transformation</li>
          </ul>
        </div>
        <div>
          <h4 class="text-lg font-bold mb-2">Quick Links</h4>
          <ul>
            <li>About Us</li>
            <li>Blog</li>
            <li>Contact</li>
            <li>Terms & Conditions</li>
            <li>Privacy Policy</li>
          </ul>
        </div>
        <div>
          <h4 class="text-lg font-bold mb-2">Solutions</h4>
          <ul>
            <li>Enterprise Resource Planning</li>
            <li>Customer Relationship Management</li>
            <li>Supply Chain Management</li>
            <li>Personalized Price Storing</li>
            <li>Inventory Management</li>
          </ul>
        </div>
        <div>
          <h4 class="text-lg font-bold mb-2">Impact+</h4>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed id ligula id turpis tincidunt vestibulum.</p>
        </div>
      </div>
      <div class="text-center mt-8">
        &copy; Impact+. All Rights Reserved.
      </div>
    </footer>
    
  </main>

  <svg class="squiggle" width="1919" height="3208" viewBox="0 0 1919 3208" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path stroke-linecap="round" d="M1.27777 1C-37.4304 483.734 818.794 -81.3268 469.646 524.897C33.212 1282.68 863.502 1342.55 1038.66 1210.64C1213.81 1078.73 1078.33 747.554 1561.22 773.749C2044.1 799.943 1911.52 1244.32 1809.92 1368.75C1701.98 1500.92 1509.93 1602.63 1159.62 1368.75C734.487 1084.91 423.196 909.401 446.421 1493.17C469.646 2076.94 867.372 2167.69 1338.64 2126.53C1809.92 2085.36 2047.97 2642.94 1388.96 2533.48C706.221 2420.08 925.435 2514.77 469.646 2774.85C197.08 2930.38 169.013 3169.02 129.982 3208" stroke="cyan" stroke-opacity="0.7" stroke-width="23"/>
  </svg>