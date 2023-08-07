<script setup>
// defineProps is a Vue 3 function that allows us to define props in the setup function.
// props are variables that are passed to us from a parent component.
const props = defineProps({
  author: {
    type: String,
    required: true
  },
  date: {
    type: String,
    required: true
  },
  color: {
    type: String,
    default: 'info'
  }
})
// computed is a Vue 3 function that allows us to define computed properties in the setup function.
const formattedDate = computed(() => {
  return new Date(props.date).toDateString()
})
</script>

<template>
  <!--
    This template is used in pages/blog/[...slug].vue and components/BlogPostList.vue.
  -->
  <div class="tags has-addons level-item are-medium">
    <span class="tag is-rounded" :class="`is-${color}`">{{ author }}</span>
    <span class="tag is-rounded">{{ formattedDate }}</span>
  </div>
</template>

<style></style>
