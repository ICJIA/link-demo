<template>
  <div>
    <v-container class="mt-12"
      ><v-row fill-height
        ><v-col>
          <v-sheet class="mx-auto">
            <v-form>
              <v-text-field
                v-model="link"
                label="Link"
                style="font-weight: 900"
              ></v-text-field>
              <div class="text-center">
                <v-btn class="mt-2 mr-5" text="encode" @click="encode"></v-btn>
                <v-btn class="mt-2 mr-5" text="decode" @click="decode"></v-btn>
                <v-btn
                  class="mt-2 mr-5"
                  text="goto URL"
                  @click="gotoURL"
                ></v-btn>
              </div>
            </v-form>
          </v-sheet>
          <div class="mt-16">
            <a :href="link" target="_blank">{{ link }}</a>
          </div></v-col
        ></v-row
      ></v-container
    >
  </div>
</template>

<script setup>
let link = ref(
  "https://researchhub.icjia-api.cloud/uploads/housing options for probationers FINAL PDF-231024T20415515.pdf"
);

const encode = () => {
  link.value = encodeURI(link.value);
};
const decode = () => {
  link.value = decodeURI(link.value);
};

const gotoURL = () => {
  window.open(link.value, "_blank");
};
</script>

<style lang="scss" scoped></style>
