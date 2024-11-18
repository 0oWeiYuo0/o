<script setup>
import { ref, computed } from "vue";

const allTags = ref([
  '策略', '燒腦', '派對', '邏輯', '背叛', '合作', '佔領'
])

const selectedTags = ref(['策略'])

const noSelectedTags = computed(() => {
  return allTags.value.filter(tag => !selectedTags.value.includes(tag))

})

const addTag = (tag) => {
  if (!selectedTags.value.includes(tag)) {
    selectedTags.value.push(tag)
  }
}

const removeTag = (tag) => {
  selectedTags.value = selectedTags.value.filter(item => item !== tag)
}

console.log(!selectedTags.value);


</script>

<template>
  <div class="tag-selector">
    <div class="selected-tags">
      <span v-for="tags in selectedTags" :key="tags" class="tag selected" @click="removeTag(tags)">
        {{ tags }} x
      </span>
    </div>

    <p>點擊新增標籤</p>
    <div class="available-tags">
      <span v-for="tags in noSelectedTags" :key="tags" class="tag available" @click="addTag(tags)">
        {{ tags }} +
      </span>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>