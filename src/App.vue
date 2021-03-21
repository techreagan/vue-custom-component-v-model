<template>
	<div class="container">
		<button class="btn" @click="openDialog">Open Modal</button>
	</div>

	<teleport to="body">
		<base-modal v-model="dialog"> </base-modal>
	</teleport>
</template>

<script>
import BaseModal from '@/components/UI/BaseModal'
export default {
	data() {
		return {
			dialog: false,
		}
	},
	methods: {
		openDialog() {
			this.dialog = true
		},
	},
	components: {
		BaseModal,
	},
}
</script>

<style>
* {
	padding: 0;
	margin: 0;
}

body {
	color: white;
	background: #101024;
	font-family: 'Poppins', sans-serif;
}

.container {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100vh;
}

.btn {
	border: none;
	background-color: #f3bc17;
	color: #101024;
	padding: 0.5rem 1.8rem;
	cursor: pointer;
	outline: none;
	font-size: 0.8rem;
}
</style>
