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
    <section class="Présentation" >
  <header>
    <div class="box" data-aos="zoom-in" data-aos-delay="70" data-aos-duration="1000">
      <h1 class="Title"> My Portfolio</h1>
      <div class="content">
        <img :src="face" class="me">
        <div class="presentation">
          <h1 class="name"> Name: Ossan Msoili</h1>
          <h1 class="skills"> Student at Epitech Lyon   </h1>
          <img :src="epitech" alt="epitech" class="epitech">
        </div>
      </div>
    </div>
  </header>
</section>
  <div class="waves layer1" ></div>
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
import darkModeImage from '@/assets/darkmode.png';
import face from '@/assets/Ossan.jpg';
import lightModeImage from '@/assets/lightmode.png';
import githubLightModeImage from '@/assets/github_lightMode.png';
import githubDarkModeImage from '@/assets/github_darkMode.png';
import epitech from '@/assets/epitech.png';
import akIntroImage from '@/assets/AKXolotl/Intro.png';
import akIntroDarkImage from '@/assets/AKXolotl/Intro2.png';
import duckHunterImage from '@/assets/Duck_Hunter/Duck_hunt.jpg';
import duckHunterDarkImage from '@/assets/Duck_Hunter/Duck_huntD.jpg';
import wave from '@/assets/svg/waves.svg';
import waveLight from '@/assets/svg/wavesL.svg';
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
  {title: 'My RPG/AK-Xolotl', link: '#akxolotl'},
  {title: 'My Shell', link: '#minishell'},
]);

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
      document.documentElement.style.setProperty('--background-wave', `url(${waveLight})`);
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
      document.documentElement.style.setProperty('--background-wave', `url(${wave})`);
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

.waves {
  aspect-ratio: 930/300;
  width: 100%;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}

.layer1 {
  background-image: var(--background-wave);
}

.invisible-char {
  background: none;
  font-size: 0;
  visibility: hidden;
}
</style>

