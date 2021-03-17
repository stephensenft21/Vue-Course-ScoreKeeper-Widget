<template>
  <div class="hello">
    <h1>
      <div :class="{ winning: teams[0].winning }">
        {{ teams[0].name }}
      </div>
      vs 
      <div :class="{ winning: teams[1].winning }">
        {{ teams[1].name }}
      </div>
    </h1>
  </div>
</template>

<script>
export default {
  props: {
    teams: [],
  },
};
</script>

<style>
.winning {
  color: goldenrod;
}
</style>
