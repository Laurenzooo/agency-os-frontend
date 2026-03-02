<script setup lang="ts">
const props = defineProps({
	error: Object,
});

const handleError = () => clearError({ redirect: '/' });
</script>

<template>
	<NuxtLayout name="default">
		<div class="flex flex-col items-center justify-center min-h-[50vh] text-center p-8">
			<h1 class="text-4xl font-bold mb-4">Oops! Something went wrong.</h1>
			<p class="text-lg text-gray-600 mb-8">{{ error?.message || 'An unexpected error occurred.' }}</p>
			<UButton color="black" @click="handleError">Return Home</UButton>
		</div>
	</NuxtLayout>
</template>
