<template>
  <h1>Declarative Rendering</h1>
  <div>
    <h2>The core feature of Vue is declarative rendering</h2>
    <p>
      You can describe the HTML based on javascript state by using a template syntax that extends
      HTML.
    </p>
  </div>
  <div>
    <h2>Reactive State</h2>
    <p>Reactive State: When the state changes the HTML updates automatically.</p>
    <p>By using Vue's reactive() API, reactive state can be declared.</p>
    <p>
      Reactive objects are js proxies that work just like normal object. The difference is that Vue
      is able to intercept the access and mutation of all properties of a reactive object for
      reactivity tracking and triggering.
    </p>
    <ul>
      <li>javascriptObject: [Object]{{ javascriptObject }}</li>
      <li>reactiveObject: [Reactive]{{ reactiveObject }}</li>
    </ul>
  </div>
  <div>
    <h2>reactive() vs ref()</h2>
    <p>Declaring Reactive State</p>
    <ol>
      <li>ref()</li>
      <p>In Composition API, for declaring reactive state, using the ref() is recommended</p>
      <ul>
        <li>
          ref() takes the argument(any value type) and returns it wrapped with a ref object with a
          .value property.
        </li>
        <li>To access refs in a component's template, return them from a component's setup().</li>
        <li>📌setup() is a special hook dedicated for the Composition API.</li>
        <li>
          ✨Notice: we did not need to append .value when using the ref in the template. (refs() are
          automatically unwrapped)
        </li>
        <li>you can also mutate a ref directly in event handlers</li>
        <li>
          refObject: [Object]{{ refObject
          }}<button @click="increment">refCount: {{ refCount }}</button>
        </li>
      </ul>
      <li>reactive()</li>
      <p>
        In Composition API, there's another way to declare reactive state with the reactive() API.
      </p>
      <ul>
        <li>reactive() only works on Objects(Array, Map, Set ...)</li>
        <li>
          reactive() makes an object itself reactive, unlike a ref which wraps the inner value in a
          special object.
        </li>
        <li>
          reactive() converts the object deeply: nested objects are also wrapped with reactive()
          when accessed. It is also called by ref() internally when the ref value is an object.
        </li>
        <li>
          reactiveObject: [Object]{{ reactiveObject
          }}<button @click="reactiveObject.count++">reactCount: {{ reactiveObject.count }}</button>
        </li>
      </ul>
    </ol>
  </div>
  <div>
    <h2>Why Refs?</h2>
    <p>You might be wondering why we need refs with the .value instead of plain variables.</p>
    <h2>How does Vue's reactivity system work?</h2>
    <p>It's all about a dependency-tracking based reactivity system.</p>
    <ol>
      <li>
        When you use a ref in a template, and change the ref's value later, Vue automatically
        detects the change and updates the DOM accordingly.
      </li>
      <li>
        When a component is rendered for the first time, Vue tracks every ref that was used during
        the render.
      </li>
      <li>
        Later on, when a ref is mutated, it will trigger a re-render for components that are
        tracking it.
      </li>
      <li>
        📌The .value property of ref gives Vue the opportunity to detect when a ref has been
        accessed or mutated.
      </li>
    </ol>
    <h2>Reactive Proxy vs Original</h2>
    <p>
      📒Note that the returned value from reactive() is a Proxy of the Original object, whici is not
      equal to the original object.
    </p>
    <h2>❗Limitations of reactive()</h2>
    <p>
      Due to these limitations, we recomment using ref() as the primary API for declaring reactive
      state.
    </p>
    <ol>
      <li>
        <h3>Limited value types</h3>
        <p>It only works for object types(objects, arrays) and collection types(map, set).</p>
        <p>It cannot hold primitive types(string, number, boolean).</p>
      </li>
      <li>
        <h3>Cannot replace entire object</h3>
        <p>
          We can't easily replace a reactive object becuase the reactivity connection to the first
          reference is lost
        </p>
      </li>
      <li>
        <h3>Not destructure-friendly</h3>
        <p>we will lose the reactivity connection when the state is destructured.</p>
      </li>
    </ol>
  </div>
  <div><h2>createApp()</h2></div>
</template>

<script>
import { reactive, ref } from 'vue'

export default {
  setup() {
    const javascriptObject = {
      count: 0
    }
    const reactiveObject = reactive(javascriptObject)
    const refObject = ref('.value property')
    const refCount = ref(0)
    function increment() {
      refCount.value++
    }
    return { javascriptObject, reactiveObject, refObject, refCount, increment }
  }
}
</script>

<style lang="scss" scoped></style>
