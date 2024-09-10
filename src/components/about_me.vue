<template>
  <section id="AboutMe" class="Experiences" data-aos="fade-up">
    <header class="about_title">
      <a href="../src/assets/CV_MSOILI_Ossan.pdf" target="_blank" rel="noopener noreferrer">About Me</a>
    </header>
    <div class="lang_buttons">
      <button class="my-button" :class="{ active: isListVisible }" @click="toggleListVisibility">
        {{ isListVisible ? 'Hide Languages' : 'Show Languages' }}
        <span v-if="isListVisible">🔼</span>
        <span v-else>🔽</span>
      </button>
      <button class="my-button" :class="{ active: isPresentationVisible }" @click="togglePresentationVisibility">
        {{ isPresentationVisible ? 'Hide Presentation' : 'Show Presentation' }}
        <span v-if="isPresentationVisible">🔼</span>
        <span v-else>🔽</span>
      </button>
    </div>
    <transition name="fade-lang">
      <div class="section_language" v-if="isListVisible">
        <ul class="list_lang">
          <h1>Programming Language</h1>
          <li class="only_language">
            <a href="https://en.wikipedia.org/wiki/C_(programming_language)" target="_blanck"><img src="../assets/About_Me/c.png" alt="C"></a>
            <a href="https://www.python.org/" target="_blanck"><img src="../assets/About_Me/python.png" alt="Python"></a>
            <a href="https://www.gnu.org/software/bash/manual/bash.html" target="_blanck"><img src="../assets/About_Me/bash(2).png" alt="bash"></a>
            <a href="https://fr.wikipedia.org/wiki/Hypertext_Markup_Language" target="_blanck"><img src="../assets/About_Me/html.png" alt="HTML"></a>
            <a href="https://developer.mozilla.org/en-US/docs/Web/CSS" target="_blanck"><img src="../assets/About_Me/css.png" alt="CSS"></a>
            <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blanck"><img src="../assets/About_Me/js.png" alt="JS"></a>
          </li>
          <h1>Frameworks</h1>
          <li class="frameworks">
            <a href="https://vuejs.org/" target="_blanck"><img src="../assets/About_Me/vue.png" alt="vue"></a>
            <a href="https://react.dev/" target="_blanck"><img src="../assets/About_Me/react.png" alt="React"></a>
            <a href="https://www.renpy.org/" target="_blanck"><img src="../assets/About_Me/renpy.png" alt="RenPy"></a>
          </li>
          <h1>Library or others tools</h1>
          <li class="tools_library">
            <a href="https://nodejs.org" target="_blanck"><img src="../assets/About_Me/nodes_js.png" alt="Nodes-JS"></a>
            <a href="https://www.blackmagicdesign.com/products/davinciresolve" target="_blanck"><img src="../assets/About_Me/DaVinci_Resolve_Studio.png" alt="DaVinci"></a>
            <a href="https://docs.docker.com/" target="_blanck"><img src="../assets/About_Me/docker.png" alt="docker"></a>
            <a href="https://www.sfml-dev.org/" target="_blanck"><img src="../assets/About_Me/CSFML.png" alt="CSFML"></a>
            <a href="https://git-scm.com/" target="_blanck"><img src="../assets/About_Me/git.png" alt="git"></a>
            <a href="https://www.mysql.com/" target="_blanck"><img src="../assets/About_Me/mySQL.png" alt="SQL"></a>
          </li>
          <li class="tools_library_2">
            <a href="https://unity.com" target="_blanck"><img src="../assets/About_Me/unity.png" alt="Unity"></a>
            <div class="logo_width">
              <a href="https://fr.wikipedia.org/wiki/Structured_Query_Language" target="_blanck"><img src="../assets/About_Me/sql.png" alt="SQL"></a>
              <a href="https://www.pygame.org/news" target="_blanck"><img src="../assets/About_Me/pygame logo très moche.png" alt="pygame"></a>
            </div>
          </li>
        </ul>
      </div>
    </transition>
    <transition name="Resume-fade">
      <div class="Resume" v-if="isPresentationVisible">
        <h2>I am a young developer, curious to discover new languages, and passionate about web development, video editing, game development, and software creation.</h2>
        <div id="elementToHide" v-if="isPresentationVisible">
        <h3 class="first_square">ㅤ</h3>
        <h3 class="second_square">ㅤ</h3>
        <h3 class="third_square">ㅤ</h3>
        <h3 class="fourth_square">ㅤ</h3>
        <h3 class="fifth_square">ㅤ</h3>
        <h3 class="sixth_square">ㅤ</h3>
        <h3 class="seventh_square">ㅤ</h3>
        <h3 class="eighth_square">ㅤ</h3>
        </div>
      </div>
    </transition>
  </section>
</template>


