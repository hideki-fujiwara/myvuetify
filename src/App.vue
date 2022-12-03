<template>
  <v-app :theme="theme">
    <v-system-bar height="42">
      <v-spacer></v-spacer>
      <v-icon>mdi-square</v-icon>
      <v-icon>mdi-circle</v-icon>
      <v-btn
        @click="toggleTheme"
        variant="plain"
        prepend-icon="mdi-theme-light-dark"
        color="primary"
      />
    </v-system-bar>
    <v-main>
      <todo />
    </v-main>
    <!-- <v-footer>
      <div class="px-4 py-2 bg-black text-center w-100">
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </div>
    </v-footer> -->
  </v-app>
</template>

<script setup lang="ts">
import { defineComponent } from 'vue';
import { appWindow } from '@tauri-apps/api/window';
import todo from '@/components/todo.vue';

const theme = ref('light');
function toggleTheme() {
  theme.value = theme.value === 'light' ? 'dark' : 'light';
}

onBeforeMount(() => {});
</script>

<script lang="ts">
//WindowStyleオブジェクト
export type WindowStyle = {
  theme: string;
  height: number;
  width: number;
  isMaximize: boolean;
  point: { x: number; y: number };
};
export default defineComponent({
  name: 'App',
  components: {},
  data(): WindowStyle {
    return {
      theme: 'dark',
      height: 1920,
      width: 1080,
      isMaximize: true,
      point: { x: 0, y: 0 },
    };
  },
  computed: {},
  methods: {
    toggleTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light';
    },
    async WindowAPI() {
      await appWindow.center();
      await appWindow.maximize();
      await appWindow.setFocus();
    },
  },
  watch: {},
  created() {
    this.WindowAPI();
  },
});
</script>
