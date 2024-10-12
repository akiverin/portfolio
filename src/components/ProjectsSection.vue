<template>
  <section class="projects">
    <div class="projects__wrapper wrapper">
      <div class="projects__info">
        <div class="projects__head">
          <h1 class="projects__title">Все мои</h1>
          <img src="../assets/icons/strokeStar.svg" alt="decorate icon" class="projects__icon projects__icon--sstar">
          <h1 class="projects__name">Projects</h1>
        </div>
        <p class="projects__desc">Здесь вы найдете некоторые из проектов, реализованных мной в качестве фронтенд,
          фулстек разработчика и дизайнера. Многие из них были выполнены во время обучения, а также в командной работе
          или в
          рамках проектной деятельности.</p>
        <img src="../assets/icons/fillStar.svg" alt="decorate icon" class="projects__icon projects__icon--fstar">
        <ul class="projects__list">
          <li class="projects__item case" v-for="item, key in projects" :key="key">
            <video v-if="item.media.type == 'video'" loop autoplay playsinline muted class="case__media"
              :src="require('../assets/' + item.media.title)"></video>
            <img v-if="item.media.type == 'image'" :src="require('../assets/' + item.media.title)"
              alt="image for project case" class="case__media">
            <ul class="case__badges">
              <li v-for="badge, keybadge in item.badges" :key="keybadge" class="case__badge">
                <p class="case__badge-title">{{ badge }}</p>
              </li>
            </ul>
            <h2 class="case__title">{{ item.name }}</h2>
            <p class="case__desc">{{ item.desc }}</p>
            <div class="case__actions">
              <a v-if="item.link" :href="item.link" class="case__link" target="_blank">
                <p class="case__link-text"> Перейти</p>
              </a>
              <a v-if="item.rep" :href="item.rep" class="case__link case__link--rep" target="_blank">
                <p class="visually-hidden">Репозиторий</p>
                <img src="../assets/icons/github.svg" alt="follow the link icon" class="case__follow">
              </a>
            </div>
          </li>

        </ul>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProjectsSection',
  data() {
    return {
      projects: [
        {
          name: 'Веб-сайт кафедры менеджмент Московского Политеха',
          desc: 'Проект на React с собственным дизайном интерфейса. Современные и минималистичные решения в верстке, удобство и понятность функционала.',
          media: {
            type: 'video',
            title: 'project8.mp4'
          },
          link: 'http://management.kiver.net/',
          rep: 'https://github.com/akiverin/department_management',
          badges: ['в разработке', 'react', 'дизайн'],
        },
        {
          name: 'Веб-сайт для школы',
          desc: 'Веб-портал для школы с удобным взаимодействием пользователей, формами и командной работой. Стек: VueX, Axios, адаптивный дизайн.',
          media: {
            type: 'video',
            title: 'project1.mp4'
          },
          link: 'http://school.kiver.net',
          rep: 'https://github.com/akiverin/school-site',
          badges: ['команда', 'pet-проект', 'дизайн'],
        },
        {
          name: 'Редактор изображений',
          desc: 'Создание функционального редактора изображений на React, с вычислением цветов, маштабированием изображения, горячими клавишами, модальным окнами, экспортом и импортом изображений.',
          media: {
            type: 'image',
            title: 'editor.webp'
          },
          link: 'http://editor.kiver.net/',
          rep: 'https://github.com/akiverin/image-editor',
          badges: ['pet-проект', 'дизайн', 'react'],
        },
        {
          name: 'Веб-платформа для публикации игр и программ PolyGames',
          desc: 'Сервис для распространения игровых разработок. Собственный дизайн проекта и разработка страниц «Главная» и «Каталог игр» на React.',
          media: {
            type: 'video',
            title: 'project7.mp4'
          },
          link: 'http://polygames.std-1725.ist.mospolytech.ru/',
          rep: 'https://github.com/GamesPoly/-',
          badges: ['дизайн', 'команда', 'react', 'в разработке'],
        },
        {
          name: 'Мобильное приложение заметок',
          desc: 'App на смартфон для своих заметок, цитатой дня и настройками персонализации. Разработка кроссплатформенного проекта на React Native, local storage, работа с API.',
          media: {
            type: 'image',
            title: 'project6.webp'
          },
          link: 'https://appgallery.huawei.com/app/C111249837',
          rep: 'https://github.com/akiverin/notesApp',
          badges: ['pet-проект', 'дизайн', 'react native'],
        },
        {
          name: 'Сервис для тренировок',
          desc: 'Проект демонстрирует адаптивное веб-приложение с многоуровневой навигацией, личным кабинетом и функциями работы с датами. Стек: VueJS, Pinia, axios, fetch.',
          media: {
            type: 'video',
            title: 'project2.mp4'
          },
          link: 'http://polyfit.std-1725.ist.mospolytech.ru/',
          rep: 'https://github.com/polyfit-live/polyfit',
          badges: ['pet-проект', 'свой дизайн'],
        },
        {
          name: 'Сайт для fantacy игры',
          desc: 'Проект представляет онлайн-игру с фантастическим миром, современным дизайном и интеграцией API для удобной работы. Стек: Адаптивный интерфейс, MySQL, API, Django.',
          media: {
            type: 'image',
            title: 'project3.webp'
          },
          link: 'http://webexam2023.std-1725.ist.mospolytech.ru/',
          rep: 'https://github.com/akiverin/webExam3',
          badges: ['pet-проект', 'свой дизайн'],
        },
        {
          name: 'Новостной портал арт студии',
          desc: 'Проект — минималистичная галерея для демонстрации работ художников и фотографов с удобной навигацией на всех устройствах.',
          media: {
            type: 'video',
            title: 'project4.mp4'
          },
          link: 'http://web.std-1725.ist.mospolytech.ru/',
          rep: 'https://github.com/akiverin/web-lab',
          badges: ['pet-проект', 'дизайн'],
        },
      ]
    }
  },
}
</script>

