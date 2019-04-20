<template>
  <div class="section">
    <div class="container">
      <nuxt-link to="/" class="button is-info is-small is-pulled-right">Back to Search Page</nuxt-link>
      <label class="label">Search Result : </label>
      <div class="box" v-if="users.id > 0">
        <article class="media">
          <div class="media-left">
            <figure class="image is-128x128">
              <img class="is-rounded" :src=" users.avatar_url ">
            </figure>
          </div>
          <div class="media-content">
            <div class="content">
              <div>
                <strong>{{users.name}}</strong> <br>
                <small>@{{users.login}}</small>
                <p class="is-marginless"> Location: {{users.location}}</p>
                <p class="is-marginless"> Follower: {{users.followers}}</p>
                <p class="is-marginless"> Public Repos: {{users.public_repos}}</p>
              </div>
            </div>
          </div>
        </article>
      </div>
      <div v-else>
        username doesn't exist
      </div>
    </div>
  </div>
</template>
<script>

  export default {
    data() {
      return {
        users: '',
        username_query: this.$route.query.username,
      }
    },
    mounted() {
      if (this.username_query != null) {
        this.getData();
      }
    },
    methods: {
      getData() {
         this.username = this.username_query;
        this.$axios.get('https://api.github.com/users/' + this.username)
          .then(response => {
            this.users = response.data;
            this.loadedRepo = true;
          })
          .catch(e => {
            console.log(e)
          });     
      },
    },
  }

</script>
