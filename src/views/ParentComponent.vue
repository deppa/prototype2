<template>
  <div>
    <h1>{{ state.message }}</h1>
    <ChildComponent
      :message="state.message"
      @change-message="changeMessage"
    ></ChildComponent>
  </div>
</template>

<script lang="ts">
import ChildComponent from "@/views/ChildComponent.vue";
import { defineComponent, reactive } from "vue";

export default defineComponent({
  components: {
    ChildComponent
  },
  setup() {
    const state = reactive({
      message: "Hello Kensuke Ota"
    });

    const changeMessage = (message: string) => {
      state.message = message;
    };

    return {
      state,
      changeMessage
    };
  }
});
</script>