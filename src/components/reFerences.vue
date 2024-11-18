<script setup>
import { ref } from 'vue'

// 可選的標籤列表
const categories = ref([
    'CSS Changes', 'Animations', 'Testing', 'CI/CD', 'Data Layers',
    'LLM Models', 'Design Systems', 'CSS Tokens', 'API Integrations', 'UI Components'
])

// 儲存選中的標籤
const selectedTags = ref(['API Integrations', 'UI Components'])

// 新增標籤到選中列表
const addTag = (tag) => {
    if (!selectedTags.value.includes(tag)) {
        selectedTags.value.push(tag)
        console.log(tag);

    }
}

// 從選中列表中移除標籤
const removeTag = (tag) => {
    selectedTags.value = selectedTags.value.filter(item => item !== tag)
    console.log(tag);

}
</script>

<template>
    <div class="tag-selector">
        <!-- 選中標籤的區域 -->
        <div class="selected-tags">
            <span v-for="tag in selectedTags" :key="tag" class="tag selected" @click="removeTag(tag)">
                {{ tag }} x
            </span>
        </div>
        <p>Pick up the categories that best describe you</p>

        <!-- 可選標籤的區域 -->
        <div class="available-tags">
            <span v-for="category in categories" :key="category" class="tag available" @click="addTag(category)">
                {{ category }} +
            </span>
        </div>
    </div>
</template>

<style scoped>
.tag-selector {
    border: 1px solid #e0e0e0;
    padding: 16px;
    border-radius: 8px;
    width: 300px;
}

.selected-tags,
.available-tags {
    margin-top: 8px;
}

.tag {
    display: inline-flex;
    align-items: center;
    margin: 4px;
    padding: 4px 8px;
    background-color: #f1f1f1;
    border-radius: 16px;
    cursor: pointer;
    color: #000000;
}

.selected:hover {
    background-color: #e6e6e6;
}

.available:hover {
    background-color: #d9d9d9;
}

button {
    margin-left: 4px;
    background: none;
    border: none;
    cursor: pointer;
    color: #000000;
}
</style>
