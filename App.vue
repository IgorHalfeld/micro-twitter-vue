<template>
	<main class="main">
		<Header />

		<section class="content">
			<div class="widget">
        <div class="container-tweet">
          <div class="container-tweet-avatar"></div>
          <div class="container-tweet-content">
            <textarea
							ref="tweetElement"
							v-model="tweet"
							@keyup.enter="addTweet"
							class="input container-tweet-textarea"
							placeholder="Some thoughts here">
						</textarea>
            <button
							@click="addTweet"
							class="button container-tweet-button"
							:disabled="!tweet">Tweet</button>
          </div>
        </div>
      </div>

			<transition-group name="fade">
				<Widget
					v-for="(item, index) in tweets"
					:key="index"
					:tweet="item.tweet"
				/>
			</transition-group>
		</section>
	</main>
</template>

<script>
import Header from './components/Header';
import Widget from './components/Widget';

export default {
	name: 'App',
	components: { Header, Widget },
	data: () => ({
		tweet: '',
		tweets: [
			{ tweet: 'Vue.js São Paulo Meetup @vuejssp' },
		],
	}),
	computed: {
		buttonIsDisabled() {
			return !(this.tweet && this.tweet.length);
		},
	},
	methods: {
		addTweet() {
			const { tweet } = this;
			this.tweets.unshift({ tweet });
			this.tweet = '';
			this.$refs.tweetElement.focus();
		},
	},
};
</script>

<style src="./style.css"></style>
