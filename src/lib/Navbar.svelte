<script>
  import Logo from './Logo.svelte'
  import Hamburger from './Hamburger.svelte'
  import Menu from './Menu.svelte'
  
  export let sidebar = false
</script>

<header class="flex sticky justify-between bg-white-100 p-2 items-center text-black-800" >
  <Hamburger bind:open={sidebar}/>
  <nav class="flex">
    <a href="/">
      <Logo/> 
    </a>
  </nav>
  
  <Menu/>
</header>

<style>
  header {
    z-index: 22;
    height: 60px;
  }
  a, a:hover, a:click, a:visited {
    outline:  none;
    border: none;
    text-decoration: none;
    color: inherit;
    -webkit-tap-highlight-color: white;
  }
</style>