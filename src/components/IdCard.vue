<template>
    <div class="rounded rounded-t-lg overflow-hidden shadow max-w-xs my-3 mx-2">
        <img src="https://picsum.photos/300/120" class="w-full"/>
        <div class="flex justify-center -mt-8">
            <img src="https://picsum.photos/75" class="rounded-full border-solid border-white border-2 -mt-3">
        </div>
        <div class="text-center px-3 pb-6 pt-2">
            <h3 v-if="!edit" class="text-black text-sm bold font-sans">{{ fullName }}</h3>
            <div v-else>
                <input class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal my-1" type="text" v-model="firstName" name="firstname">
                <input class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal my-1" type="text" v-model="lastName" name="lastname">
            </div>
            <button v-if="!edit" @click="edit = true">Edit</button>
            <button v-else @click="edit = false">Save</button>
            <p class="mt-2 font-sans font-light text-grey-dark">Date de naissance : {{ birthday }}</p>
        </div>
        <div>
            <slot></slot>
        </div>
    </div>
</template>

<script>

export default {
    name: 'IdCard',
    props: {
        firstName: String,
        lastName: String,
        birthday: String
    },
    data () {
        return {
            edit: false
        }
    },
    computed: {
        fullName () {
            return this.firstName + ' ' + this.lastName
        }
    }
}
</script>
