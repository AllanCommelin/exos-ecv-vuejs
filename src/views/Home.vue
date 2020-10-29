<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App" displayed/>
    <list-card :remove="removeAvatar" :avatars="avatars"/>
    <button @click="sortByDate">Trier</button>
    <div class="form">
      <h3>Créer un avatar</h3>
      <label for="firstname"></label>
      <input id="firstname" name="firstname" class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal" type="text" v-model="newAvatar.firstName">
      <label for="lastname"></label>
      <input id="lastname" name="lastname" class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal" type="text" v-model="newAvatar.lastName">
      <label for="birthday"></label>
      <input id="birthday" name="birthday" class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal" type="date" v-model="newAvatar.birthday">
      <button @click="addAvatar">Ajouter</button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import ListCard from '@/components/ListCard.vue'

export default {
  name: 'Home',
  data () {
    return {
      newAvatar: { id: null, firstName: null, lastName: null, birthday: null },
      avatars: [
        { id: 0, firstName: 'Allan', lastName: 'Commelin', birthday: '1998-02-04' }
      ],
      sorted: false
    }
  },
  components: {
    HelloWorld,
    ListCard
  },
  methods: {
    sortByDate () {
      if (this.sorted) {
        this.avatars.sort().reverse()
        this.sorted = false
      } else {
        this.avatars.sort((a, b) => {
          return new Date(a.birthday) - new Date(b.birthday)
        })
        this.sorted = true
      }
    },
    removeAvatar (id) {
      this.avatars = this.avatars.filter(avatar => avatar.id !== id)
    },
    addAvatar () {
      // adding avatar in this.avatars
      if (this.newAvatar.firstName && this.newAvatar.lastName && this.newAvatar.birthday) {
        this.newAvatar.id = this.avatars.length + 1
        this.avatars.push(this.newAvatar)
        this.newAvatar = { id: null, firstName: null, lastName: null, birthday: null }
      }
    }
  }
}
</script>
<style lang="scss">
  .home {
    margin: 0 1rem;
  }

  ul {
    display: flex;
  }

  .form {
    width: 400px;
    input {
      margin: 1rem 0;
    }
  }

  ul li {
    display: inline;
  }
</style>
