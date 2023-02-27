<template>
  <!-- Делаем обертку для нашего шаблона -->
  <div ref="wrapper" class="wrapper">
    <TheHeader class="wrapper__header" :has-offset="hasOffset" />
    <main class="wrapper__header">
        <TheStore ref="store" />
        <TheDiscount ref="discount" />
        <TheAbout ref="about" />
    </main>
    <TheFooter class="wrapper__footer" />
  </div>
</template>

<script>
import TheHeader from '@/component/TheHeader.vue';
import TheFooter from '@/component/TheFooter.vue';
import TheStore from '@/component/TheStore.vue';
import TheDiscount from '@/component/TheDiscount.vue';
import TheAbout from '@/component/TheAbout.vue';

export default {
    components: {
        TheHeader,
        TheFooter,
        TheStore,
        TheDiscount,
        TheAbout,
    },
    data: () => ({
        hasOffset: false,
    }),
    created() {
        window.addEventListener('hashchange', () => {
            const { hash } = window.location;
            this.$refs[hash.slice(1)].$el.scrollIntoView({ behavior: 'smooth' });
        });
    },
    mounted() {
        const { wrapper } = this.$refs;
        setTimeout(() => wrapper.scrollTo(0, 0), 1);

        wrapper.addEventListener('scroll', (event) => {
            const { scrollTop } = wrapper;
            this.hasOffset = scrollTop !== 0;
        });
    },
};
</script>

<style lang="scss" scoped>
.wrapper {
  display: grid;
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  grid-template-areas:  'header'
                        'main'
                        'footer';
  grid-template-rows: auto
                      1fr
                      auto;
}
</style>