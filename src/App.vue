<template>
  <div class="container">
    <div class="card">
      <h1>Vue Composition Api</h1>
      <hr />
      <framework-info
        :name="name"
        :version="version"
        @change-version="changeVersion"
      />

      <div class="foem-control">
        <input type="text" ref="input" />
        <input type="text" v-model="firstName" />
      </div>

      <button class="btn" @click="changeInfo">Изменить</button>
    </div>
  </div>
</template>

<script>
import { ref, computed, watch } from "vue";

import FrameworkInfo from "./FrameworkInfo";

export default {
  setup() {
    const name = ref("VueJS");
    const version = ref(3);
    const firstName = ref("");

    const input = ref(null);

    function changeInfo() {
      name.value = "React sucks";
      version.value = 1;

      console.log(input.value, "ref");
    }

    function changeVersion(newVersion) {
      version.value = newVersion
    }

    const doubleVersion = computed(() => {
      return version.value * 2;
    });

    watch(firstName, (newValue, oldValue) => {
      console.log(newValue, oldValue);
    });

    return {
      name,
      version,
      changeInfo,
      doubleVersion,
      input,
      firstName,
      changeVersion
    };
  },

  components: { FrameworkInfo },
};
</script>
