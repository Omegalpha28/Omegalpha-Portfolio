<template>
    <section id="minishell" class="Minishell" data-aos="fade-up">
      <header class="Title_Minishell">
        <div class="Ms"><a href="git@github.com:Omegalpha28/Minishell.git">My Shell</a></div>
        <div @click="toggleVisibility" class="discover-button">Discover this Project</div>
      </header>
      <div class="image-container" v-if="isVisible">
        <div :class="['diapo', { 'show': currentIndex === 0 }]">
          <div class="content">
            <h1>{{ images[0].text }}</h1>
            <img :src="images[0].src" alt="Begin">
          </div>
        </div>
      </div>
    </section>
</template>

<script>
  export default {
    name: 'minishell',
    data() {
      return {
        isVisible: false,
        currentIndex: 0,
        intervalId: null,
        images_ms: []
      };
    },
    methods: {
    toggleVisibility() {
      this.isVisible = !this.isVisible;
      if (this.isVisible) {
        this.startImageTransition();
      } else {
        this.stopImageTransition();
      }
    },
    startImageTransition() {
      if (this.intervalId) {
        clearInterval(this.intervalId);
      }
      this.intervalId = setInterval(() => {
        this.currentIndex = (this.currentIndex + 1) % this.images.length;
      }, 10000);
    },
    stopImageTransition() {
      if (this.intervalId) {
        clearInterval(this.intervalId);
        this.intervalId = null;
      }
    },
    fetchImages() {
      fetch('../src/tab_json/images_ms.json')
        .then(response => response.json())
        .then(data => {
          this.images = data;
        })
        .catch(error => {
          console.error('Error loading images:', error);
        });
    }
  },
  mounted() {
    this.fetchImages();
  },
  beforeDestroy() {
    this.stopImageTransition();
  }
};
</script>

<style>

.Minishell {
    display: flex;
    flex-direction: column;
    height: 100vh;
    background-size: cover;
    background-image: var(--ms-background);
    background-repeat: no-repeat;
    font-family: 'Noto Sans', sans-serif;
}

.Title_Minishell {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    cursor: pointer;
    text-decoration: none;
    color: inherit;
    flex-direction: column;
}

.Minishell header .Ms:hover {
    animation: littlescale 2s infinite ease-in-out;
}

.Title_Minishell .Ms a {
    font-family: 'Honk';
    font-size: 10rem;
    cursor: pointer;
    text-decoration: none;
    color: inherit;
}

</style>