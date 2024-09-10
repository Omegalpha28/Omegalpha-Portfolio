<template>
  <body>
      <nav>
          <div class="my_profile">
              <HorizontalMenu :items="services" :exp="exp" :services="services" />
              <div class="linkGithub">
                <a href="https://github.com/Omegalpha28" target="_blank">
                  <img src="../assets/github_lightMode.png" alt="Github">
                </a>
              </div>
              <div class="changeTheme">
                  <img src="../assets/lightmode.png" alt="new_theme">
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

onMounted(() => {
const themeBtn = document.querySelector('.changeTheme');
const themeGithub = document.querySelector('.linkGithub');
const themeBtnMode = themeBtn.querySelector('img');
const themeGithubMode = themeGithub.querySelector('img');
let start = 0;

if (toggleBtn.value === 1 && start === 0) {
  themeBtnMode.src = "../src/assets/darkmode.png";
  themeGithubMode.src = "../src/assets/github_darkMode.png";
  start++;
}

themeBtn.addEventListener('click', () => {
  if (toggleBtn.value === 1) {
    themeBtnMode.src = "../src/assets/lightmode.png";
    themeGithubMode.src = "../src/assets/github_lightMode.png";
    document.documentElement.style.setProperty('--background-button-color', 'var(--vt-c-back-red)');
    document.documentElement.style.setProperty('--background_text', 'var(--vt-c-back-light');
    document.documentElement.style.setProperty('--AK-background', 'url("./src/assets/AKXolotl/Intro.png")');
    document.documentElement.style.setProperty('--AK-Duck-Hunter', 'url("./src/assets/Duck_Hunter/Duck_hunt.jpg")');
    document.documentElement.style.setProperty('--about-background', 'url("./src/assets/seaL.gif")');
    document.documentElement.style.setProperty('--background_presentation', 'url("./src/assets/backgroundL.gif")');
    document.documentElement.style.setProperty('--ms-background', 'url("./src/assets//minishell/backgroundL.png")');
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
    themeBtnMode.src = "../src/assets/darkmode.png";
    themeGithubMode.src = "../src/assets/github_darkMode.png";
    document.documentElement.style.setProperty('--background-button-color', 'var(--vt-c-back-red-dark)');
    document.documentElement.style.setProperty('--background_text', 'var(--vt-c-back-dark)');
    document.documentElement.style.setProperty('--AK-background', 'url("./src/assets/AKXolotl/Intro2.png")');
    document.documentElement.style.setProperty('--about-background', 'url("./src/assets/seaD.gif")');
    document.documentElement.style.setProperty('--AK-Duck-Hunter', 'url("./src/assets/Duck_Hunter/Duck_huntD.jpg")');
    document.documentElement.style.setProperty('--background_presentation', 'url("./src/assets/background.gif")');
    document.documentElement.style.setProperty('--ms-background', 'url("./src/assets/minishell/background.png")');
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
