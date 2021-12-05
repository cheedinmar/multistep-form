<template>
  <p class="text-5xl font-bold mb-9 text-center">Customize your Profile</p>
  <div class="shadow-lg p-10 rounded">
    <div>
      <label for="fileUploader" class="font-bold text-2xl"
        >Upload your Profile Picture
      </label>
      <input @change="uploadFile"  type="file" name="fileUploader" id="fileUploader" ref="fileUploader" class="hidden" />
      <div
        class="
          cursor-pointer
          flex
          justify-center
          items-center
          flex-col
          border-green-500 border-2
          w-full
          h-72
          mt-4
          rounded-lg
          hover:shadow-lg
          mb-4
        "
        @click="$refs.fileUploader.click()"
      >
      <img :src="formValue.profilePicture" class="h-40 w-40 rounded mb-4" v-if="formValue.profilePicture"/>
        <img v-else src="../../assets/upload.png" class="w-8 h-8" />
        <p>Click Here to upload</p>
      </div>
    </div>
    <div>
      <label for="bio" class="font-bold text-2xl">Describe yourself </label>
      <br />
      <textarea
        @input="onChange"
        name="bio"
        v-model="formValue.bio"
        id="bio"
        class="w-full text-2xl p-2 border-2 rounded border-green-500 mt-4 mb-4"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Profile ",
  props: {
    formValue: {
      profilePicture: String,
      bio: String,
    },
  },
  methods: {
    onChange(e) {
      this.$emit("formValueChange", {
        label: "profile",
        data: {
          ...this.formValue,
          [e.target.name]: e.target.value,
        },
      });
    },
    uploadFile(e){
      const file = e.target.files[0];
      if(!file){
        return;
      }
      const fileReader = new FileReader()
       fileReader.onload = ()=>{
         this.$emit("formValueChange", {
        label: "profile",
        data: {
          ...this.formValue,
         profilePicture: fileReader.result,
        },
      });
       }
       fileReader.readAsDataURL(file)
    }
  },
  emits: ["formValueChange"],
};
</script>

<style>
</style>