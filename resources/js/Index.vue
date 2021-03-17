<template>
    <div id="main">
        <header id="header">
            <h2 class="text-center bg-info text-danger">
                <router-link :to="{name: 'home'}">
                    BOOK
                </router-link>
            </h2>
            <navigationMenu></navigationMenu>
        </header>
        <div id="content">
            <router-view></router-view>
        </div>
    </div>
</template>

<script>
  import navigationMenu from './components/Menu.vue'
  export default {
    data() {
      return {
        //
      }
    },
    components: {
      navigationMenu
    }
  }
</script>
