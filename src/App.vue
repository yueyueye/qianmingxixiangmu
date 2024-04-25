<script setup lang="ts">
import Downloader from "./components/Downloader.vue";
import { reactive, ref } from "vue";

const globalData = reactive({
  value:
    "http://shipin.cdxyhpx.com/sv/3bba3a21-18926843f74/3bba3a21-18926843f74.mp4",
});
const setGlobalData = (obj: any) => {
  globalData.value = obj.value;
};

const url = ref("https://zion-app.functorz.com/zero/JmAxbl1kYqo/api/graphql-v2");
const actionflow_id = ref("5e5e155d-7b3c-4771-bf94-ceb597cbb666");
</script>

<template>
  <Downloader
    source="http://shipin.cdxyhpx.com/sv/3bba3a21-18926843f74/3bba3a21-18926843f74.mp4"
    vid="a175d6b01b4271ee80980764b3ec0102"
    playauth=""
    :url="url"
    :actionflow_id="actionflow_id"
    :global-data="globalData"
    :set-global-data="setGlobalData"
    :course_log_pk="0"
  />
</template>

<style>
#app {
  height: 100vh;
}
</style>
