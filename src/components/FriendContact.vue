<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Vissible)' : '' }}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? 'Hide Details' : 'Show Details' }}
    </button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong>{{ phoneNumber }}</li>
      <li><strong>Email:</strong>{{ emailAddress }}</li>
    </ul>
    <button @click="$emit('delete-friend', id)">Delete</button>
  </li>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },

    isFavorite: {
      type: String,
      required: true,
    },
  },
  emits: ['toggle-favorite', 'delete-friend'],
  data() {
    return {
      detailsAreVisible: false,
    }
  },

  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible
    },

    toggleFavorite() {
      this.$emit('toggle-favorite', this.id)
    },
  },
}
</script>
