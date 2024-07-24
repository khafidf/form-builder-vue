<script setup lang="ts">
import { defineProps } from "vue";

const props = defineProps<{
	formData: { description: string; title: string };
	submitForm: () => void;
	backForm: () => void;
}>();

const titleOptions = ["Mr.", "Mrs.", "Ms.", "Dr.", "Prof."];
</script>

<style>
div {
	padding: 10px;
	display: flex;
	flex-direction: column;
}
button {
	margin-left: 5px;
}
</style>

<template>
	<div>
		<h2>Additional Information</h2>
		<p>Please provide additional details</p>
		<form @submit.prevent="props.submitForm">
			<div>
				<label for="description">Description</label>
				<textarea
					v-model="props.formData.description"
					id="description"
					placeholder="Enter a description"
				></textarea>
			</div>
			<div>
				<label for="title">Title</label>
				<select v-model="props.formData.title" id="title">
					<option disabled value="">Enter a title</option>
					<option v-for="option in titleOptions" :key="option" :value="option">
						{{ option }}
					</option>
				</select>
			</div>
			<button @click="props.backForm">Back</button>
			<button type="submit">Submit</button>
		</form>
	</div>
</template>
