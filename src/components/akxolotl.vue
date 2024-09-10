<template>
  <section id="akxolotl" class="AKXolotl" data-aos="fade-up">
    <header class="Title">
      <div class="AK"><a href="https://github.com/Omegalpha28/my_rpg">MY RPG/AK Xolotl</a></div>
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
  name: 'akxolotl',
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
    fetchImages() {
      fetch('../src/tab_json/images_ak.json')
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

.AKXolotl {
  display: flex;
  flex-direction: column;
  height: 100vh;
  background-size: cover;
  background-image: var(--AK-background);
  background-repeat: no-repeat;
  font-family: 'Noto Sans', sans-serif;
}

.Title {
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  text-decoration: none;
  color: inherit;
  flex-direction: column;
}

.AKXolotl header .AK:hover {
  animation: littlescale 2s infinite ease-in-out;
}

.Title .AK a {
  font-family: 'Honk';
  font-size: 10rem;
  cursor: pointer;
  text-decoration: none;
  color: inherit;
}


@media (max-width: 1080px) {
    .Title .AK a {
      font-size: 5rem;
    }

    .AKXolotl {
      background-size: cover;
      background-position-x: -55vh;
    }

    .Title {
      margin-top: 5vh;
    }

    .content {
      flex-direction: column;
      justify-content: center;
    }

    .content img,
    .content h1 {
      width: 100%;
      max-width: 100%;
      padding-left: 0;
      text-align: center;
    }

}

@media (max-width: 768px) {
    .Title .AK a {
      font-size: 5rem;
    }

    .AKXolotl {
      background-size: cover;
      background-position-x: -55vh;
    }

    .Title {
      margin-top: 2vh;
    }

    .content {
      flex-direction: column;
      justify-content: center;
    }

    .content img,
    .content h1 {
      width: 100%;
      max-width: 100%;
      padding-left: 0;
      text-align: center;
    }

  }
  @media screen and (max-width: 600px) {
    .Title .AK a {
      font-size: 4rem;
    }

    .AKXolotl {
      background-size: cover;
      background-position-x: -55vh;
    }

    .Title {
      margin-top: 5vh;
      padding: 0.5vh;
    }

    .content img,
    .content h1 {
      width: 100%;
      max-width: 100%;
      padding-left: 0;
      text-align: center;
      padding: -2vh;
    }

    .content h1 {
      font-size: 1.5rem;
    }

  }

  @media screen and (max-width: 480px) {
    .Title .AK a {
      font-size: 3rem;
    }

    .AKXolotl {
      background-size: cover;
      background-position-x: -55vh;
    }

    .Title {
      margin-top: 5vh;
      padding: 0.5vh;
    }

    .content img,
    .content h1 {
      width: 100%;
      max-width: 100%;
      padding-left: 0;
      text-align: center;
      padding: -2vh;
    }

    .content h1 {
      font-size: 1.5rem;
    }

  }
</style>
