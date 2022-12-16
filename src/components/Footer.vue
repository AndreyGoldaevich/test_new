<template>
  <footer class="footer">
    <button class="footer__add-button" @click="handleAdd">add</button>
  </footer>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { mapGetters, mapMutations } from 'vuex';

export default defineComponent({
  name: 'AppFooter',
  methods: {
    ...mapMutations({
      addFigure: 'addFigure',
      addConnectors: 'addConnectorsGroup',
    }),
    handleAdd() {
      this.addFigure();
      const { width, height, coords } = this.lastFigure;
      this.addConnectors({
        width: width,
        height: height,
        figurePosition: coords,
      });
    },
  },
  computed: {
    ...mapGetters({ lastFigure: 'getLastFigure' }),
  },
});
</script>

<style scoped>
.footer {
  position: fixed;
  bottom: 15px;
  max-width: 400px;
  width: 100%;
  height: 80px;
  border-radius: 20px;
  padding: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.footer__add-button {
  width: 40px;
  height: 40px;
  background-color: #0b5dea;
  border-radius: 5px;
  transition: 0.3s;
  cursor: pointer;
}
.footer__add-button:hover {
  transform: scale(1.1);
  background-color: #1a65f1;
}
</style>
