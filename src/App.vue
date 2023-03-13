<script setup lang="ts">
import { ref, watch } from "vue";

const show = ref(true);

/**
 * Fonction pour invoquer manuellement le widget
 */
function renderWidget() {
  // @ts-ignore
  if (typeof window.mec?.renderWidget === "function") {
    // @ts-ignore
    window.mec.renderWidget();
  }
}

watch(
  () => show.value,
  () => {
    if (show.value) {
      renderWidget();
    } else {
      const element = document.querySelector(".mec-wcard");
      element?.remove();
    }
  }
);
</script>

<template>
  <div class="flex">
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
    <a href="https://monemprunt.com" target="_blank">
      <img
        src="https://www.monemprunt.com/static/logo-2f1d95c77461634bd37c3ff2b40fe368.svg"
        class="logo"
        alt="Monemprunt logo"
      />
    </a>
  </div>

  <p>
    Ceci est un POC de l'intégration du widget monemprunt avec vuejs, vous
    pouvez retrouver le code sur

    <a href="https://github.com/Fredkiss3/wai-demo-vue" target="_blank"
      >github</a
    >.
  </p>

  <br />

  <p class="read-the-docs">
    Pour plus de détails sur l'intégration du widget, veuillez voir la
    <a
      href="https://monemprunt.atlassian.net/wiki/spaces/TM/pages/36339713/Documentation+Int+gration+du+Widget"
      target="_blank"
      >documentation</a
    >.
  </p>

  <div class="card">
    <button type="button" @click="show = !show">
      {{ show ? "hide" : "show" }} Widget
    </button>
  </div>

  <div
    :hidden="!show"
    class="mec--widget-app"
    data-integration="default"
    data-label="payez wimontant / mois sur wiyear années"
    data-wimodal-btn-class="modal-btn"
    data-montant-bien="310000"
    data-type-calcul="mensualite"
    data-mentions-legales-text="Mentions"
    data-wimodal-btn-mensualite="true"
    data-cle="200623-9HG2Q3"
    data-logo="https://www.monemprunt.com/static/logo-2f1d95c77461634bd37c3ff2b40fe368.svg"
  ></div>
</template>

<style scoped>
.flex {
  display: flex;
  justify-content: center;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.read-the-docs {
  color: #888;
}

button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  background-color: #1a1a1a;
  cursor: pointer;
  transition: border-color 0.25s;
}
button:hover {
  border-color: #646cff;
}
button:focus,
button:focus-visible {
  outline: 4px auto -webkit-focus-ring-color;
}

pre {
  text-align: left;
  background-color: #213547;
  color: #f9f9f9;
  border-radius: 6px;
  padding: 12px;
  max-width: 100%;
  overflow-y: auto;
}

@media (prefers-color-scheme: light) {
  button {
    background-color: #f9f9f9;
  }
}
</style>
