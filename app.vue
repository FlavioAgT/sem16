<script setup>
import { ref, computed } from 'vue'
import Characters from 'Characters.vue'
import Episodes from '.Episodes.vue'
import Locations from 'Locations.vue'

const routes = {
    '/characters': Characters,
    '/episodes': Episodes,
    '/locations': Locations,
}

const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})
</script>
