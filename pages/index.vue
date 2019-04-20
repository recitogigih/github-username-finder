<template>
  <div class="section">
    <div class="container">
      <label class="label">Github's Username</label>
      <div class="field has-addons">
        <div class="control">
          <input class="input"  v-model="username" placeholder="">
        </div>
        <div class="control">
          <nuxt-link class="button is-info">
            Search
          </nuxt-link>
        </div>
      </div>

    </div>
  </div>
</template>


<script>
export default {
  
}
</script>


