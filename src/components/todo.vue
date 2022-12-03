<template>
    <v-navigation-drawer
      v-model="drawer"
      absolute
      color="grey-lighten-3"
      rail
    >
      <v-avatar
        class="d-block text-center mx-auto mt-4"
        color="grey-darken-1"
        size="36"
      >
      </v-avatar>

      <v-divider class="mx-3 my-5"></v-divider>

      <v-avatar
        v-for="n in 6"
        :key="n"
        class="d-block text-center mx-auto mb-9"
        color="grey-lighten-1"
        size="28"
      ></v-avatar>
    </v-navigation-drawer>

    <v-navigation-drawer
      v-model="drawer"
      width="300"
    >
      <v-sheet
        color="grey-lighten-5"
        height="128"
        width="100%"
      ></v-sheet>

      <v-list
        class="pl-14"
        shaped
      >
        <v-list-item
          v-for="n in 5"
          :key="n"
          link
        >
          <v-list-item-content>
            <v-list-item-title>Item {{ n }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      flat
      height="72"
      class="px-3"
      color="grey-lighten-4"
    >
      <v-spacer></v-spacer>

      <v-responsive max-width="156">
        <v-text-field
          density="compact"
          hide-details
          rounded
        ></v-text-field>
      </v-responsive>
    </v-app-bar>

    <v-main>
      <!--  -->
    </v-main>

    <v-navigation-drawer location="right">
      <v-list>
        <v-list-item
          v-for="n in 5"
          :key="n"
          link
        >
          <v-list-item-content>
            <v-list-item-title>Item {{ n }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-footer
      app
      color="transparent"
      height="72"
      inset
    >
      <v-text-field
        bg-color="grey lighten-1"
        density="compact"
        flat
        hide-details
        rounded
        variant="solo"
      ></v-text-field>
    </v-footer>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

//Dataオブジェクト
export type DataType = {
  text: string;
  theme :string ;
};
//Dataオブジェクト
export type move = {
  x: number;
  y: number;
};
export type resize = {
  height: number;
  width: number;
};

export default defineComponent({
  name: 'App',
  components: {},
  data(): DataType {
    return {
      //nameの初期化
      text: '',
      theme: 'dark'
    };
  },
  computed: {

  },
  methods: {
    toggleTheme() {
      this.theme = (this.theme === 'light' ?  'dark' : 'light')
    },
    async WindowAPI() {
      await appWindow.center();
      await appWindow.maximize();
      await appWindow.setFocus();
    }
  },
  watch: {},
  created(){
    console.log("Start!!")
    this.WindowAPI();
  }
});

</script>
<style scoped>
</style>