<style lang="scss" scoped>
.projects__wrapper {
  border-radius: 40px;
  padding-top: 40px;
  padding-bottom: 40px;
  background-color: white;
  z-index: -2;
}

.projects__info {
  position: relative;
  display: flex;
  justify-content: space-between;
  flex-flow: row;
  flex-wrap: wrap;
  gap: 40px;
  height: min-content;
  overflow: visible;
  padding: 0px;
}

.projects__head {
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

.projects__title {
  font-family: 'Neue Machina';
  font-size: 90px;
  text-align: center;
  color: black;
  padding: 0;
  margin: 0;
}

.projects__name {
  font-family: 'PP Migra Italic Extrabold Italic', serif;
  color: rgb(49, 189, 214);
  transform: rotate(-6deg);
  font-size: 90px;
  text-align: center;
  width: fit-content;
  padding: 0;
  margin: -20px 0 -20px;
  height: fit-content;
}

.projects__desc {
  color: black;
  font-family: 'PP Neue Machina Regular';
  max-width: 50%;
  font-size: 22px;
  text-align: left;
  line-height: 1.5;
  margin-top: 30px;
}

.projects__icon {
  position: absolute;

  &--sstar {
    left: 185px;
    top: 60px;
    transform: rotate(-30deg);
  }

  &--fstar {
    right: 20px;
    bottom: -20px;
    transform: rotate(-30deg);
  }
}

.projects__list {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(560px, 1fr));
  flex-wrap: wrap;
  column-gap: 0px;
  row-gap: 0px;
  justify-content: center;
  padding: 0;
  margin: 0;
}

.projects__item {
  z-index: 0;
  // max-width: 720px;
  // min-width: 560px;
  padding: 26px 32px;
  font-family: Helvetica, 'PP Neue Machina Regular';
  color: black;
}

.case__title {
  font-size: 36px;
  font-weight: 500;
  margin: 18px 0 6px;
}

.case__desc {
  font-size: 18px;
  line-height: 1.5;
}

.case__media {
  width: 100%;
  border-radius: 20px;
  object-fit: cover;
}

.case__actions {
  place-content: center;
  display: flex;
  gap: 10px;
  align-items: center;
}

