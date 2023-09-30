<template>
    <footer class="footer">
      <div class="footer__wrapper wrapper">
        <p class="footer__info">
            Киверин Андрей, 2023
        </p>
        <a href="tel: 89531370800" class="footer__tel">+7 (953) 137-08-00</a>
        <ul class="footer__social social">
          <li class="social__item">
            <a href="https://vk.com/andkiv" class="social__link" target="_blank" >
              <img src="../assets/icons/vk.svg" alt="vk icon" class="social__icon">
            </a>
          </li>
          <li class="social__item">
            <a href="https://github.com/akiverin" class="social__link" target="_blank" >
              <img src="../assets/icons/github.svg" alt="github icon" class="social__icon">
            </a>
          </li>
          <li class="social__item">
            <a href="https://www.behance.net/kiverin03fb9c" class="social__link" target="_blank" >
              <img src="../assets/icons/behance.svg" alt="behance icon" class="social__icon">
            </a>
          </li>
          <li class="social__item">
            <a href="https://t.me/andkiv" class="social__link" target="_blank" >
              <img src="../assets/icons/telegram.svg" alt="telegram icon" class="social__icon">
            </a>
          </li>
        </ul>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: 'FooterComponent'
  }
  </script>
  
  <style lang="scss" scoped>
  .footer {
    background-color: transparent;
    color: #fff;
    padding: 2rem 0;
  }

  
  .footer__info {
    font-family: 'PP Neue Machina Regular', Inter, arial, sans-serif;
    font-size: 22px;
  }

  .footer__tel {
    font-family: 'PP Neue Machina Regular', Inter, arial, sans-serif;
    font-size: 22px;
    text-decoration: none;
    color: rgb(49, 189, 214);
    &:hover {
      text-decoration:underline;
    }
  }

  .footer__social {
    list-style: none;
    display: flex;
    place-self: center;
    gap: 20px;
    justify-content: center;
    padding: 0;
    margin: 20px 0;
  }

  .social__link {
    padding: 6px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #fff;
    border: 1px solid transparent;
    border-radius: 16px;
    transition: all .2s ease-in-out;

    &:hover {
      background-color: transparent;
      border: 1px solid #fff;
      .social__icon {
        filter: invert(100%);
      }
    }
  }
  .social__icon {
    height: 40px;
    width: 40px;
    color: white
  }
  </style>