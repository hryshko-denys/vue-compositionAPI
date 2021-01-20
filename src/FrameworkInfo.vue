<template>
  <div class="card">
    <p>
      Название: <strong>{{ name }}</strong>
    </p>
    <p>
      Версия: <strong>{{ version }}({{ doubleVersion }})</strong>
    </p>
    <button class="btn warning" @click="changeToThrird">Change to third version</button>
  </div>
</template>

<script>
import { computed } from 'vue'

export default {
  props: ['name', 'version'],
  emits: ['change-version'],
  setup(props, context) {
    const doubleVersion = computed(() => {
      return props.version * 2
    })

    function changeToThrird() {
      context.emit('changeVersion', 3)
    }

    return {
      doubleVersion,
      changeToThrird
    }
  }
  
  // components: {FrameworkInfo}
}
</script>

