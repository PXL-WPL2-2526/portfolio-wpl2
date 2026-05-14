<script setup>
import { useI18n } from 'vue-i18n'
const { t } = useI18n()
</script>

<template>
  <section>
    <h3>{{ t('logo.frontend') }}</h3>
    <h3>{{ t('logo.graphic') }}</h3>
    <img src="@/assets/img/logo.svg" alt="gielboogaertsstudio logo"/>
    <h3 class="right">{{ t('logo.book') }}</h3>
  </section>
</template>

<style scoped>
section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0 1rem;
}

h3 {
  font: var(--header-1);
  color: var(--primary-color);
  align-self: start;
  position: relative;
  top: 4rem;
}

.right {
  align-self: end;
  top: -4rem;
}

img {
  width: 35%;
}

@media screen and (max-width: 450px) {
  .right {
    top: -1rem;
  }

  h3 {
    top: 1rem;
  }
}
</style>
