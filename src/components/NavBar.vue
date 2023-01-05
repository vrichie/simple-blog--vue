<template lang="En">
    <nav><router-link to="/">  <h1>
      {{name}}
   </h1></router-link>
      

        <span id="desktopMenu">
        <router-link to="/">Home</router-link> &nbsp; | &nbsp;
        <router-link to="/about">About</router-link>  &nbsp; | &nbsp;
        <router-link to="/create">create</router-link>  &nbsp; | &nbsp;
        </span>
        <span id="mobileMenu" v-if="showMobileMenu">
            <div id="wrapper">
            <span id="wrapperMenu">
              <router-link to="/">  <h1>
                {{name}}
             </h1></router-link>
            <button @click="showMobileMenu=!showMobileMenu" id="menuButton">
    
                <img src="../assets/icons/x.png" alt="x" />
                
             </button> 
            </span>
            <hr/>
            <br/>

            <div id="links"> 
            <router-link to="/" @click="showMobileMenu=false" >Home</router-link> 
            <router-link to="/about" @click="showMobileMenu=false" >About</router-link>  
            <router-link to="/create" @click="showMobileMenu=false" >create</router-link>  
            </div>

            </div>
            
         </span>
         <button @click="showMobileMenu=!showMobileMenu" id="menuButton">
            <img src="../assets/icons/menu.png" alt="menu" />
            
         </button>

      </nav>
</template>
<script>
export default {
  name: "NavBar",
  props: {
    name: String,
  },
  data() {
    return {
      showMobileMenu: false,
    };
  },
};
</script>
<style scoped>
nav {
  padding: 30px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: relative;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: #42b983;
}
#mobileMenu {
  display: none;
  background: transparent;
  border: none;
  outline: none;
}

#menuButton {
  display: none;
  background: transparent;
  border: none;
  outline: none;
  cursor: pointer;
}
img {
  width: 20px;
}
@media (max-width: 767px) {
  #menuButton {
    display: block;
  }
  #desktopMenu {
    display: none;
  }
  #mobileMenu {
    display: flex;
    width: 100%;
    background-color: #000000fb;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    overflow: hidden;
    transition: all ease-in 300ms;
  }
  #wrapper {
    width: 100%;
    padding: 10px;
  }
  #wrapperMenu {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 0;
    color: aliceblue;
  }
  #links {
    display: flex;
    flex-direction: column;
    height: 70%;
    align-items: center;
    justify-content: space-around;
  }
}
</style>
