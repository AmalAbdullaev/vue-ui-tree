<template>
  <div>
      <ul>
          <li v-for="item in items" :key="item.id">
            <input type="checkbox" :id="item.id" v-model="item.checked">
            <label :for="item.id">{{ item.name }}</label>
              <Tree :items="item.childrens"/>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'Tree',
  props: {
    items: Array
  }
}
</script>

