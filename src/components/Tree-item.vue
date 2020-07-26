<template>
  <div>
      <ul>
          <li v-for="item in mapped" :key="item.id">
              <input type="checkbox" :id="item.id" v-model="item.checked">
              <label :for="item.id">{{ item.name }}</label>
          </li>
      </ul>
      {{ mapped }}
  </div>
</template>