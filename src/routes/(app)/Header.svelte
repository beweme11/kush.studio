<script>
  import { fly } from 'svelte/transition';
</script>

<style>
  /* Add Tailwind CSS styles here or import directly if configured in your project */
  .navbar {
    background-color: white;
    color: #000;
    transition: color 0.3s ease-in-out;
  }

  .navbar a {
    transition: color 0.3s ease-in-out, transform 0.3s ease-in-out;
  }

  .navbar a:hover {
    color: #00FFFF; /* Cyan color */
    transform: scale(1.1);
  }
</style>

<div class="h-16 navbar text-black py-4 px-6 flex justify-between items-center fixed top-0 left-0 right-0 z-50 transition-all duration-300 ease-in-out" transition:fly="{{ y: -50, duration: 300, easing: cubicOut }}">
  <div class="text-lg font-bold"><a href="/" class="text-black">Your Logo</a></div>
  <div class="flex items-center space-x-6">
    <div><a href="/">Home</a></div>
    <div><a href="/about">About</a></div>
    <div><a href="/services">Services</a></div>
    <div><a href="/contact">Contact</a></div>
  </div>
</div>
