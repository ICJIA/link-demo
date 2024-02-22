<template>
  <div>
    <v-container class="mt-12"
      ><v-row fill-height
        ><v-col>
          <v-card class="mx-auto px-10 py-10" elevation="5">
            <v-form>
              <v-text-field
                v-model="link"
                label="Link"
                style="font-weight: 900"
                @keyup="clearMessages"
              ></v-text-field>
              <div class="text-center">
                <v-btn class="mt-2 mr-5" text="encode" @click="encode"></v-btn>
                <v-btn class="mt-2 mr-5" text="decode" @click="decode"></v-btn>
                <v-btn
                  class="mt-2 mr-5"
                  text="copy to clipboard"
                  @click="copyToClipboard"
                ></v-btn>

                <v-btn
                  class="mt-2 mr-5"
                  text="goto URL"
                  @click="gotoURL"
                ></v-btn>
                <v-btn class="mt-2 mr-5" text="clear" @click="clearAll"></v-btn>
              </div>
            </v-form>
            <!-- <v-snackbar v-model="isCopied" top>
              Copied to clipboard

              <template v-slot:actions>
                <v-btn color="blue" variant="text" @click="isCopied = false">
                  Close
                </v-btn>
              </template>
            </v-snackbar> -->
            <div v-if="isCopied" class="mt-16 mx-auto text-center">
              Copied to clipboard!
            </div>
          </v-card>
          <!-- <div class="mt-16">
            <a :href="link" target="_blank">{{ link }}</a>
          </div> -->
        </v-col></v-row
      ></v-container
    >
    <v-container class="mt-12"
      ><v-row
        ><v-col>
          <v-card class="px-5 py-5" style="background: #fafafa" elevation="5">
            <h2 class="mb-5">References:</h2>
            <ul class="pl-10">
              <li>
                <a href="https://www.ietf.org/rfc/rfc3986.txt" target="_blank">
                  Uniform Resource Identifier (URI): Generic Syntax (Network
                  Working Group RFC 3986)
                </a>
              </li>
              <li>
                <a
                  href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI"
                  target="_blank"
                  >encodeURI() (MDN - Mozilla)</a
                >
              </li>
              <li>
                <a href="https://github.com/ICJIA/link-demo" target="_blank"
                  >Github repo for this page</a
                >
              </li>
            </ul>
            <h3 class="mt-10 mb-5">Additional Info:</h3>
            <ul class="pl-10">
              <li>
                <a
                  href="https://en.wikipedia.org/wiki/Percent-encoding"
                  target="_blank"
                  >Percent Encoding</a
                >
              </li>
              <li>
                <a
                  href="https://en.wikipedia.org/wiki/Uniform_Resource_Identifier"
                  target="_blank"
                  >Uniform Resource Identifier</a
                >
              </li>
            </ul>
          </v-card>
        </v-col></v-row
      ></v-container
    >
  </div>
</template>

<script setup>
let isCopied = ref(false);
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

const copyToClipboard = () => {
  isCopied.value = true;
  navigator.clipboard.writeText(link.value);
};

const clearMessages = () => {
  isCopied.value = false;
  // link.value = "";
};

const clearAll = () => {
  isCopied.value = false;
  link.value = "";
};
</script>

<style lang="scss" scoped></style>
