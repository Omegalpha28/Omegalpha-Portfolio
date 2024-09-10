<template>
  <div class="menu-container">
    <button class="menu-toggle" @click="isMenuVisible = !isMenuVisible">
      MENU
    </button>
    <div v-if="isMenuVisible" class="horizontal-menu">
      <div class="Menu_Item">
        <a href="#">Home</a>
      </div>
      <div class="Menu_Item">
        <a href="#AboutMe">About Me</a>
      </div>
      <dropdown title="Projects" :items="exp" />
      <dropdown_newwin title="Contact" :items="services" /> <!-- Correction des props -->
    </div>
  </div>
</template>

<script>
  import dropdown from './dropdown.vue';
  import dropdown_newwin from './dropdown_newwin.vue';

  export default {
    name: "HorizontalMenu",
    components: {
      dropdown,
      dropdown_newwin
    },
    data() {
      return {
        isMenuVisible: false,
        exp: [],
        services: []
      };
    },
    props: {
      items: {
        type: Array,
        default: () => []
      },
      exp: {
        type: Array,
        default: () => []
      },
      services: {
        type: Array,
        default: () => []
      }
    }
  };
</script>

<style scoped>
  .menu-container {
    display: flex;
    align-items: center;
  }

  .menu-toggle {
    background-color: var(--color-button-mute);
    color: var(--color-text);
    transition: background-color 0.5s ease-in-out;
    transition: color 0.5s ease-in-out;
    border: none;
    padding: 2vh 2vh;
    cursor: pointer;
    font-size: 18px;
    position: relative;
    border-radius: 10%;
  }

  .menu-toggle:hover,
  .menu-toggle.active {
    transition: background-color 1s ease-in-out;
    background-color: var(--button-color);
  }

  .horizontal-menu {
    display: flex;
    align-items: center;
    background-color: var(--color-background-mute);
    position: absolute;
    top: 100%;
    left: 0;
    transition: opacity transform 2.5s ease-in-out;
    transition: background-color 0.5s ease-in-out;
    z-index: 1;
    border-radius: 0px 0px 16px 16px;
  }

  .Menu_Item {
    display: flex;
    color: var(--color-text);
    padding: 1vh 2vh;
    position: relative;
    text-align: center;
    margin: 0;
    border-bottom: 3px solid transparent;
    transition: background-color 0.5s ease-in-out;

  }

  .Menu_Item a {
    color: inherit;
    text-decoration: none;
  }

  .horizontal-menu .Menu_Item:hover,
  .horizontal-menu .Menu_Item.active {
    border-bottom-color: transparent;
    border-radius: 10%;
  }

  @media screen and (max-width: 768px) {

    .horizontal-menu {
      width: 100%;
    }

    .Menu_Item {
      width: 100%;
      font-size: 2vh;
      border-bottom: 6px solid transparent;
    }
  }

@media screen and (max-width: 480px) {

  .menu-toggle {
    background-size: cover;
  }

  .horizontal-menu {
  width: 100%;
}

.Menu_Item {
  width: 100%;
  font-size: 1.7vh;
  border-bottom: 6px solid transparent;
}
}
</style>

