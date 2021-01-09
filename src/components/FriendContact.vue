<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }}</h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavorite">{{ isFavorite ? 'Remove' : 'Add' }} Favorite</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ email }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  name: "FriendContact",
  props: [
    'id',
    'name',
    'phone',
    'email',
    'isFavorite'
  ],
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      /* send custom event from child to parent component */
      this.$emit('toggle-favorite', this.id);
    }
  }
}
</script>

<style scoped>
button {
  margin: 10px;
}
</style>
