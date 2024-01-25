<template>
  <div>
    <h1>Template Syntax</h1>
    <p>
      Vue uses an HTML-based template syntax that allows you to declaratively bind the renedered DOM
      to the underlying component instance's data.
    </p>
    <p>
      Vue compliles the templates into highly-optimized js code. Combine with the reactiviy system,
      Vue can intelligently figure out the minimal number of components to re-render and apply the
      minimal amount of DOM manipulations when the app state changes.
    </p>
    <div>
      <ol>
        <h2>
          <li>{{ titles[0] }}</li>
        </h2>
        <div>
          <p>
            The most basic form of data binding is text interpolation using the
            {{ mustache }} syntax.
          </p>
        </div>
        <h2>
          <li>{{ titles[1] }}</li>
        </h2>
        <div>
          <p>
            The double {{ mustache }}es interpret the data as plain text(not HTML). In order to
            output real HTML, you will need to use the {{ built_in_directives[1] }} directive.
          </p>
          <ul>
            <li>rawHtml: {{ rawHtml }}</li>
            <li>{{ built_in_directives[1] }}: <span v-html="rawHtml"></span></li>
          </ul>
          <p>📌Directives are prefixed with v- to indicate that they are special attributes provided by Vue, and they apply special reactive behavior to the rendered DOM.</p>
          <p>✅Built-in Directives include: 
            <ul>
              <li v-for="directive in built_in_directives" v-bind:key="directive">{{ directive }}</li>
            </ul>
          </p>
        </div>
        <h2>
          <li>{{ titles[2] }}</li>
        </h2>
        <h2>
          <li>{{ titles[3] }}</li>
        </h2>
        <h2>
          <li>{{ titles[4] }}</li>
        </h2>
      </ol>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
    const titles = [
      'Text Interpolation',
      'Raw HTML',
      'Attribute Bindings',
      'Using javascript Expressions',
      'Directives'
    ]
    const built_in_directives = [
      'v-text',
      'v-html',
      'v-show',
      'v-if',
      'v-else',
      'v-else-if',
      'v-for',
      'v-on',
      'v-bind',
      'v-model',
      'v-slot',
      'v-pre',
      'v-once',
      'v-memo',
      'v-cloak'
    ]
    const mustache = ref('Mustache')
    const rawHtml = '<span style="color:blue">This is blue</span>'
    return { titles, built_in_directives, mustache, rawHtml }
  }
}
</script>

<style lang="scss" scoped></style>
