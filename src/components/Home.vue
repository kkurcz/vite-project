<template>
    <div class="p-10 bg-blue-500 rounded-lg">
        <div>Home hiii</div>
        <p class="mb-4">Name in store is {{ name }}</p>
        <input
            v-model="newName"
            type="text"
            class="mr-2 p-2 border border-gray-500 rounded-lg"
        />
        <button @click="saveName" class="text-white bg-indigo-500">
            Submit
        </button>
    </div>
</template>

<script setup>
import { computed, ref } from 'vue'
import { useStore } from 'vuex'
import { useRouter } from 'vue-router'
const router = useRouter()
const store = useStore()

const name = computed(() => {
    return store.state.user.name
})

const newName = ref('')

function saveName() {
    store.dispatch('saveName', newName.value)
    newName.value = ''
    router.push('/about')
}
</script>
