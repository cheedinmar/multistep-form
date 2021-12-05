<template>
  <div class="w-1/2 m-auto">
  <div v-if="!submitted">
     <component
      :is="steps[currentStep].component"
      :formValue="formValue[steps[currentStep].label]"
      @formValueChange="updateFormValue"
    />
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
        v-if="currentStep < steps.length - 1"
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
        @click="submit"
      >
        Submit
      </button>
    </div>
  </div>
  <div v-else class="text-3xl font-bold text-center text-green-500 shadow-lg p-10 ">
    <span>Thank you for submitting the form. <br/><br/> We will get back to you </span>
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
      submitted: false,
      formValue: {
        information: {
          name: "",
          age: 0,
          dob: "",
          email: "",
        },
        about: {
          address: "",
          gender: "",
        },
        profile: {
          profilePicture: "",
          bio: "",
        },
      },
      currentStep: 0,
      steps: [
        {
          component: Information,
          label: "information",
        },
        {
          component: About,
          label: "about",
        },
        {
          component: Profile,
          label: "profile",
        },
      ],
    };
  },
  components: {
    Information,
    About,
    Profile,
  },
  methods: {
    next() {
      this.currentStep += 1;
    },
    previous() {
      this.currentStep -= 1;
    },
    submit() {
      this.submitted = true;
      console.log(this.formValue);
    },
    updateFormValue(payload){
      this.formValue ={
        ...this.formValue,
        [payload.label]:payload.data
      }
    }
  },
};
</script>

<style>
</style>