<script>
export default {
  name: 'AboutMe',
  data() {
    return {
      isListVisible: false,
      isPresentationVisible: false,
    };
  },
  methods: {
    toggleListVisibility() {
      this.isListVisible = !this.isListVisible;
      if (this.isListVisible) {
        this.isPresentationVisible = false;
      }
    },
    togglePresentationVisibility() {
      this.isPresentationVisible = !this.isPresentationVisible;
      if (this.isPresentationVisible) {
        this.isListVisible = false;
      }
    },
  },
};

let initialRatio = window.devicePixelRatio;

  function checkZoom() {
    const currentRatio = window.devicePixelRatio;

    if (currentRatio !== initialRatio) {
      document.getElementById("elementToHide").style.display = "none";
    } else {
      document.getElementById("elementToHide").style.display = "block";
    }
  }

  // Vérifier le zoom lors du redimensionnement et du scroll
  window.addEventListener("resize", checkZoom);
  window.addEventListener("scroll", checkZoom);
</script>


<style>

.Experiences {
  display: flex;
  background-size: 100%;
  height: 110vh;
  align-items: center;
  flex-direction: column;
  background-image: var(--about-background);
  background-repeat: no-repeat;
  font-family: 'Noto Sans', sans-serif;
}

.about_title h2 {
  display: flex;
  justify-content: left;
  margin: 2vh;
  font-size: 3vh;
  cursor: pointer;
  text-decoration: none;
  color: inherit;
  flex-direction: column;
}

.about_title a {
  height: 10vh;
  font-size: 10rem;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin-top: 5vh;
  margin-left: 50vh;
  margin-right: 50vh;
  cursor: pointer;
  font-family: 'Honk', sans-serif;
}

.lang_buttons {
  display: flex;
  gap: 10px;
  margin-bottom: 20vh;
  margin: 10vh;
}

.about_title a:hover {
  animation: littlescale 2s infinite ease-in-out;
}

.list_lang {
  list-style-type: none;
}


.Resume {
  font-size: 1rem;
  margin-top: 5vh;
  padding-left: 50vh;
  padding-right: 50vh;
  font-family: 'Vast Shadow', sans-serif;
}

.Resume h2 {
  display: inline-flex;
  padding-left: 5vh;
  padding-right: 5vh;
  padding-top: 5vh;
  padding-bottom: 5vh;
  background-color: var(--color-background-soft);
  border-radius: 20px;
  flex-wrap: wrap;
  z-index: 8;
}


.elementToHide {
  position: relative;
}

.first_square {
  display: inline-flex;
  padding-left: 5rem;
  padding-right: 4rem;
  padding-top: 2rem;
  padding-bottom: 1rem;
  position: absolute;
  top: 25rem;
  left: 26rem;
  background-color: var(--color-background-mute);
  border-radius: 20px;
  z-index: 5;
  flex-wrap: wrap;
  animation: floatingR 2s ease-in-out infinite;
}

.second_square {
  display: inline-flex;
  padding-left: 5rem;
  padding-right: 4rem;
  padding-top: 2rem;
  padding-bottom: 1rem;
  position: absolute;
  top: 24rem;
  left: 25rem;
  background-color: var(--background_text);
  border-radius: 20px;
  z-index: 6;
  flex-wrap: wrap;
  animation: sliding 2s ease-in-out infinite;

}

.third_square {
  display: inline-flex;
  padding-left: 5rem;
  padding-right: 4rem;
  padding-top: 2rem;
  padding-bottom: 1rem;
  position: absolute;
  top: 40rem;
  left: 26rem;
  background-color: var(--color-background-mute);
  border-radius: 20px;
  z-index: 5;
  flex-wrap: wrap;
  animation: floating 2s ease-in-out infinite;

}

.fourth_square {
  display: inline-flex;
  padding-left: 5rem;
  padding-right: 4rem;
  padding-top: 2rem;
  padding-bottom: 1rem;
  position: absolute;
  top: 41rem;
  left: 25rem;
  background-color: var(--background_text);
  border-radius: 20px;
  z-index: 6;
  flex-wrap: wrap;
  animation: sliding 2s ease-in-out infinite;

}

.fifth_square {
  display: inline-flex;
  padding-left: 5rem;
  padding-right: 4rem;
  padding-top: 2rem;
  padding-bottom: 1rem;
  position: absolute;
  top: 40rem;
  left: 84rem;
  background-color: var(--color-background-mute);
  border-radius: 20px;
  z-index: 5;
  flex-wrap: wrap;
  animation: floating 2s ease-in-out infinite;

}

.sixth_square {
  display: inline-flex;
  padding-left: 5rem;
  padding-right: 4rem;
  padding-top: 2rem;
  padding-bottom: 1rem;
  position: absolute;
  top: 41rem;
  left: 85rem;
  background-color: var(--background_text);
  border-radius: 20px;
  z-index: 6;
  flex-wrap: wrap;
  animation: slidingR 2s ease-in-out infinite;

}

