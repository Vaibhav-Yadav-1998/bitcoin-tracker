<template>
    <div id="time">
      Last Updated : {{time}}
    </div>
</template>

<script>
export default {
  name: "Time",
  props: {
    time: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
#time {
  text-align: center;
  font-weight: 600;
}
</style>
