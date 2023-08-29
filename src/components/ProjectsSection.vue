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
                <li class="projects__item case">
                    <video loop autoplay playsinline muted class="case__video" src="../assets/project1.mp4">
                    </video>
                    <h2 class="case__title">Веб-сайт для школы</h2>
                    <p class="case__desc">Современный подход к нашему комплексному обслуживанию, предназначенному как для учителей, учащихся, так и для родителей. Наш школьный портал включает в себя все необходимые функции, легко интегрированные с удобной навигацией и элегантным интерфейсом. Благодаря своей палитре, доступности и простоте наша платформа предназначена и для людей с глазными заболеваниями.</p>
                </li>
                <li class="projects__item case">
                    <video loop autoplay playsinline muted class="case__video" src="../assets/project1.mp4">
                    </video>
                    <h2 class="case__title">Веб-сайт для школы</h2>
                    <p class="case__desc">Современный подход к нашему комплексному обслуживанию, предназначенному как для учителей, учащихся, так и для родителей. Наш школьный портал включает в себя все необходимые функции, легко интегрированные с удобной навигацией и элегантным интерфейсом. Благодаря своей палитре, доступности и простоте наша платформа предназначена и для людей с глазными заболеваниями.</p>
                </li>

            </ul>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
      name: 'ProjectsSection',
  }
  </script>
  
  <style lang="scss" scoped>

  .projects__wrapper {
    border-radius: 40px;
    padding: 40px;
    background-color: white;
  }
  .projects__info {
    position: relative;
    place-content: flex-start;
    align-items: flex-start;
    display: flex;
    justify-content: space-between;
    flex-flow: row;
    flex-wrap: wrap;
    gap: 40px;
    height: min-content;
    overflow: visible;
    padding: 0px;
    position: relative;
    width: 100%;
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
    padding: 0px;
    width: 515px;
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
    font-size: 22px;
    max-width: 50%;
    text-align: left;
    line-height: 1.5;
  }

  .projects__icon {
    position: absolute;
    &--sstar {
        left: 155px;
        top: 50px;
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
    display: flex;
    flex-wrap: wrap;
    gap: 4%;
    justify-content: center;
  }

  .projects__item {
    max-width: 720px;
    min-width: 560px;
    width: 40%;
    padding: 20px;
    border: 1px solid black;
    font-family: 'PP Neue Machina Regular';
    color: black;
  }
  .case__video {
    width: 100%;
    border-radius: 20px;
  }

  @media screen and (max-width: 768px) {
    .projects__desc {
        max-width: 100%;
  }
  .projects__icon--fstar {
        right: 20px;
        bottom: -20px;
        transform: rotate(-30deg);
    }
  }
  </style>
  