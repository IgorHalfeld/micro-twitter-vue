<template>
  <div class="widget tweet-published">
    <div class="container-tweet">
      <div class="container-tweet-avatar"></div>
      <div class="container-tweet-content">
        <p class="container-tweet-desc">
          {{ tweet }}
        </p>
        <span class="container-tweet-date">
          Published at {{ formatedDate }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Widget',
  props: {
    tweet: { type: String, default: 'Batata' },
    date: { type: String, default: new Date().toISOString() },
  },
  computed: {
    formatedDate() {
      const date = new Date(this.date);
      return `${date.getFullYear()}/${date.getMonth() + 1}/${date.getDate()} ${date.toLocaleTimeString()}`;
    },
  },
};
</script>