.seventh_square {
  display: inline-flex;
  padding-left: 5rem;
  padding-right: 4rem;
  padding-top: 2rem;
  padding-bottom: 1rem;
  position: absolute;
  top: 25rem;
  left: 84rem;
  background-color: var(--color-background-mute);
  border-radius: 20px;
  z-index: 5;
  flex-wrap: wrap;
  animation: floatingR  2s ease-in-out infinite;

}

.eighth_square {
  display: inline-flex;
  padding-left: 5rem;
  padding-right: 4rem;
  padding-top: 2rem;
  padding-bottom: 1rem;
  position: absolute;
  top: 24rem;
  left: 85rem;
  background-color: var(--background_text);
  border-radius: 20px;
  z-index: 6;
  flex-wrap: wrap;
  animation: slidingR 2s ease-in-out infinite;

}


.section_language ul li {
  cursor: pointer;
}

.section_language ul li img {
  animation: littlescale 1.5s infinite ease-in-out;
}

.section_language ul li img:hover {
  animation: my_rotationY_scale 1.5s infinite ease-in-out;
}

.section_language {
  display: flex;
  align-items: center;
  flex-direction: row;
  justify-content: space-between;
}

.section_language img {
  width: 10vh;
  height: 11vh;
  margin: 5px;
  justify-content: space-between;
}

.section_language .logo_width {
  display: flex;
  justify-content: space-between;
}

.tools_library {
  display: flex;
  align-items: center;
}

.tools_library_2 {
  display: flex;
  align-items: center;
}

.section_language .logo_width img {
  width: 20vh;
  height: 11vh;
  margin: 5px;
}

.my-button {
  background-color: var(--color-background);
  color: var(--color-text);
  padding: 12px 24px;
  font-size: 16px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.5s ease-in-out;
  display: flex;
  align-items: center;
  gap: 10px;
}

.my-button.active {
  background-color: var(--button-color);
  color: var(--color-uni);
}

.my-button:hover {
  background-color: var(--button-color);
}

@media screen and (max-width: 1080px) {
  .Experiences {
    padding: 0rem;
    background-size: cover;
    background-position-x: -20vh;
  }

  .about_title h2 {
  display: flex;
  justify-content: center;
  margin: 2vh;
  font-size: 1vh;
  }

  .eighth_square,
  .seventh_square,
  .sixth_square,
  .fifth_square,
  .fourth_square,
  .third_square,
  .second_square,
  .first_square {
    background-color: transparent;
  }
  .about_title a {
    font-size: 21vw;
    margin: 0 0;
  }

  .lang_buttons {
    margin-bottom: 2vh;
  }

  .Resume {
    font-size: 5vw;
    padding: 0rem;
  }

  .section_language img {
    width: 7vh;
    height: 7vh;
    margin: 1vh;
  }

  .section_language .logo_width img {
  width: 7vh;
  height: 5vh;
  margin: 1vh;
  }
}

@media screen and (max-width: 800px) {
  .Experiences {
    padding: Orem;
    background-size: cover;
    background-position-x: -20vh;
  }

  .about_title h2 {
  display: flex;
  justify-content: center;
  margin: 2vh;
  font-size: 1vh;
  }

  .eighth_square,
  .seventh_square,
  .sixth_square,
  .fifth_square,
  .fourth_square,
  .third_square,
  .second_square,
  .first_square {
    background-color: transparent;
  }
  .about_title a {
    font-size: 20vw;
    margin: 0 0;
  }

  .lang_buttons {
    margin-bottom: 2vh;
  }

  .Resume {
    font-size: 4vw;
    padding: 0.1rem;
  }

  .section_language img {
    width: 7vh;
    height: 7vh;
    margin: 1vh;
  }

  .section_language .logo_width img {
  width: 7vh;
  height: 6vh;
  margin: 1vh;
  }
}

@media screen and (max-width: 480px) {
  .Experiences {
    padding: Orem;
    background-size: cover;
    background-position-x: -25vh;
  }

  .about_title a {
    font-size: 20vw;
    margin: 0 0;
  }

  .eighth_square,
  .seventh_square,
  .sixth_square,
  .fifth_square,
  .fourth_square,
  .third_square,
  .second_square,
  .first_square {
    background-color: transparent;
  }
  .Resume {
    font-size: 3vw;
    padding: 0rem;
  }

  .section_language {
    padding-right: 5vh;
  }

  .section_language img {
    width: 5vh;
    height: 5vh;
    margin: 1vh;
  }

  .section_language .logo_width img {
  width: 5vh;
  height: 4vh;
  margin: 1vh;
}

  .my-button {
    padding: 1vh 1vh;
    font-size: 5vw;
  }
}


</style>
