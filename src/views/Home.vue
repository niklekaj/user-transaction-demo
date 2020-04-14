<template>
  <div class="c-home">
    <div class="c-home__sections">
    <div :class="{
            'c-home__sections-section': true,
            'c-home__sections-section--active': currentSection === section
          }"
          v-for="section in sections"
          :key="section.id"
          @click="currentSection = section"
    >
      {{ section }}
    </div>
  </div>
  <component v-bind:is="currentSection"></component>
  </div>
</template>

<script>
import  Addresses from './Addresses.vue';
import  Transactions from './Transactions.vue';
import  Update from './Update.vue';

export default {
  name: "Home",
  data() {
    return {
      sections: ["Addresses", "Transactions", "Update"],
      currentSection: "Addresses"
    };
  },
  components: {
    Addresses,
    Transactions,
    Update
  }
};
</script>

<style scoped lang="scss">
    @import "./Home.scss";
</style>
