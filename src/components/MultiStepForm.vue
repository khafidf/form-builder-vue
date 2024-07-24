<script setup lang="ts">
import { ref } from "vue";
import StepOne from "./StepOne.vue";
import StepTwo from "./StepTwo.vue";

const formData = ref({
	name: "",
	gender: "",
	description: "",
	title: "",
});

const personalInformation = ref("");

const step = ref(1);

const nextStep = () => {
	step.value++;
	personalInformation.value = "";
};

const backForm = () => {
	step.value--;
};

const submitForm = () => {
	console.log("Form submitted", formData.value);
	personalInformation.value = `I'm ${formData.value.title}${formData.value.name}, I'm ${formData.value.gender} and this is my description ${formData.value.description}`;
	formData.value = {
		name: "",
		gender: "",
		description: "",
		title: "",
	};
	step.value--;
};
</script>

<template>
	<div>
		<div v-if="step === 1">
			<StepOne
				:formData="formData"
				:nextStep="nextStep"
				:personalInformation="personalInformation"
			/>
		</div>
		<div v-if="step === 2">
			<StepTwo
				:formData="formData"
				:submitForm="submitForm"
				:backForm="backForm"
			/>
		</div>
	</div>
</template>
