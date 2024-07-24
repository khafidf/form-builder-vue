<script setup lang="ts">
import { defineProps } from "vue";

const props = defineProps<{
	formData: { name: string; gender: string };
	nextStep: () => void;
	personalInformation: string;
}>();
</script>

<style>
div {
	padding: 10px;
	display: flex;
	flex-direction: column;
}
</style>

<template>
	<div>
		<h2>Personal Information</h2>
		<p>
			{{
				personalInformation
					? personalInformation
					: "Please fill out your personal information"
			}}
		</p>
		<form @submit.prevent="props.nextStep">
			<div>
				<label for="name">Name</label>
				<input
					v-model="props.formData.name"
					type="text"
					id="name"
					placeholder="Enter your name"
					required
				/>
			</div>
			<div>
				<label>Gender</label>
				<div>
					<label
						><input v-model="props.formData.gender" type="radio" value="male" />
						Male</label
					>
					<label
						><input
							v-model="props.formData.gender"
							type="radio"
							value="female"
						/>
						Female</label
					>
					<label
						><input
							v-model="props.formData.gender"
							type="radio"
							value="other"
						/>
						Other</label
					>
				</div>
			</div>
			<button type="submit">Next</button>
		</form>
	</div>
</template>
