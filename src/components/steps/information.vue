<template>
  <p class="text-5xl font-bold mb-9 text-center">General Information</p>
    <div class="shadow-lg p-10 rounded ">
        <div>
            <label for="name" class="font-bold text-2xl"> Your good name?</label>
            <br />
            <input
            @input="onChange"
            type="text"
            name="name"
            id="name"
            v-model="formValue.name"
            class="text-2xl p-2 border-2 rounded border-green-500 mt-4 mb-4"
            />
        </div>
        <div>
            <label for="dob" class="font-bold text-2xl"> When were you born ?</label>
            <br />
            <input
            @input="onChange"
            type="date"
            name="dob"
            id="dob"
             v-model="formValue.dob"
            class="text-2xl p-2 border-2 rounded border-green-500 mt-4 mb-4"
            />
        </div>
        <div>
            <label for="age" class="font-bold text-2xl">How old are you</label>
            <br />
            <input
            @input="onChange"
            type="number"
            name="age"
            id="age"
             v-model="formValue.age"
            class="text-2xl p-2 border-2 rounded border-green-500 mt-4 mb-4"
            />
        </div>
        <div>
            <label for="name" class="font-bold text-2xl">Enter Email</label>
            <br />
            <input
            @input="onChange"
            type="text"
            name="email"
            id="email"
             v-model="formValue.email"
            class="text-2xl p-2 border-2 rounded border-green-500 mt-4 mb-4"
            />
        </div>
    </div>
</template>

<script>
export default {
  name: "Information ",
  props:{
      formValue:{
          email: String,
          name: String,
          dob: String,
          age:Number
      }
  },
  methods:{
      onChange(e){
          this.$emit('formValueChange', {
              label:'information',
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

<style>
</style>