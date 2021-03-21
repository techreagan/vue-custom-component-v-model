<template>
	<div v-if="modelValue" @click="closeModal" id="overlay"></div>
	<transition name="modal">
		<dialog open v-if="modelValue">
			<slot>
				<header>
					<h2>Delete App</h2>
				</header>
				<div class="content">
					<main>
						<p>Are you sure?</p>
					</main>
					<footer>
						<button @click="closeModal" class="btn btn-danger">Agree</button>
						<button @click="closeModal" class="btn btn-success">
							Disagree
						</button>
					</footer>
				</div>
			</slot>
		</dialog>
	</transition>
</template>

<script>
export default {
	props: {
		modelValue: {
			type: Boolean,
			required: true,
		},
	},
	emits: ['update:modelValue'],
	setup(_, context) {
		function closeModal() {
			context.emit('update:modelValue', false)
		}

		return { closeModal }
	},
}
</script>

<style scoped>
dialog {
	position: fixed;
	top: 20vh;
	margin: auto;
	width: 50%;
	z-index: 100;
	border: none;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
	overflow: hidden;
}

#overlay {
	position: fixed;
	top: 0;
	left: 0;
	height: 100vh;
	width: 100%;
	background-color: rgba(0, 0, 0, 0.5);
	z-index: 10;
}

header {
	background-color: #121227;
	color: white;
	padding: 1rem;
}

.content {
	padding: 1rem;
}

main {
	margin: 1rem 0 3rem;
}

.btn-danger {
	background-color: #ee5b60;
	color: white;
}

.btn-success {
	background-color: #101024;
	color: white;
	margin-left: 10px;
}

/* fatel */
.modal-enter-from,
.modal-leave-to {
	transform: translateY(-20px);
	opacity: 0;
}

.modal-enter-active,
.modal-leave-active {
	transition: 0.3s all ease-in-out;
}

.modal-enter-to,
.modal-leave-from {
	transform: translateY(0px);
	opacity: 1;
}
/* .modal-leave-from {
	transform: translateY(0px);
	opacity: 1;
}

.modal-leave-active {
	transition: 0.3s all ease-in-out;
}

.modal-leave-to {
	transform: translateY(-20px);
	opacity: 0;
} */

@media (max-width: 700px) {
	dialog {
		width: 80%;
	}
}
</style>
