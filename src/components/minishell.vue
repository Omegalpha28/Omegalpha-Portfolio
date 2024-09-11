<template>
  <section id="minishell" class="Minishell" data-aos="fade-up">
    <header class="Title_Minishell">
      <div class="Ms"><a href="https://github.com/Omegalpha28/Minishell">My Shell</a></div>
      <div @click="toggleVisibility" class="discover-button">Discover this Project</div>
    </header>
    <div class="image-container" v-if="isVisible">
      <div v-for="(image, index) in images" :key="index" :class="['diapo', { 'show': currentIndex === index }]">
        <div class="content">
          <img :src="image.src" :alt="image.text">
          <h1>{{ image.text }}</h1>
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
      images: []
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
    async fetchImages() {
      const imageFiles = import.meta.glob('@/assets/minishell/diapo/*.png');
      const imagesInfo = [
        {
          src: '1.png',
          text: "Run commands, use cd for directory changes, setenv/unsetenv for environment variables, env for display/edit, and exit to close the shell. Supports ';' for sequential command execution."
        }
      ];

      try {
        const imageEntries = await Promise.all(
          Object.keys(imageFiles).map(async (path) => {
            const module = await imageFiles[path]();
            const imageName = path.split('/').pop();
            return {
              src: module.default,
              text: imagesInfo.find(info => info.src === imageName)?.text || 'No description'
            };
          })
        );

        this.images = imageEntries;
      } catch (error) {
        console.error('Error loading images:', error);
      }
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
    padding: 1%;
}

.Title_Minishell {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    cursor: pointer;
    text-decoration: none;
    color: inherit;
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

@media (max-width: 1080px) {
    .Title_Minishell .Ms a {
      font-size: 5rem;
    }

    .Minishell {
      background-position-x: -75vh;
    }
    .Minishell header {
      padding: 10%
    };
    .Title_Minishell {
      margin-top: 2vh;
    }
}
@media screen and (max-width: 768px) {
    .Title_Minishell .Ms a {
      font-size: 5rem;
    }

    .Minishell {
      background-size: cover;
      background-position-x: -78vh;
    }

    .Title_Minishell {
      margin-top: 10vh;
    }
}

@media screen and (max-width: 540px) {
    .Title_Minishell .Ms a {
      font-size: 2rem;
    }

    .Minishell {
      background-size: cover;
      background-position-x: -80vh;
    }

    .Title_Minishell {
      margin-top: 2vh;
    }
}

@media screen and (max-width: 480px) {
    .Title_Minishell .Ms a {
      font-size: 3rem;
    }

    .Minishell {
      background-size: cover;
      background-position-x: -80vh;
    }

    .Title_Minishell {
      margin-top: 2vh;
    }
}
</style>