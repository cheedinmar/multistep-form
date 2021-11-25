<template>
  <p class="text-5xl font-bold mb-9 text-center">Tell Us About Yourself</p>
  <div class="shadow-lg p-10 rounded">
    <div>
      <label for="name" class="font-bold text-2xl"> Where do you live?</label>
      <br />
      <textarea
        name="address"
        id="address"
        class="w-full text-2xl p-2 border-2 rounded border-green-500 mt-4 mb-4"
      />
    </div>

    <div>
      <label for="name" class="font-bold text-2xl">Are you a ...</label>
      <br />
      <div>
        <input
          type="radio"
          name="gender"
          id="gender"
          value="female"
          class="form-radio text-green-500"
        />
        <label>Female</label>
      </div>
      <div>
        <input
          type="radio"
          name="gender"
          id="gender"
          value="male"
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
        <label>Male</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "About",
};
</script>

