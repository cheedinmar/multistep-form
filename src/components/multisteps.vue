<template>
  <div class="w-1/2 m-auto">
    <component v-bind:is="steps[currentStep].component" />
     <div class="items-center justify-between flex mx-auto">
        <button
        class="
          text-center
          bg-green-500
          rounded
          px-8
          py-2
          font-semibold
          rounded
          text-white text-2xl
          mt-4
        "
        @click="previous"
        v-if="currentStep !== 0"
      >
        Previous
      </button>
       <button
        class="
          text-center
          bg-green-500
          rounded
          px-8
          py-2
          font-semibold
          rounded
          text-white text-2xl
          mt-4
        "
        @click="next"
        v-if="currentStep < steps.length -1"
      >
        Next
      </button>
      <button
        class="
          text-center
          bg-green-500
          rounded
          px-8
          py-2
          font-semibold
          rounded
          text-white text-2xl
          mt-4
        "
        v-else
      >
        Submit
      </button>
     </div>
  </div>
</template>

<script>
import Information from "./steps/information.vue";
import About from "./steps/about.vue";
import Profile from "./steps/profile.vue";
export default {
  name: "Multisteps",
  data() {
    return {
      currentStep: 0,
      steps: [
        {
          component: Information,
        },
        {
          component: About,
        },
        {
          component: Profile,
        },
      ],
    };
  },
  components: {
    Information,
    About,
    Profile,
  },
  methods:{
    next(){
      this.currentStep +=1;
    },
    previous(){
      this.currentStep -=1
    }
  }
};
</script>

<style>
</style>