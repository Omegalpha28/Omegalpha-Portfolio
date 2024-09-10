<template>
  <section id="duck_hunter" class="Duck" data-aos="fade-up">
    <header class="Title_Hunter">
      <div class="Hunter"><a href="https://github.com/Omegalpha28/Duck_Hunter">MY Duck Hunter</a></div>
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
  name: 'duck_hunter',
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
      const imageFiles = import.meta.glob('@/assets/Duck_Hunter/diapo/*.png');
      const imagesInfo = [
        {
          text: "This was my first project involving the creation of a visual game using the C language. The objective, similar to the game 'Duck Hunt', is to shoot ducks to score points.",
          src: '/assets/Duck_Hunter/diapo/menu.png'
        }
      ];

      try {
        const imageEntries = await Promise.all(
          Object.keys(imageFiles).map(async (path) => {
            const module = await imageFiles[path]();
            return {
              src: module.default,
              text: imagesInfo.find(info => path.endsWith(info.src))?.text || 'No description'
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

.Duck {
    display: flex;
    flex-direction: column;
    height: 100vh;
    background-size: cover;
    background-image: var(--AK-Duck-Hunter);
    background-repeat: no-repeat;
    font-family: 'Noto Sans', sans-serif;
}

.Title_Hunter {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.Duck header .Hunter:hover {
    animation: littlescale 2s infinite ease-in-out;
}

.Title_Hunter .Hunter a {
    font-family: 'Honk';
    font-size: 10rem;
    cursor: pointer;
    text-decoration: none;
    color: inherit;
}

@media (max-width: 1088px) {
    .Title_Hunter .Hunter a {
      font-size: 7rem;
    }

    .Duck {
      background-size: cover;
      background-position-x: -75vh;
    }

    .Title_Hunter {
      margin-top: 2vh;
    }
  }


@media (max-width: 768px) {
    .Title_Hunter .Hunter a {
      font-size: 5rem;
    }

    .Duck {
      background-size: cover;
      background-position-x: -78vh;
    }

    .Title_Hunter {
      margin-top: 10vh;
    }
  }

  @media (max-width: 540px) {
    .Title_Hunter .Hunter a {
      font-size: 4rem;
    }

    .Duck {
      background-size: cover;
      background-position-x: -80vh;
    }

    .Title_Hunter {
      margin-top: 2vh;
    }
  }

  @media (max-width: 480px) {
    .Title_Hunter .Hunter a {
      font-size: 3rem;
    }

    .Duck {
      background-size: cover;
      background-position-x: -80vh;
    }

    .Title_Hunter {
      margin-top: 2vh;
    }
  }
</style>
