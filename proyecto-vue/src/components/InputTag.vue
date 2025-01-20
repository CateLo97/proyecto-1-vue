<script setup>
import { ref } from 'vue';

const tags = ref(['Tags']);
const currentValue = ref('');


//metodo para añadir un nuevo tag

const handleKeyDown = (e)=>{
    if(e.key==='Enter' && currentValue.value.trim() !== ''){
        tags.value.push(currentValue.value);
        currentValue.value= '';
    }
};

//metodo para eliminar un tag

const deleteTag = (tag) => {
    tags.value = tags.value.filter( item => item !== tag)
};

</script>

<template>
    <div class="inputTag">
        <div class="tags">
            <div class="tag" v-for="(tag, index) in tags" :key="index">
                {{ tag }} <button @click="deleteTag(tag)">❗❌</button>
            </div>
        </div>
        <input type="text" v-model="currentValue" @keydown="handleKeyDown" />
    </div>
</template>

<style scoped>

</style>
