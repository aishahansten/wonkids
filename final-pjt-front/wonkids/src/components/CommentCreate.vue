<template>
  <form @submit.prevent="createComment">
    <label for="content" style="margin-right: 10px;">내용 : </label>
    <input type="text" name="content" id="content" v-model="content" style="margin-right: 10px;">
    <button>댓글 작성</button>
  </form>
</template>

<script setup>
import { useCommentStore } from '@/stores/comments.js'
import { ref } from 'vue';
const store = useCommentStore()
const props = defineProps({
  articlePk: Number
})
const content = ref('')
const createComment = function () {
  store.commentCreate(props.articlePk, content.value)
  content.value = ''
}
</script>

<style scoped>

</style>