<template>
  <div>
    <input class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal my-1" type="text" v-model="search">
    <ul>
      <li v-for="avatar in results" v-bind:key="avatar.id">
        <id-card :first-name=avatar.firstName :last-name=avatar.lastName :birthday=getBirthday(avatar.birthday)>
          <button @click="remove(avatar.id)">Supp</button>
        </id-card>
      </li>
    </ul>
  </div>
</template>

<script>
    import IdCard from '@/components/IdCard.vue'

    export default {
        name: 'ListCard',
        components: {
          IdCard
        },
        props: {
          avatars: Array,
          remove: Function
        },
        data () {
          return {
            search: ''
          }
        },
        computed: {
          results () {
            return this.avatars.filter(avatar => avatar.firstName.match(this.search))
          }
        },
        methods: {
          getBirthday (birthday) {
            birthday = new Date(birthday)
            const day = birthday.getUTCDate().toString().length === 2 ? birthday.getUTCDate() : '0' + birthday.getUTCDate()
            let month = birthday.getUTCMonth() + 1
            month = month.toString().length === 2 ? month : '0' + month
            return day + '/' + month + '/' + birthday.getFullYear()
          }
        }
    }
</script>

<style scoped>

</style>
