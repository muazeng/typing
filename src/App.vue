<script>
  import Home from './components/Home.vue'
  import About from './components/About.vue'
  import NavigationBar from './components/NavigationBar.vue'
      
    const routes = {
      '/': Home,
      '/about': About
    }
    
    export default {
    data() {
        return {
            currentPath: window.location.pathname
        };
    },
    computed: {
        currentView() {
            console.log(this.currentPath)
            return routes[this.currentPath || "/"] ;1

        }
    },
    mounted() {
        window.addEventListener("hashchange", () => {
            this.currentPath = window.location.hash;
        });
    },
    components: { NavigationBar }
  }
</script>
    
<template>
  <NavigationBar/>
  <component :is="currentView" />
</template>