<template>
    <div>Item list</div>
    <ul v-for="data in Items" :key="data.id">
        <li>
            {{ data.name }} - <input type="checkbox" v-model="data.completed" @click="completedItems(data.id)">
        </li>
    </ul>
</template>

<script setup lang="ts">
import {  defineProps, defineEmits } from 'vue';
import type {ItemInterface} from "../../models/Items/Item.interface"
defineProps<{Items: ItemInterface[]}>();

const emit = defineEmits<{(e:"changeItem", id: number): any}>();


const completedItems = (id: number) =>{
    emit("changeItem",id)
}

</script>