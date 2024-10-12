<template>
  <section class="stack">
    <div class="stack__wrapper wrapper">
      <div class="stack__info" data-scroll data-scroll-speed="0">
        <div class="stack__head">
          <div class="stack__group-title">
            <h1 class="stack__title">Мой</h1>
            <h1 class="stack__subtitle">stack</h1>
            <img src="../assets/icons/strokeStar.svg" alt="decorate icon" class="stack__icon stack__icon--sstar">
          </div>
          <h1 class="stack__title">технологий</h1>
        </div>
        <p class="stack__desc">Перечень навыков, языков, фреймворков и прочих изученных технологий.</p>
        <img src="../assets/icons/grid.svg" alt="grid decorate element" class="stack__grid">
      </div>
      <ul class="stack__list" ref="stack__list">
        <li class="stack__item" v-for="(item, index) in skills" :key="index" data-scroll
          :data-scroll-speed="(6 - index) / 30">
          <h2 class="stack__name">{{ item.name }} <span class="stack__detail">{{ item.detail }}</span></h2>
          <p class="stack__data">{{ item.desc }}</p>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import VueSticky from 'vue-sticky';

export default {
  name: "StackSection",
  directives: {
    'sticky': VueSticky.directive,
  },
  data() {
    return {
      skills: [
        {
          name: 'React \n',
          detail: '& React Native',
          desc: 'Верстка сайтов и приложений на React. Создание кросплатформенных проектов с помощью React Native. React Route + Redux',
        },
        {
          name: 'HTML (БЭМ) \n',
          detail: '& CSS (SCSS)',
          desc: 'Опыт создания семантических и стилизованных веб-страниц по методологии БЭМ с использованием SCSS для более эффективного управления стилями.',
        },
        {
          name: 'Java Script',
          detail: '& Type Script',
          desc: 'Использую Type Script в последних проектах. Опыт работы с фреймворком Vue.js, разработка ~5 проектов с использованием SFC, роутинга и состояния (VueX & Pinia).',
        },
        {
          name: 'Git',
          detail: 'GitHub, GitLab, GitVerse',
          desc: 'Опыт работы с системой контроля версий Git, включая ветвление, конфликты, коммиты с пушингом изменений, умение работать в команде и следование правилам.',
        },
        {
          name: 'Node.js/express',
          detail: '& Django',
          desc: 'Применение Node.js с Express для создания серверной части в последних проектах, работа с API, CRUD, JWT аутентификация, cookies, local storage, MongooDB, MySQL.',
        },
        {
          name: 'Анимация',
          detail: 'c GSAP / WebGL',
          desc: 'Опыт создания анимаций с помощью библиотеки GreenSock Animation Platform (GSAP).',
        }
      ]
    }
  }
}
</script>

<style scoped lang="scss">
.stack {
  margin: 80px 0 20px;
}

.stack__wrapper {
  border-radius: 40px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 40px 5%;
  gap: 40px;

  @media screen and (max-width: 1050px) {
    grid-template-columns: 1fr;
  }
}

.stack__info {

  display: flex;
  flex-wrap: wrap;
  height: fit-content;
  padding: 0px;
  position: sticky;
  top: 40px;
  /* Расстояние от верхней части экрана до начала фиксации */
  align-self: start;
  /* Фиксация при начале прокрутки */
}

.stack__grid {
  position: absolute;
  right: 0;
  bottom: -260px;
}

.stack__head {
  position: relative;
  place-content: flex-start;
  align-items: flex-start;
  display: flex;
  flex: 0 0 auto;
  flex-flow: column;
  gap: 0px;
  height: min-content;
  overflow: hidden;
  padding: 10px 28px;
}

.stack__group-title {
  display: flex;
  gap: 36px;
}

.stack__title {
  font-family: 'Neue Machina';
  font-size: 76px;
  text-align: center;
  color: white;
  padding: 0;
  line-height: 0.8;
  margin: 0;
}

.stack__subtitle {
  font-family: 'PP Migra Italic Extrabold Italic', serif;
  color: rgb(236, 111, 213);
  transform: rotate(0deg);
  font-size: 76px;
  text-align: center;
  width: fit-content;
  padding: 0;
  margin: 0;
  height: fit-content;
  line-height: 0.8;
}

.stack__desc {
  color: white;
  font-family: 'PP Neue Machina Regular';
  font-size: 22px;
  text-align: left;
  padding: 10px 28px;
  line-height: 1.5;
}

.stack__icon {
  position: absolute;

  &--sstar {
    left: 425px;
    top: 10px;
    transform: rotate(-45deg);
  }
}

.stack__list {
  place-content: center;
  align-items: center;
  display: flex;
  flex: 0 0 auto;
  flex-flow: column;
  gap: 0px;
  height: min-content;
  padding: 0px;
  position: relative;
  list-style: none;
}

.stack__item {
  max-width: 90%;
}

.stack__name {
  font-family: 'Neue Machina', Inter, Arial;
  font-size: 38px;
  text-align: left;
}

.stack__detail {
  font-family: PP Migra Italic Extrabold Italic, serif;
  font-weight: 800;
  color: #EC6FD5;
}

.stack__data {
  color: white;
  font-family: 'PP Neue Machina Regular';
  font-size: 20px;
  text-align: justify;
  line-height: 1.4;
}

@media screen and (max-width: 768px) {
  .stack__desc {
    font-size: 20px;
  }

  .stack__title,
  .stack__subtitle {
    font-size: 64px;
  }

  .stack__desc {
    font-size: 20px;
  }

  .stack__name {
    font-size: 24px;
    line-height: 1.4;
  }

  .stack__data {
    font-size: 16px;
  }
}

@media screen and (max-width: 560px) {

  .stack__title,
  .stack__subtitle {
    font-size: 13em;
  }

  .projects__item {
    padding: 0;
  }
}
</style>