<template>
  <div id="app">
    <Tree :items="mapped" />
  </div>
</template>

<script>
import Tree from './components/Tree.vue'

export default {
  name: 'App',
  components: {
    Tree
  },
  data() {
    return {
      items: [
        {
          id: 1,
          parentId: null,
          name: "Desc1",
          checked: true
        },
        {
          id: 2,
          parentId: 1,
          name: "Desc2",
          checked: true
        },
        {
          id: 3,
          parentId: 1,
          name: "Desc3",
          checked: true
        },        {
          id: 4,
          parentId: 2,
          name: "Desc4",
          checked: true
        },        {
          id: 5,
          parentId: 2,
          name: "Desc5",
          checked: true
        },        {
          id: 6,
          parentId: 4,
          name: "Desc6",
          checked: true
        },        {
          id: 7,
          parentId: 4,
          name: "Desc7",
          checked: true
        }
      ]
    }
  },
  computed: {
      mapped: function() {
          const mapped = {}, roots = [];
          for(const item of this.items) {
              mapped[item.id] = item
              mapped[item.id]['childrens'] = []
          }
          for(const key in mapped){
            const item = mapped[key]
            if(item['parentId']){
                mapped[item['parentId']]['childrens'].push(item)
            } else {
                roots.push(item)
            }
          }
          return roots
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
