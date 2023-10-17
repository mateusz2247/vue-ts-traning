<template>
	<div>
		<h1>My todo</h1>
		<h3>{{ completedAll }}</h3>
	</div>
	<ItemList :Items="DataItemsList" @changeItem="CompletedItem"></ItemList>
</template>

<script setup lang="ts">
import ItemList from "./components/Items/Items-component.vue";
import { reactive, computed } from "vue";
import type { ItemInterface } from "./models/Items/Item.interface";
const DataItemsList: ItemInterface[] = reactive([
	{
		id: 1,
		name: "coffe",
		completed: false,
	},
	{
		id: 2,
		name: "books",
		completed: false,
	},
]);

const CompletedItem = (id: number) => {
	alert("id" + id);
};

const completedAll = computed(() => {
	let all = DataItemsList.length;
	let countCompleted = 0;

	DataItemsList.forEach((element) => {
		if (element.completed) {
			countCompleted++;
		}
	});
	return countCompleted == all ? "All task is completed" : "No";
});
</script>

<style></style>
