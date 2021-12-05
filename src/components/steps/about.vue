<template>
  <p class="text-5xl font-bold mb-9 text-center">Tell Us About Yourself</p>
  <div class="shadow-lg p-10 rounded">
    <div>
      <label for="name" class="font-bold text-2xl"> Where do you live?</label>
      <br />
      <textarea
        v-model="formValue.address"
        @input="onChange"
        name="address"
        id="address"
        class="w-full text-2xl p-2 border-2 rounded border-green-500 mt-4 mb-4"
      />
    </div>

    <div>
      <label for="gender" class="font-bold  text-2xl">Are you a ...</label>
      <br />
      <div class="mt-8">
        <input
          type="radio"
          name="gender"
          id="gender"
          value="female"
          class="form-radio text-green-500"
          @change="onChange"
        />
        <label class="text-lg font-bold ml-3">Female</label>
      </div>
      <div>
        <input
          type="radio"
          name="gender"
          id="gender"
          value="male"
          @change="onChange"
          class="
            text-2xl
            p-2
            border-2
            rounded
            form-radio
            text-green-500
            mt-4
            mb-4
          "
        />
        <label class="text-lg font-bold ml-3">Male</label>
      </div>
      <div>
        <input
          type="radio"
          name="gender"
          id="gender"
          value="others"
          @change="onChange"
          class="
            text-2xl
            p-2
            border-2
            rounded
            form-radio
            text-green-500
            mt-4
            mb-4
          "
        />
        <label class="text-lg font-bold ml-3">Others</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "About",
  props:{
      formValue:{
          address: String,
          gender: String,
      }
  },
  methods:{
    onChange(e){
        this.$emit('formValueChange', {
            label:'about',
            data:{
                ...this.formValue,
                [e.target.name]:e.target.value
            }
        })
    }
  },
  emits:['formValueChange']
};
</script>

