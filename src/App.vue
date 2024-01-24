<template>
  <h1>Declarative Rendering</h1>
  <h2>The core feature of Vue is declarative rendering</h2>
  <p>
    You can describe the HTML based on javascript state by using a template syntax that extends
    HTML.
  </p>
  <h2>Reactive</h2>
  <p>Reactive State: When the state changes the HTML updates automatically.</p>
  <p>By using Vue's reactive() API, reactive state can be declared.</p>
  <p>Objects created from reactive() are js proxies that work just like normal object.</p>
  <ul>
    <li>javascriptObject: [Object]{{ javascriptObject }}</li>
    <li>reactiveObject: [Reactive]{{ reactiveObject }}</li>
  </ul>
</template>

<script>
import { reactive } from 'vue'

export default {
  setup() {
    const javascriptObject = {
      count: 0
    }
    const reactiveObject = reactive(javascriptObject)
    return { javascriptObject, reactiveObject }
  }
}
</script>

<style lang="scss" scoped></style>
