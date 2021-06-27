<template>
  <div id="nav" class="ir-fixed ir-top">
    <div class="ir-margin ir-fixed">
    <router-link class="ir-padding logo" to="/"><img style="width:84px;height:84px;border-radius:50%;" src="./assets/logo.png" /></router-link>
    </div>
    <div class="ir-margin ir-right">
      <router-link class="ir-padding" to="/">Home</router-link>
      <router-link class="ir-padding" to="/projects">Projects</router-link>
      <router-link class="ir-padding" to="/about">About</router-link>
    </div>
  </div>
  <div id="m-nav" class="ir-fixed ir-top">
    <a class="toggle fa fa-bars"></a>
  </div>
  <div id="m-menu" class="ir-fixed ir-top">
    <div class="scale-in">
      <router-link class="ir-padding" to="/">Home</router-link>
      <router-link class="ir-padding" to="/projects">Projects</router-link>
      <router-link class="ir-padding" to="/about">About</router-link>
    </div>
  </div>
  <div id="social" class="ir-fixed ir-bottom ir-left ir-margin">
    <a target="_blank" href="https://stackoverflow.com/users/14104186/the-otterlord"><i class="fa fa-stack-overflow"></i></a>
    <a target="_blank" href="https://github.com/TheOtterlord"><i class="fa fa-github"></i></a>
  </div>
  <router-view v-slot="{ Component }" class="view">
    <transition name="fade" mode="out-in">
      <component :is="Component"></component>
    </transition>
  </router-view>
</template>

<script>
export default {
  created () {
    window.addEventListener('scroll', this.handleScroll);
    window.addEventListener('click', this.handleToggle);
  },
  unmount () {
    window.removeEventListener('scroll', this.handleScroll);
    window.removeEventListener('click', this.handleToggle);
  },
  methods: {
    handleScroll () {
      var el = document.querySelector("#nav");
      if (document.body.scrollTop > 40 || document.documentElement.scrollTop > 40) {
        el.classList.add("background");
      } else {
        el.classList.remove("background");
      }
    },
    handleToggle (ev) {
      // TODO: add style for button
      if (!ev.target.classList.contains("toggle") && ev.target.parentElement.parentElement.id != "m-menu") return;
      var menu = document.querySelector("#m-menu");
      menu.classList.toggle("active");
      if (!menu.classList.contains("active")) menu.classList.add("close");
      else menu.classList.remove("close");
    }
  }
}
</script>

<style scoped>
#nav {
  width: 100%;
  z-index: 100;
}

#nav, #nav div {
  transition: 0.4s ease;
  float: right;
}

#nav.background {
  background-color: var(--primary);
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

#nav.background div {
  margin: 0;
}

#nav a {
  position: relative;
  display: block;
  float: left;
  font-size: 20px;
  text-decoration: none;
}

#nav a::before {
  content: "";
  transition: all 0.4s ease-in-out;
  position: absolute;
  right: 50%;
  left: 50%;
  bottom: 0;
  height: 2px;
  background-color: var(--secondary);
}

#nav a:hover::before {
  right: 0;
  left: 0;
}

#nav .logo::before {
  display: none;
}

#m-nav {
  display: none;
}

#m-menu {
  transform: scale(0);
  width: 100%;
  height: 100vh;
  padding-top: 100px;
  z-index: 99;
  background-color: var(--primary);
}

@media only screen and (max-width: 599px) {
  #nav {
    display: none;
  }

  #m-nav {
    top: 0;
    right: 0;
    display: block;
    z-index: 100;
    background-color: var(--primary);
    overflow: hidden;
    border-radius: 52px;
    margin: 16px;
  }

  #m-nav .toggle {
    width: 52px;
    height: 52px;
    font-size: 24px;
    float: right;
    padding: 16px;
  }

  #m-menu.active {
    transform: scale(1);
    animation: fade-in 0.2s;
  }

  #m-menu.close {
    animation: fade-out 0.2s;
  }

  #m-menu a {
    width: 100%;
    display: block;
    text-align: center;
    font-size: 24px;
    text-decoration: none;
  }

  #m-menu .scale-in {
    transform: scale(0);
    animation: scale-out 0.4s;
  }

  #m-menu.active .scale-in {
    transform: scale(1);
    animation: scale-in 0.4s;
  }
}

@keyframes scale-in {
  0% {
    transform: scale(0.8);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

@keyframes scale-out {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  100% {
    transform: scale(0.8);
    opacity: 0;
  }
}

@keyframes fade-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes fade-out {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  100% {
    transform: scale(1);
    opacity: 0;
  }
}

#social {
  background-color: var(--primary);
  border: 2px solid var(--secondary);
  border-radius: 36px;
  overflow: auto;
  z-index: 98;
}

#social a {
  display: block;
  text-align: center;
  padding: 12px;
  transition: background-color 0.3s ease;
  color: white;
  font-size: 36px;
  color: var(--secondary);
}

#social a:hover {
  background-color: rgba(0,0,0,0.2);
}

.fade-enter-active,
.fade-leave-active {
  transition-duration: 0.3s;
  transition-property: opacity;
  transition-timing-function: ease;
}

.fade-enter-from,
.fade-leave-active {
  opacity: 0;
}
</style>
