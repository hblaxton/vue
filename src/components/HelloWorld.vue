<template>
  <h1>{{ msg }}</h1>

<button class="duplicate" v-on:click="duplicate">duplicate</button>
<button class="button" v-on:click="color">button</button>
<button class="modifytitle" v-on:click="name">modifytitle</button>
<button class="button" v-on:click="deletes">delete me</button>
<button data-toggle-btn v-on:click="toggle">toggle description</button>

<div class="wrapper">
  <div class="container">
  <img class="image" src="https://upload.wikimedia.org/wikipedia/commons/e/eb/Ash_Tree_-_geograph.org.uk_-_590710.jpg">
  <div class="header">
    <h3>Landscaping Company</h3>
    <h4>A beautiful green tree</h4>
  </div>
</div>
  <details class="details">
    <summary>Description</summary>
    <div>
      <ul>
        <li>A tree as beautiful as this one should be cut down</li>
        <li>Trees!</li>
       </ul>
    </div>
    </details>
</div>


  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Documentation
    </a>
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Documentation</a>
  </p>

  <button type="button" @click="state.count++">count is: {{ state.count }}</button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
</template>

<script setup>
import { defineProps, reactive } from 'vue'

defineProps({
  msg: String
})

const state = reactive({ count: 0 })
</script>

<script>
const container = document.querySelector(".container");
const bg = document.querySelector("#bg");
const details = document.querySelector('summary');

export default {
methods: {
toggle(){
document.querySelector('button[data-toggle-btn]').addEventListener('click', (e) => {
  if (details.parentNode.getAttribute('open')) {
    details.parentNode.removeAttribute('open');
  }
  else {
    details.parentNode.setAttribute('open','open');    
  }
});
},

// duplicate the 1st item
duplicate(){
document.querySelector('.duplicate').addEventListener('click', function(e) {
  const itemToClone = document.querySelector('.wrapper').cloneNode(true);
  document.body.appendChild(itemToClone);
});
},

color(){
bg.addEventListener("click", (e) => {
  const colors = ["red", "orange", "yellow", "green", "blue", "purple"];
  const randomColor = colors[Math.floor(Math.random() * colors.length)];
  container.style.backgroundColor = randomColor;
});
},
 

name(){
document.querySelector('.modifytitle').addEventListener('click', function(e) {
  let name = prompt("Rename the company");
  if (name) {
    document.querySelector('.wrapper h3').innerText = name;
  }
});
},

deletes(){
document.querySelector('#deletelastcard').addEventListener('click', function(e) {
  let wantsTo = confirm("Are you so sure?");
  if (wantsTo) {
    if (document.querySelector('.wrapper:last-child') !== document.querySelector('.wrapper')) {
      document.querySelector('.wrapper:last-child').remove();      
    }
    else {
      alert("YOU CAN NOT DELETE OUR TREE");
    }
  }
});
},
}
}
</script>

<style scoped>
a {
  color: #42b983;
}
</style>

