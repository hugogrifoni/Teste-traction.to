<script setup>
import NotFavoriteIcon from './icons/IconNotFavorite.vue';
import FavoriteIcon from './icons/IconFavorite.vue';
</script>

<script>
export default {
	props: ['msg', 'index', 'toggleFavoritePost'],
};
</script>

<template>
	<div class="flex mt-5 mb-2">
		<div>
			<img src="../assets/Avatar.png" />
		</div>
		<div class="w-full ml-4">
			<div class="box-border bg-neutral-900 mb-2 py-5 px-2.5 rounded-lg">
				<p>{{ msg.message }}</p>
			</div>
			<div class="ml-auto flex justify-end">
				<a
					href="#"
					title="favoritar"
					v-on:click="toggleFavoritePost(index)"
				>
					<div
						class="flex items-center bg-neutral-900 px-4 py-1 rounded-md"
						v-if="msg.isFavorite"
					>
						<span>Favorito</span>
						<FavoriteIcon class="mt-auto ml-2" />
					</div>
					<div
						class="flex items-center bg-neutral-900 px-4 py-1 rounded-md"
						v-else
					>
						<span>Favoritar</span>
						<NotFavoriteIcon class="mt-auto ml-2" />
					</div>
				</a>
			</div>
		</div>
	</div>
</template>