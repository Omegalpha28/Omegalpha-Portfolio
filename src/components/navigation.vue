<template>
  <body>
    <nav>
      <div class="my_profile">
        <HorizontalMenu :items="services" :exp="exp" :services="services" />
        <div class="linkGithub">
          <a href="https://github.com/Omegalpha28" target="_blank">
            <img :src="githubModeImage" alt="Github">
          </a>
        </div>
        <div class="changeTheme">
          <img :src="themeModeImage" alt="new_theme">
        </div>
      </div>
    </nav>
    <section class="Présentation" data-aos="zoom-in" data-aos-delay="50" data-aos-duration="1000">
      <header>
        <transition ref="fade">
          <h1 v-if="showFirst">Welcome Here!</h1>
        </transition>
        <transition ref="fade2">
          <h1 v-if="showSecond">My name is Ossan MSOILI.</h1>
        </transition>
        <transition ref="fade2">
          <h1 v-if="showThird">It's my Portfolio!</h1>
        </transition>
      </header>
    </section>
    <about_me title="=About Me" data-aos-delay="50" data-aos-duration="1000"/>
    <duck_hunter title="Duck_hunter" data-aos-delay="50" data-aos-duration="1000"/>
    <akxolotl title="AKXolotl" data-aos-delay="50" data-aos-duration="1000"/>
    <minishell title="Minishell" data-aos-delay="50" data-aos-duration="1000"/>
  </body>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import HorizontalMenu from './horizontal_drop.vue';
import akxolotl from './akxolotl.vue';
import about_me from './about_me.vue';
import duck_hunter from './duck_hunter.vue';
import minishell from './minishell.vue';

// Importer les images
import darkModeImage from '@/assets/darkmode.png';
import lightModeImage from '@/assets/lightmode.png';
import githubLightModeImage from '@/assets/github_lightMode.png';
import githubDarkModeImage from '@/assets/github_darkMode.png';
import akIntroImage from '@/assets/AKXolotl/Intro.png';
import akIntroDarkImage from '@/assets/AKXolotl/Intro2.png';
import duckHunterImage from '@/assets/Duck_Hunter/Duck_hunt.jpg';
import duckHunterDarkImage from '@/assets/Duck_Hunter/Duck_huntD.jpg';
import seaImage from '@/assets/seaL.gif';
import seaDarkImage from '@/assets/seaD.gif';
import backgroundImage from '@/assets/backgroundL.gif';
import backgroundDarkImage from '@/assets/background.gif';
import minishellImage from '@/assets/minishell/backgroundL.png';
import minishellDarkImage from '@/assets/minishell/background.png';

const services = ref([
  { title: 'Github', link: 'https://github.com/Omegalpha28' },
  { title: 'Mail', link: 'mailto:ossan.msoili@epitech.eu' },
  { title: 'Linkedin', link: 'https://www.linkedin.com/in/ossan-msoili/' }
]);

const exp = ref([
  {title: 'My Duck Hunter', link: '#duck_hunter'},
  {title: 'My Radar', link: '#'},
  {title: 'My RPG/AK-Xolotl', link: '#akxolotl'},
  {title: 'My Shell', link: '#minishell'},
]);

const showFirst = ref(true);
const showSecond = ref(false);
const showThird = ref(false);

let timeout1, timeout2, resetTimeout;

const startTimeouts = () => {
  clearTimeout(timeout1);
  clearTimeout(timeout2);
  clearTimeout(resetTimeout);
  timeout1 = setTimeout(() => {
    showFirst.value = false;
    showSecond.value = true;
  }, 5000);
  timeout2 = setTimeout(() => {
    showSecond.value = false;
    showThird.value = true;
  }, 10000);
  resetTimeout = setTimeout(() => {
    resetStates();
    startTimeouts();
  }, 15000);
};

const resetStates = () => {
  showFirst.value = true;
  showSecond.value = false;
  showThird.value = false;
};

onMounted(() => {
  startTimeouts();
});

const userPrefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
const toggleBtn = ref(userPrefersDark ? 1 : 0);

