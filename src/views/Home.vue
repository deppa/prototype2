<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome "/>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import About from '@/views/About.vue'; // @ is an alias to /src
import File from '@/views/File.vue'; // @ is an alias to /src

@Options({
  components: {
    HelloWorld,
    About,
    File
  },
})
export default class Home extends Vue {}
</script>
