<template>
  <v-container fluid class="experience py-12 px-4">
    <v-timeline align-top dark :dense="$vuetify.breakpoint.mdAndDown">
      <v-timeline-item
        data-aos="fade-in"
        v-for="(item, index) in data"
        :key="index"
        color="white"
        small
      >
        <template v-slot:opposite v-if="!!item.image">
          <img :src="item.image" style="max-height: 5rem" data-aos="zoom-in" />
        </template>
        <v-container fluid class="text-left" data-aos="zoom-in">
          <v-row class="d-flex flex-xs-wrap flex-lg-nowrap align-center">
            <v-col
              class="text-h4 font-weight-normal place--text"
              @click="redirect(item.link)($event)"
              v-text="item.title"
            ></v-col>

            <v-col
              class="text-overline font-weight-thin"
              v-text="item.position"
              data-aos="zoom-in"
              data-aos-delay="300"
            ></v-col>
          </v-row>

          <v-row>
            <v-col
              class="text-subtitle mb-4 my-0"
              v-if="!!item.subtitle"
              v-text="item.subtitle"
              cols="12"
            ></v-col>

            <v-col
              class="text-body-2 font-weight-light mb-4"
              v-text="item.description"
              cols="12"
            ></v-col>

            <v-col
              class="text-overline mb-4"
              cols="12"
              v-html="item.time"
            ></v-col>
          </v-row>
        </v-container>
      </v-timeline-item>
    </v-timeline>
  </v-container>
</template>

<script>
export default {
  name: "Experience",
  props: ["data"],
  methods: {
    redirect: (link) => () => {
      window.open(link, "_blank").focus();
    },
  },
};
</script>

<style lang="scss" scoped>
.place--text {
  cursor: pointer;
  width: initial;
}
</style>