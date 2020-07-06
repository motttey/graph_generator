<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <div class="text-center">
        <logo />
        <vuetify-logo />
        <file-upload />
      </div>

    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue';
import VuetifyLogo from '~/components/VuetifyLogo.vue';
import FileUpload from '~/components/FileUpload.vue';
import Barchart from '~/components/Barchart.vue';

import * as d3 from "d3";

export default {
  components: {
    Logo,
    VuetifyLogo,
    FileUpload
  },
}
</script>
