<template>
  <div class="home">

    <JuegosComponents/>
  
  </div>
</template>

<script>
// @ is an alias to /src
import JuegosComponents from '@/components/JuegosComponents.vue';

export default {
  name: 'HomeView',
  components: {
    JuegosComponents
}
}
</script>
