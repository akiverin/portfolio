<template>
    <section class="projects">
      <div class="projects__wrapper wrapper">
        <div class="projects__info">
            <div class="projects__head">
                <h1 class="projects__title">Все мои</h1>
                <img src="../assets/icons/strokeStar.svg" alt="decorate icon" class="projects__icon projects__icon--sstar">
                <h1 class="projects__name">Projects</h1>
            </div>
            <p class="projects__desc">Здесь вы найдете некоторые из моих проектов, которые я реализовал в качестве фронтенд разработчика и дизайнера. Многие из них были выполнены во время моего обучения, а также в командной работе и в рамках проектной деятельности.</p>
            <img src="../assets/icons/fillStar.svg" alt="decorate icon" class="projects__icon projects__icon--fstar">
            <ul class="projects__list">
                <li  class="projects__item case" v-for="item, key in projects" :key="key" data-scroll :data-scroll-speed="(4-key)%2/10">
                    <video v-if="item.media.type == 'video'" loop autoplay playsinline muted class="case__media" :src="require('../assets/'+item.media.title)"></video>
                    <img v-if="item.media.type == 'image'" :src="require('../assets/'+item.media.title)" alt="image for project case" class="case__media">
                    <h2 class="case__title">{{ item.name }}</h2>
                    <p class="case__desc">{{ item.desc }}</p>
                    <div class="case__actions">
                        <a v-if="item.link" :href="item.link" class="case__link" target="_blank">
                            Перейти
                            <img src="../assets/icons/open.svg" alt="follow the link icon" class="case__follow">
                        </a>
                        <a v-if="item.rep" :href="item.rep" class="case__link" target="_blank">
                          Репозиторий
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
      data(){
        return {
            projects: [
                {
                    name: 'Веб-сайт для школы',
                    desc: 'Современный подход к разработке школьного веб-портала 🌐, обеспечивающего комфортное взаимодействие для учителей, учеников и родителей. Мы использовали VueX 💡 для эффективного управления данными, обеспечивая адаптивность и собственный дизайн 🎨 для всех пользователей. Наши запросы Axios обеспечивают быстрый доступ к информации 🚀, а плагины карт делают навигацию простой и интерактивной, проделана большая работа с формами. Результат получен итогом сотрудничества в команде.',
                    media: {
                        type: 'video',
                        title: 'project1.mp4'
                    },
                    link: 'http://our-school.std-1725.ist.mospolytech.ru/',
                    rep: 'https://github.com/web-polytech/2023',
                    badges: ['в команде','обучение','свой дизайн'],
                },
                {
                    name: 'Сервис для тренировок',
                    desc: '🚀 Мой сервис обеспечивает адаптивность для всех устройств, использует передовые технологии во фронтенде, такие как Pinia, axios и fetch для работы с хранилищами, состояниями и API. С многоуровневым роутингом, личным кабинетом 💼, формами регистрации и авторизации, а также дружелюбным дизайном 🎨 и доступностью с читаемостью, этот проект демонстрирует мои навыки в создании современных веб-приложений. К тому же, учёт и работа с датами в календаре 📅 добавляют дополнительный функционал планирования и удобство для пользователей.',
                    media: {
                        type: 'video',
                        title: 'project2.mp4'
                    },
                    link: 'http://polyfit.std-1725.ist.mospolytech.ru/',
                    rep: 'https://github.com/polyfit-live/polyfit',
                    badges: ['обучение','свой дизайн'],
                },
                {
                    name: 'Сайт для игры',
                    desc: 'Окунитесь в завораживающее онлайн-царство со своим игровым сайтом fantasy world. Откройте для себя визуально потрясающий мир фантазий. Реализован современный тематический дизайн интерфейса 🖼, легко интегрированный с базами данных, управляемыми API, удобные формы, адаптивный дизайн и множество удобных функций 💻. Отправляйтесь в незабываемое путешествие уже сегодня! 🚀',
                    media: {
                        type: 'image',
                        title: 'project3.jpg'
                    },
                    link: 'http://webexam2023.std-1725.ist.mospolytech.ru/',
                    rep: 'https://github.com/akiverin/webExam3',
                    badges: ['обучение','свой дизайн'],
                },
                {
                    name: 'Новостной портал арт студии',
                    desc: 'Минималистичный дизайн демонстрирует работы каждого художника или фотографа в галерее 📷, в которой различные изображения, которые органично вписываются в дело студии. Навигация интуитивно понятна благодаря адаптивному пользовательскому интерфейсу, позволяющему посетителям как настольных компьютеров, так и мобильных устройств 📱 просматривать основные моменты и новости в удобном режиме 🎯, не отвлекаясь ни на что другое.',
                    media: {
                        type: 'video',
                        title: 'project4.mp4'
                    },
                    link: 'http://web.std-1725.ist.mospolytech.ru/',
                    rep: 'https://github.com/akiverin/web-lab',
                    badges: ['обучение','свой дизайн'],
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
    color: rgb(49,189,214);
    transform: rotate(-6deg);
    font-size: 90px;
    text-align: center;
    width: fit-content;
    padding: 0;
    margin: 0;
    height: fit-content;
  }

  .projects__desc {
    color: black;
    font-family: 'PP Neue Machina Regular';
    max-width: 50%;
    font-size: 22px;
    text-align: left;
    line-height: 1.5;
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
    grid-template-columns: repeat(auto-fit,minmax(560px, 1fr));
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
    padding: 20px;
    font-family: 'PP Neue Machina Regular';
    color: black;
  }

  .case__title {
    font-size: 36px;
    font-weight: 800;
  }
  .case__desc {
    font-size: 18px;
    line-height: 1.5;
    text-align: justify;
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

  }

  .case__link {
    cursor: pointer;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    text-decoration: none;
    padding: 18px 22px;
    font-family: 'PP Neue Machina Regular';
    border: 1px solid #020202;
    color: #020202;
    background-color: transparent;
    border-radius: 12px;
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
  }

  .case__follow {
    position: absolute;
    top: 2px;
    right: 2px;
    height: 18px;
    width: 18px;
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
    }
  }
  @media screen and (max-width: 560px) {

    .projects__name{ 
      font-size: 16em;
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
    }

    .case__title {
      font-size: 20px;
    }

    .case__desc {
      font-size: 14px;
      line-height: 1.4;
    }
    .projects__list {
      list-style: none;
      display: grid;
      grid-template-columns: repeat(auto-fit,minmax(350px, 1fr));
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
  }
</style>