.case__link {
  cursor: pointer;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
  padding: 18px 24px;
  font-family: 'PP Neue Machina Regular';
  border: 1.4px solid #020202;
  color: #020202;
  background-color: transparent;
  border-radius: 40px;
  line-height: 1;
  font-size: 22px;
  transition: all .5s;
  margin: 10px;

  &:hover {
    color: white;
    background-color: #020202;
    border: 1px solid transparent;

    & .case__follow {
      filter: invert(100%);
    }
  }

  &--rep {
    padding: 4px;
    border-radius: 48px;
    border: 1px solid transparent;

    width: 50px;
    aspect-ratio: 1;

    & .case__follow {
      margin: 0;
      padding: 0;
      width: 40px;

    }

    &:hover {
      background-color: #020202;

      & .case__follow {
        filter: invert(100%);
      }
    }
  }
}

.case__link-text {
  padding: 0;
  margin: 0;
}

@media screen and (max-width: 1080px) {
  .projects__desc {
    color: black;
    font-family: 'PP Neue Machina Regular';
    max-width: 100%;
    font-size: 20px;
    padding: 0 28px;
    margin-top: 10px;

  }
}

@media screen and (max-width: 768px) {
  .projects__desc {
    max-width: 100%;
    font-size: 20px;
  }

  .projects__icon--fstar {
    right: 20px;
    bottom: -20px;
    transform: rotate(-30deg);
  }

  .case__title {
    font-size: 22px;
  }

  .case__desc {
    font-size: 16px;
    line-height: 1.4;
    padding: 0 20px;
    margin-bottom: 6px;
  }

  .case__badge {
    border-radius: 60px;
  }

  .case__link {
    padding: 14px 20px;
    border: 1px solid #020202;
    font-size: 18px;

    &--rep {
      padding: 0px 5px;
      border-radius: 48px;
      border: 1px solid transparent;
      width: 30px;

      &:hover {}

      & .case__follow {
        width: 40px;
        height: 40px;
      }
    }
  }


}

@media screen and (max-width: 560px) {

  .projects__icon--sstar {
    display: none;
  }

  .projects__name {
    font-size: 16em;
    transform: rotate(-4deg);

  }

  .projects__title {
    font-size: 16em;
  }

  .projects__icon--sstar {
    width: 6em;
    top: 60px;
  }

  .projects__desc {
    font-size: 16px;
    padding: 0 20px;
  }

  .case__title {
    font-size: 20px;
  }

  .case__desc {
    font-size: 14px;
    line-height: 1.4;
    padding: 0;
    margin-bottom: 2px;
  }

  .projects__list {
    list-style: none;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    flex-wrap: wrap;
    column-gap: 20px;
    row-gap: 20px;
    justify-content: center;
    padding: 0;
    margin: 0;
  }

  .projects__item {
    padding: 0;
  }

  .case__badge-title {
    font-weight: 600;
    font-size: 12px;
    margin: 0;
  }

  .case__badge {
    border-radius: 60px;
    border: 1px solid rgb(73, 73, 73);
    padding: 2px 8px;
    opacity: 0.6;
  }

  .case__link {
    padding: 10px 18px;
    border: 1px solid #020202;
    font-size: 16px;

    &--rep {
      padding: 2px 2px;
      border-radius: 48px;
      border: 1px solid transparent;
      width: 30px;

      &:hover {}

      & .case__follow {
        width: 30px;
        height: 30px;
      }
    }
  }

  .projects__icon--fstar {
    display: none;
  }
}

.case__badges {
  list-style: none;
  display: flex;
  column-gap: 8px;
  row-gap: 4px;
  align-items: center;
  margin: 8px auto 12px;
  padding: 0;
  flex-wrap: wrap;
}

.case__badge {
  border-radius: 60px;
  border: 1.4px solid rgb(73, 73, 73);
  padding: 4px 10px;
  opacity: 0.6;
}

.case__badge-title {
  font-weight: 400;
  font-size: 16px;
  font-family: Helvetica, Arial, sans-serif;

  margin: 0;
}
</style>