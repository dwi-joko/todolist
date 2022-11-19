<script>
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap";
import * as Vue from "vue"; // in Vue 3
import axios from "axios";
import VueAxios from "vue-axios";

// import { Popover } from bootstrap;
const app = Vue.createApp();
app.use(VueAxios, axios);

import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header class="header">
    <div class="container">
      <h4>To Do List App</h4>
    </div>
  </header>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header> -->

  <RouterView />
</template>
