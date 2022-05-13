<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
      </v-col>

      <v-col class="mb-4">

        <p v-for="(msg, index) in msgs" :key="index" class="subheading font-weight-regular">
          {{msg}}
        </p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',
    mounted() {
    },
    data: () => ({
    }),
    props: {
      msgs: Array
    }
  }
</script>
