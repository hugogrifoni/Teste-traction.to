<script setup>
import NotFavoriteIcon from './icons/IconNotFavorite.vue';
import FavoriteIcon from './icons/IconFavorite.vue';
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
			if (this.name.trim() === '' || this.message.trim() === '') {
				return;
			}
			this.posts.push({
				name: this.name,
				message: this.message,
				isFavorite: false,
			});
			this.name = '';
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
		class="flex flex-col items-center bg-slate-700 text-white h-screen bg-[url('../assets/image-bg.png')]"
	>
		<div class="my-8">
			<img src="../assets/logo.png" />
		</div>
		<hr />
		<h2 class="py-5">Social Feed</h2>

		<div class="w-2/3">
			<div>
				<input
					class="text-black w-full mb-2 p-2 rounded-lg"
					placeholder="Nome"
					type="text"
					name="author"
					v-model="name"
				/>
			</div>
			<div>
				<textarea
					class="text-black w-full mb-2 p-2 rounded-lg"
					placeholder="Insira sua mensagem..."
					type="text"
					name="author"
					v-model="message"
				/>
			</div>
			<div
				class="box-border border-2 border-lime-600 rounded-lg w-14 text-center content-end bg-lime-600 text-white"
			>
				<button
					class="btn btn-primary"
					v-on:click="addPost"
					type="submit"
				>
					post
				</button>
			</div>
		</div>

		<div class="w-2/3 py-12 text-gray-400">
			<div
				class="box-border border-2 my-5 py-5 px-2.5 rounded-lg"
				v-for="(comment, index) in posts"
			>
				<span class="postAuthor"
					>Autor: <strong>{{ comment.name }}</strong></span
				>
				<p>{{ comment.message }}</p>

				<a
					href="#"
					title="favoritar"
					v-on:click="toggleFavoritePost(index)"
				>
					<div class="flex items-center" v-if="!comment.isFavorite">
						<FavoriteIcon /> Desfavoritar
					</div>
					<div class="flex" v-else><NotFavoriteIcon /> Favoritar</div>
				</a>
			</div>
		</div>

		<hr />
	</div>
</template>
