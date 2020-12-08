<template>
  <div class="user">
    <h2 class="username">@{{ user.username }}</h2>
    <p>{{ user.getfullName }}</p>
    <p></p>
    <p>{{ user.email }}</p>
    <p class="admin-badge" v-if="user.isAdmin">{{ user.isAdmin }}</p>
    <strong> {{ user.followers }} followers </strong>
    <br />
    <button @click="followUser()">Follow</button>
    <br />
    <br />
    <form v-on:submit.prevent="createNewTwoot">
      <label for="twoot" id="twoot-input">New Twoot</label>
      <textarea
        name="twoot"
        id="twoot"
        cols="30"
        rows="10"
        v-model="newTwootContent"
      >
      </textarea>
      <div class="twoot-type">
        <label for="twoot-type">Type</label>
        <br />
        <br />
        <select name="twoot_type" id="twoot-type" v-model="newTwootType">
          <option
            v-for="option in twoot_types"
            v-bind:key="option.id"
            value="option.value"
          >
            {{ option.name }}
          </option>
        </select>
      </div>
      <button>Twoot</button>
    </form>
  </div>

  <div class="twoots">
    <h3 class="twootes-header">Recent Twoots</h3>

    <div class="twoot" v-for="twoot in twoots" v-bind:key="twoot.id">
      <Twoot
        v-bind:twoot="twoot"
        v-bind:content="twoot.content"
        v-bind:username="user.username"
        v-on:favorite="toggleFavorite(twoot.id)"
      >
      </Twoot>
    </div>
  </div>
</template>

<script>
import Twoot from "./Twoot";

export default {
  name: "UserProfile",
  components: { Twoot },
  data() {
    return {
      newTwootContent: "",
      newTwootType: "instant",
      user: {
        username: "jod35",
        firstName: "ssali",
        lastName: "Jonathan",
        email: "jodestrevin@gmail.com",
        isAdmin: false,
        followers: 0,
      },
      twoots: [
        { id: 1, content: "Twotter is cool" },
        { id: 2, content: "I am coding Vue" },
        { id: 3, content: "This is amazing" },
      ],
      twoot_types: [
        { value: "draft", name: "Draft" },
        { value: "instant", name: "Instant" },
      ],
    };
  },
  computed: {
    getfullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followUser() {
      this.user.followers++;
    },
    toggleFavorite(id) {
      console.log(`Favorited twoot with ID ${id}`);
    },
    createNewTwoot(){
        if(this.newTwootContent && this.newTwootType !== 'draft'){
            this.twoots.unshift({
                id:this.twoots.id +1,
                content: this.newTwootContent

            })
        }
        this.newTwootContent="";
    }
  },
  mounted() {
    this.followUser();
  },
  watch: {
    follow(oldFollwerCount, NewfollowerCount) {
      if (oldFollwerCount < NewfollowerCount) {
        console.log(`${this.user.username} has been followed`);
      }
    },
  },
};
</script>

<style>
.user {
  background-color: white;
  padding: 20px;
  width: 20%;
  min-height: 400px;
  border-radius: 7px;
  position: fixed;
}
.twoots {
  width: 70%;
  padding: 20px;
  position: relative;
  left: 300px;
}
.twoot {
  padding: 10px;
  border-radius: 7px;
  background-color: white;
  margin: 10px;
  transition: all 1.2s;
}
.twoot:hover {
  transform: scale(1.1, 1.1);
  cursor: pointer;
}
.admin-badge {
  background-color: rebeccapurple;
  color: white;
  padding: 10px;
}
.twoot-type {
  margin-top: 30px;
}
</style>