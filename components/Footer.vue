<template>
    <footer class="site-footer">
      <div class="container footer-inner">
        <div class="footer-section">
          <h5 class="footer-title">О нас</h5>
          <p>Котлы и котельное оборудование Барнаул — надёжность с 1998 года</p>
        </div>
        <div class="footer-section">
          <h5 class="footer-title">Разделы</h5>
          <ul>
            <li><NuxtLink to="/">Главная</NuxtLink></li>
            <li><NuxtLink to="/catalog">Каталог</NuxtLink></li>
            <li><NuxtLink to="/about">О нас</NuxtLink></li>
            <li><NuxtLink to="/blog">Статьи</NuxtLink></li>
            <li><NuxtLink to="/contact">Контакты</NuxtLink></li>
          </ul>
        </div>
        <div class="footer-section">
          <h5 class="footer-title">Контакты</h5>
          <p>+7 (3852) 123-456</p>
          <p>info@kotly-barnaul.ru</p>
          <p>г. Барнаул, ул. Промышленная, 10</p>
        </div>
        <div class="footer-section social">
          <h5 class="footer-title">Мы в соцсетях</h5>
          <!-- иконки соцсетей -->
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 1998–2025 Котлы Барнаул. Все права защищены.</p>
      </div>
    </footer>
  </template>
  
  <style lang="scss" scoped>
  .site-footer {
    background: var(--primary);
    color: #fff;
  
    .footer-inner {
      @include container();
      display: flex;
      flex-wrap: wrap;
      gap: 2rem;
      padding: 2rem 0;
      justify-content: space-between;
    }
  
    .footer-section {
      flex: 1 1 200px;
  
      .footer-title {
        margin-bottom: .5rem;
        font-size: 1.1rem;
        font-weight: 600;
      }
  
      p, ul, li a {
        font-size: .95rem;
        color: #fff;
      }
  
      ul {
        list-style: none;
        padding: 0;
        li + li { margin-top: .5rem; }
      }
  
      a:hover {
        text-decoration: underline;
      }
    }
  
    .footer-bottom {
      background: rgba(0,0,0,0.1);
      text-align: center;
      padding: .75rem 0;
      font-size: .85rem;
    }
  }
  </style>
  