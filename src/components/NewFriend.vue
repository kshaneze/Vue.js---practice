<template>
  <form>
    <input type="text" placeholder="Name" v-model="friendName" />
    <input type="tel" placeholder="Phone" v-model="friendPhone" />
    <input type="email" placeholder="Email" v-model="friendEmail" />
    <button @click.prevent="submitFriendsInformation">Create Friend</button>
  </form>
</template>
<script>
export default {
  emits: ['add-contact'],
  data() {
    return {
      friendName: '',
      friendPhone: '',
      friendEmail: '',
    }
  },

  methods: {
    submitFriendsInformation() {
      this.$emit(
        'add-contact',
        this.friendName,
        this.friendPhone,
        this.friendEmail
      )
    },
  },
}
</script>
