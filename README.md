
#  Phase 3: Component Architecture (Vue 3)

##  Overview
Vue applications are built like a **Lego set** — small, reusable **components** connected together to form a complete UI.

This phase focuses on:
- Understanding **Single File Components (SFCs)**
- Passing data **down** using Props
- Sending events **up** using Emits
- Creating flexible layouts with **Slots**
- Knowing **when** component logic runs using Lifecycle Hooks

Mastering these concepts is critical for building **scalable and maintainable Vue applications**.

---

#  1. Single File Components (SFCs)

## What is an SFC?
A **Single File Component** is a `.vue` file that encapsulates:
- Template (HTML)
- Logic (JavaScript)
- Styles (CSS)

### Structure of an SFC

```vue
<template>
  <h1>Hello Vue</h1>
</template>

<script setup>
  // component logic
</script>

<style scoped>
  h1 {
    color: green;
  }
</style>
````

### Why SFCs?

* Better organization
* Scoped styles
* Reusable components
* Clear separation of concerns

---

# 📤 2. Props — Passing Data Down

## What are Props?

**Props** allow a parent component to pass data to a child component.

> Data flows **one-way**: Parent ➜ Child

---

### Parent Component

```vue
<template>
  <UserCard name="Sowmiya" :age="21" />
</template>
```

---

### Child Component

```vue
<script setup>
defineProps({
  name: String,
  age: Number
})
</script>

<template>
  <p>Name: {{ name }}</p>
  <p>Age: {{ age }}</p>
</template>
```

### Key Rules:

* Props are **read-only**
* Child should not modify props
* Use props for configuration and display

---

# 📢 3. Emits — Sending Events Up

## What is Emits?

**Emits** allow a child component to notify its parent when something happens.

> Events flow **Child ➜ Parent**

---

### Child Component

```vue
<script setup>
const emit = defineEmits(["increment"])
</script>

<template>
  <button @click="emit('increment')">+</button>
</template>
```

---

### Parent Component

```vue
<template>
  <CounterButton @increment="count++" />
</template>

<script setup>
import { ref } from "vue"
const count = ref(0)
</script>
```

### When to Use Emits?

* User actions
* Form submissions
* Component communication

---

# 🧩 4. Slots — Flexible Layouts

## What are Slots?

Slots allow you to **pass HTML content** into a component.

Think of slots as **placeholders** inside components.

---

### Default Slot

```vue
<!-- Parent -->
<Card>
  <p>This is card content</p>
</Card>
```

```vue
<!-- Child -->
<template>
  <div class="card">
    <slot></slot>
  </div>
</template>
```

---

### Named Slots

```vue
<!-- Parent -->
<Card>
  <template #header>Header Content</template>
  <template #footer>Footer Content</template>
</Card>
```

```vue
<!-- Child -->
<template>
  <slot name="header"></slot>
  <slot></slot>
  <slot name="footer"></slot>
</template>
```

### Use Cases:

* Layout components
* Modals
* Cards
* Tables

---

# ⏳ 5. Lifecycle Hooks

## What are Lifecycle Hooks?

Lifecycle hooks let you run code at **specific stages** of a component’s life.

---

### Common Lifecycle Hooks

| Hook            | Purpose                |
| --------------- | ---------------------- |
| `onMounted`     | Component added to DOM |
| `onUnmounted`   | Component removed      |
| `onUpdated`     | DOM updated            |
| `onBeforeMount` | Before render          |

---

### Example

```vue
<script setup>
import { onMounted, onUnmounted } from "vue"

onMounted(() => {
  console.log("Component mounted")
})

onUnmounted(() => {
  console.log("Component destroyed")
})
</script>
```

### Typical Uses:

* API calls (`onMounted`)
* Event listeners
* Cleanup tasks

