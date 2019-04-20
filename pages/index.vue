<template>
  <div class="section">
    <div class="container">
      <label class="label">Github's Username</label>
      <div class="field has-addons">
        <div class="control">
          <input class="input" v-on:keyup.enter="getData" v-model="username" placeholder="">
        </div>
        <div class="control">
          <nuxt-link :to="'repo?username='+ username" class="button is-info">
            Search
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        username: ''
      }
    },

    methods: {
      getData: function (event) {
        console.log(event.key);
        if (event.key == "Enter") {
          console.log("enter key was pressed!");
          this.$router.push('?username=' + this.username)
        }
      }
    }

  }

</script>
