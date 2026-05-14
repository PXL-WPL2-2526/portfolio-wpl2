<script setup>
import { useI18n } from 'vue-i18n'
const { t } = useI18n()
</script>

<template>
  <section>
    <h2>{{ t('welcome.heading1') }}</h2>
    <div>
      <p>{{ t('welcome.body') }}</p>
    </div>
    <h2 class="right">{{ t('welcome.heading2') }}</h2>
  </section>
</template>

<style scoped>
section {
  width: 100%;
  padding: 0 1rem;
  display: flex;
  flex-direction: column;
  gap: 5rem;
}

h2 {
  font: var(--headline);
  color: var(--primary-color);
}

.right {
  text-align: right;
}

div {
  width: 100%;
  display: flex;
  justify-content: center;
}

p {
  font: var(--header-3);
  width: 15rem;
  margin-right: 40vw;
}

@media screen and (max-width: 450px) {
  p {
    margin-right: 10vw;
    width: 10rem
  }
}
</style>