const themeModeImage = ref(userPrefersDark ? darkModeImage : lightModeImage);
const githubModeImage = ref(userPrefersDark ? githubDarkModeImage : githubLightModeImage);

onMounted(() => {
  const themeBtn = document.querySelector('.changeTheme');
  const themeGithub = document.querySelector('.linkGithub');
  const themeBtnMode = themeBtn.querySelector('img');
  const themeGithubMode = themeGithub.querySelector('img');

  let start = 0;

  if (toggleBtn.value === 1 && start === 0) {
    themeBtnMode.src = darkModeImage;
    themeGithubMode.src = githubDarkModeImage;
    start++;
  }

  themeBtn.addEventListener('click', () => {
    if (toggleBtn.value === 1) {
      themeBtnMode.src = lightModeImage;
      themeGithubMode.src = githubLightModeImage;
      document.documentElement.style.setProperty('--background-button-color', 'var(--vt-c-back-red)');
      document.documentElement.style.setProperty('--background_text', 'var(--vt-c-back-light)');
      document.documentElement.style.setProperty('--AK-background', `url(${akIntroImage})`);
      document.documentElement.style.setProperty('--AK-Duck-Hunter', `url(${duckHunterImage})`);
      document.documentElement.style.setProperty('--about-background', `url(${seaImage})`);
      document.documentElement.style.setProperty('--background_presentation', `url(${backgroundImage})`);
      document.documentElement.style.setProperty('--ms-background', `url(${minishellImage})`);
      document.documentElement.style.setProperty('--color-background', '#ffffff');
      document.documentElement.style.setProperty('--color-background-soft', '#f8f8f8');
      document.documentElement.style.setProperty('--color-background-mute', '#f2f2f2');
      document.documentElement.style.setProperty('--color-button-mute', 'var(--vt-c-back-red)');
      document.documentElement.style.setProperty('--button-color', 'red');
      document.documentElement.style.setProperty('--color-uni', 'var(--vt-c-black)');
      document.documentElement.style.setProperty('--color-border', 'rgba(60, 60, 60, 0.12)');
      document.documentElement.style.setProperty('--color-border-hover', 'rgba(60, 60, 60, 0.29)');
      document.documentElement.style.setProperty('--color-heading', '#2c3e50');
      document.documentElement.style.setProperty('--color-text', '#2c3e50');
      toggleBtn.value--;
    } else {
      themeBtnMode.src = darkModeImage;
      themeGithubMode.src = githubDarkModeImage;
      document.documentElement.style.setProperty('--background-button-color', 'var(--vt-c-back-red-dark)');
      document.documentElement.style.setProperty('--background_text', 'var(--vt-c-back-dark)');
      document.documentElement.style.setProperty('--AK-background', `url(${akIntroDarkImage})`);
      document.documentElement.style.setProperty('--about-background', `url(${seaDarkImage})`);
      document.documentElement.style.setProperty('--AK-Duck-Hunter', `url(${duckHunterDarkImage})`);
      document.documentElement.style.setProperty('--background_presentation', `url(${backgroundDarkImage})`);
      document.documentElement.style.setProperty('--ms-background', `url(${minishellDarkImage})`);
      document.documentElement.style.setProperty('--color-background', '#181818');
      document.documentElement.style.setProperty('--color-background-soft', '#222222');
      document.documentElement.style.setProperty('--color-background-mute', '#282828');
      document.documentElement.style.setProperty('--color-button-mute', '#9d24a881');
      document.documentElement.style.setProperty('--color-uni', 'var(--vt-c-white)');
      document.documentElement.style.setProperty('--button-color', '#9d24a8');
      document.documentElement.style.setProperty('--color-border', 'rgba(84, 84, 84, 0.48)');
      document.documentElement.style.setProperty('--color-border-hover', 'rgba(84, 84, 84, 0.65)');
      document.documentElement.style.setProperty('--color-heading', '#f8f9fa');
      document.documentElement.style.setProperty('--color-text', 'rgba(235, 235, 235, 0.64)');
      toggleBtn.value++;
    }
  });
});
</script>

<style>
.invisible-char {
  background: none;
  font-size: 0;
  visibility: hidden;
}
</style>

