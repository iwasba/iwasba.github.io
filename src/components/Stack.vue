<template>
  <v-row
    class="stack px-12 "
    :style="
      $vuetify.theme.dark
        ? { backgroundColor: '#596B7D ' }
        : { backgroundColor: '#6c86a1' }
    "
  >
    <v-col class="hidden-sm-and-down " cols="1" />
    <v-col class="fadeIn" :class="{ fillWidth: $vuetify.breakpoint.smAndDown }">
      <div class="leftAlign">
        <h2 :style="{ color: 'white !important' }">Tech Stack</h2>
        <slot name="description"></slot>
      </div>
    </v-col>
    <v-col sm="12" md="6" class="centered" max-width="420">
      <v-row>
        <v-col class="centered" v-for="tool in stack" :key="tool">
          <img
            class="fadeLeft"
            :style="
              imgSize
                ? {
                    height: $vuetify.breakpoint.smAndDown
                      ? `${imgSize * 1.5}vw`
                      : `${imgSize}vw`
                  }
                : { height: $vuetify.breakpoint.smAndDown ? '14vw' : '7vw' }
            "
            :src="require(`@/assets/icons/${tool}.png`)"
          />
        </v-col>
      </v-row>
    </v-col>
    <v-col class="hidden-sm-and-down" cols="1" />
  </v-row>
</template>

<script>
export default {
  name: "Stack",
  props: {
    description: String,
    stack: Array,
    name: String,
    imgSize: Number || null
  }
};
</script>

<style scoped>
.fadeLeft {
  opacity: 0;
  animation: fade-in-left 1.5s;
  animation-delay: 2s;
  animation-fill-mode: both;
}
.fillWidth {
  min-width: 100%;
}
.stack {
  padding-top: 90px;
  padding-bottom: 90px;
}
.leftAlign {
  text-align: left;
}
</style>
