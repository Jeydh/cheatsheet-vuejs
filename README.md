# Vue.js Cheatsheet 
---

# Sommaire

* Installation
* Structure d'un composant
* Template
* Directives
* Réactivité
* Computed
* Watch
* Lifecycle Hooks
* Events
* Props
* Emits
* Slots
* Components
* Router
* Pinia
* API
* Forms
* Conditionnel
* Listes
* Style
* Helpers
* Bonnes pratiques
* Commandes utiles

---

# Installation

Créer un projet

```bash
npm create vue@latest
```

Installer les dépendances

```bash
npm install
```

Lancer le projet

```bash
npm run dev
```

Build

```bash
npm run build
```

Preview

```bash
npm run preview
```

---

# Structure d'un composant

```vue
<script setup>
import { ref } from 'vue'

const count = ref(0)

const increment = () => {
    count.value++
}
</script>

<template>
    <button @click="increment">
        {{ count }}
    </button>
</template>

<style scoped>

</style>
```

---

# Réactivité

```javascript
const count = ref(0)
```

```javascript
count.value++
```

Objet réactif

```javascript
const user = reactive({
    name: 'John',
    age: 30
})
```

---

# Computed

```javascript
const fullName = computed(() => {
    return `${user.firstName} ${user.lastName}`
})
```

---

# Watch

```javascript
watch(count, (newValue, oldValue) => {

})
```

Sur plusieurs valeurs

```javascript
watch([firstName, lastName], () => {

})
```

---

# Lifecycle Hooks

```javascript
onMounted(() => {

})

onUpdated(() => {

})

onUnmounted(() => {

})
```

Les plus utilisés

* onMounted
* onUnmounted
* onBeforeMount
* onBeforeUnmount

---

# Directives

Afficher une variable

```vue
{{ message }}
```

Condition

```vue
<div v-if="loading"></div>

<div v-else></div>
```

Boucle

```vue
<div v-for="user in users" :key="user.id">

</div>
```

Afficher / cacher

```vue
v-show
```

Liaison

```vue
:class="..."
```

```vue
:style="..."
```

```vue
:disabled="loading"
```

Événements

```vue
@click=""
```

```vue
@submit.prevent=""
```

```vue
@keyup.enter=""
```

Modèle

```vue
v-model="name"
```

---

# Gestion des événements

```vue
<button @click="save">
```

Passer un argument

```vue
@click="remove(user.id)"
```

Empêcher le comportement

```vue
@click.prevent=""
```

Empêcher la propagation

```vue
@click.stop=""
```

---

# Props

Parent

```vue
<UserCard :user="user" />
```

Enfant

```javascript
const props = defineProps({
    user: Object
})
```

---

# Emits

```javascript
const emit = defineEmits([
    'save'
])

emit('save')
```

---

# Slots

Parent

```vue
<Card>

    Contenu

</Card>
```

Enfant

```vue
<slot />
```

Slot nommé

```vue
<slot name="header"/>
```

---

# Components

Importer

```javascript
import UserCard from './UserCard.vue'
```

Utiliser

```vue
<UserCard />
```

---

# Router

Installation

```bash
npm install vue-router
```

Créer

```javascript
const router = createRouter({

})
```

Lien

```vue
<RouterLink to="/">
```

Vue

```vue
<RouterView />
```

Navigation

```javascript
router.push('/users')
```

Nom

```javascript
router.push({
    name: 'users'
})
```

Paramètre

```javascript
router.push({
    name: 'user',
    params: {
        id: 1
    }
})
```

---

# Pinia

Installation

```bash
npm install pinia
```

Créer un store

```javascript
export const useUserStore = defineStore('user', {

})
```

Composition API

```javascript
export const useCounterStore = defineStore('counter', () => {

    const count = ref(0)

    function increment(){
        count.value++
    }

    return {
        count,
        increment
    }

})
```

Utilisation

```javascript
const store = useCounterStore()

store.increment()
```

---

# API

Fetch

```javascript
const response = await fetch('/api/users')

const users = await response.json()
```

Axios

```bash
npm install axios
```

```javascript
const response = await axios.get('/api/users')
```

POST

```javascript
await axios.post('/api/users', data)
```

---

# Forms

```vue
<input
    v-model="name"
/>
```

Checkbox

```vue
<input
    type="checkbox"
    v-model="checked"
/>
```

Select

```vue
<select
    v-model="selected"
>
</select>
```

---

# Conditionnel

```vue
v-if
```

```vue
v-else
```

```vue
v-else-if
```

```vue
v-show
```

---

# Boucles

```vue
<div
    v-for="user in users"
    :key="user.id"
>
</div>
```

Avec index

```vue
v-for="(user,index) in users"
```

---

# Class dynamiques

```vue
:class="{ active:isActive }"
```

```vue
:class="[primaryClass,errorClass]"
```

---

# Style dynamique

```vue
:style="{
    color:'red'
}"
```

---

# Computed vs Watch

## computed

* retourne une valeur
* mis en cache
* sans effet de bord

## watch

* déclenche une action
* appel API
* sauvegarde
* log

---

# Provide / Inject

Parent

```javascript
provide('theme', 'dark')
```

Enfant

```javascript
const theme = inject('theme')
```

---

# Helpers utiles

```javascript
nextTick()
```

```javascript
ref()
```

```javascript
reactive()
```

```javascript
computed()
```

```javascript
watch()
```

```javascript
watchEffect()
```

```javascript
readonly()
```

---

# Bonnes pratiques

* utiliser `<script setup>`
* préférer Composition API
* éviter les gros composants
* utiliser Pinia plutôt que Vuex
* éviter les watchers inutiles
* toujours mettre un `:key`
* utiliser des composants réutilisables
* nommer les composants en PascalCase
* garder la logique métier hors des composants lorsque possible

---

# Structure conseillée

```
src/

components/

views/

router/

stores/

services/

composables/

assets/

App.vue

main.js
```

---

# Composables

Créer

```javascript
export function useCounter(){

    const count = ref(0)

    const increment = () => count.value++

    return {
        count,
        increment
    }

}
```

Utiliser

```javascript
const {
    count,
    increment
} = useCounter()
```

---

# Commandes utiles

Installer les dépendances

```bash
npm install
```

Lancer

```bash
npm run dev
```

Build

```bash
npm run build
```

Lint

```bash
npm run lint
```

Tests

```bash
npm run test
```

---

# À connaître absolument

* Composition API
* script setup
* ref
* reactive
* computed
* watch
* props
* emits
* slots
* Router
* Pinia
* composables
* lifecycle hooks
* v-model
* directives
* appels API
* async / await
* gestion des formulaires
* composants dynamiques
* Lazy Loading
* Suspense (bases)

---

# Questions fréquentes en entretien

* Quelle est la différence entre `ref()` et `reactive()` ?
* Quand utiliser `computed` plutôt que `watch` ?
* Quelle différence entre `v-if` et `v-show` ?
* À quoi sert `:key` dans un `v-for` ?
* Pourquoi utiliser Pinia plutôt qu'un simple composable ?
* Que fait `nextTick()` ?
* Comment partager un état entre plusieurs composants ?
* Quelle différence entre `props` et `emit` ?
* Quelle différence entre SPA et SSR ?
* Qu'est-ce que le Virtual DOM ?
* Pourquoi utiliser les composables ?

---

⭐ Cette cheatsheet est conçue comme une base de révision rapide avant un test technique Vue.js.
