<template>
  <div class="c-home">
    <div style="border: 2px solid red;" class="c-home__sections">
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
  <component style="border: 2px solid black;" v-bind:is="currentSection"></component>
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

<style lang="scss">
    .c-home {
      width: 100%;
      display: flex;
      flex-direction: column;


      &__sections {
      display: flex;
      margin-top: 5rem;
      width: 100%;
      justify-content: space-around;
      // align-items: center;
      flex-direction: row;
      color: white;
      font-size: 5rem;

      &-section {
        background: white;
        color: #12e4ac;
        border-radius: 2rem;
        padding: 0 1rem;

        &:hover {
          cursor: pointer;
        }

        &--active {
          text-decoration: underline;
        }
      }
    }
  }
</style>
