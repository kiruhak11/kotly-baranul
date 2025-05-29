<template>
    <section 
      class="hero-section" 
      ref="heroRef"
    >
      <div class="hero-overlay"></div>
      <div class="container hero-content" :class="{ 'in-view': contentVisible }">
        <h1>Надёжные котлы для вашего дома и бизнеса</h1>
        <p>Котлы и котельное оборудование Барнаул — экспертность с 1998 года</p>
        <div class="cta-buttons">
          <NuxtLink to="/catalog" class="btn btn-primary">Перейти в каталог</NuxtLink>
          <NuxtLink to="/contact" class="btn btn-secondary">Оставить заявку</NuxtLink>
        </div>
      </div>
    </section>
  
    <section class="advantages-section container">
      <div class="advantage-item">
        <svg class="icon" viewBox="0 0 24 24">
          <!-- пример иконки щита -->
          <path d="M12 1l8 4v6c0 5-3.5 9.7-8 11-4.5-1.3-8-6-8-11V5l8-4z"/>
        </svg>
        <h3>Гарантия качества</h3>
        <p>Сертифицированное оборудование от ведущих производителей.</p>
      </div>
      <div class="advantage-item">
        <svg class="icon" viewBox="0 0 24 24">
          <!-- пример иконки энергоэффективности -->
          <path d="M6 2h12l-6 20-6-20z"/>
        </svg>
        <h3>Энергоэффективность</h3>
        <p>Современные решения для экономии топлива и снижения затрат.</p>
      </div>
      <div class="advantage-item">
        <svg class="icon" viewBox="0 0 24 24">
          <!-- пример иконки поддержки -->
          <path d="M12 12c2.7 0 5-2.3 5-5s-2.3-5-5-5-5 2.3-5 5 2.3 5 5 5zm0 2c-3.3 0-10 1.7-10 5v3h20v-3c0-3.3-6.7-5-10-5z"/>
        </svg>
        <h3>24/7 поддержка</h3>
        <p>Наши менеджеры всегда на связи для оперативного решения ваших задач.</p>
      </div>
    </section>
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted } from 'vue'
  
  const heroRef = ref<HTMLElement | null>(null)
  const contentVisible = ref(false)
  
  onMounted(() => {
    if (heroRef.value) {
      const observer = new IntersectionObserver(
        ([entry]) => {
          if (entry.isIntersecting) {
            contentVisible.value = true
            observer.unobserve(entry.target)
          }
        },
        { threshold: 0.1 }
      )
      observer.observe(heroRef.value)
    }
  })
  </script>
  
  <style lang="scss" scoped>
  @use '@/assets/styles/global/_base.scss' as *;
  .hero-section {
    position: relative;
    background-image: url('@/assets/img/hero.png');
    background-attachment: fixed;
    background-position: center;
    background-size: cover;
    padding: 8rem 0;
    overflow: hidden;
    color: var(--bg);
  
    .hero-overlay {
      position: absolute;
      inset: 0;
      background: rgba(0, 0, 0, 0.5);
    }
  
    .hero-content {
      @include container();
      position: relative;
      z-index: 1;
      text-align: center;
  
      opacity: 0;
      transform: translateY(20px);
      transition: opacity .8s ease-out, transform .8s ease-out;
  
      &.in-view {
        opacity: 1;
        transform: translateY(0);
      }
  
      h1 {
        font-size: 3rem;
        margin-bottom: 1rem;
      }
      p {
        font-size: 1.25rem;
        margin-bottom: 2rem;
      }
      .cta-buttons {
        display: flex;
        gap: 1rem;
        justify-content: center;
  
        .btn-primary {
          @extend .btn;
          background-color: var(--accent);
          color: var(--bg);
        }
        .btn-secondary {
          @extend .btn;
          background-color: var(--bg);
          color: var(--text);
          &:hover {
            background-color: var(--accent);
            color: var(--bg);
          }
        }
      }
    }
  }
  
  .advantages-section {
    margin: 4rem 0;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 2rem;
    text-align: center;
  
    .advantage-item {
      @extend .card;
      padding: 2rem 1.5rem;
      background: rgba(255,255,255,0.1);
      color: var(--text);
  
      .icon {
        width: 48px;
        height: 48px;
        margin-bottom: 1rem;
        fill: var(--accent);
      }
      h3 {
        font-size: 1.25rem;
        margin-bottom: .5rem;
      }
      p {
        font-size: .95rem;
        color: var(--secondary);
      }
    }
  }
  </style>
  