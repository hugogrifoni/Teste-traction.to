<script setup>
import NotFavoriteIcon from './icons/IconNotFavorite.vue';
import FavoriteIcon from './icons/IconFavorite.vue';
import MessageItem from './MessageItem.vue';
</script>

<script>
export default {
	data() {
		return {
			posts: [],
			name: '',
			message: '',
		};
	},
	methods: {
		addPost() {
			if (this.message.trim() === '') {
				return;
			}
			this.posts.push({
				name: this.name,
				message: this.message,
				isFavorite: false,
			});
			this.message = '';
		},
		toggleFavoritePost(index) {
			this.posts[index].isFavorite = !this.posts[index].isFavorite;
		},
	},
};
</script>

<template>
	<div
		class="flex flex-col items-center bg-slate-700 text-white pb-10 min-h-screen bg-[url('../assets/image-bg.png')]"
	>
		<div class="my-8">
			<img src="../assets/logo.png" />
		</div>
		<hr />
		<h2 class="py-5 text-3xl font-bold mt-5">Social Feed</h2>

		<div class="flex flex-col w-2/3 rounded-xl bg-neutral-900">
			<div class="p-3">
				<textarea
					class="text-white resize-none h-28 w-full mb-0 p-2 bg-neutral-900"
					placeholder="Insira sua mensagem..."
					type="text"
					name="author"
					v-model="message"
				/>
			</div>
			<div class="w-full border-t border-gray-700" />
			<div class="ml-auto p-4">
				<button
					class="w-36 text-center rounded-lg py-1 border-lime-600 bg-lime-600 text-white"
					v-on:click="addPost"
					type="submit"
				>
					Postar
				</button>
			</div>
		</div>

		<h2 class="text-3xl font-bold mt-10">Últimos posts</h2>

		<div class="w-2/3 mt-5 text-gray-400">
			<div v-for="(comment, index) in posts">
				<MessageItem
					:index="index"
					:msg="comment"
					:toggle-favorite-post="toggleFavoritePost"
				/>
			</div>
		</div>

		<hr />
	</div>
</template>
