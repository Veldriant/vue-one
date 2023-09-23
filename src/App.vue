<script setup>
  import { ref, computed } from 'vue';

  const users = ref([
    {id: "2", name: 'Joni', age: '11'},
    {id: "1", name: 'Markus', age: '21'}, 
    {id: "3", name: 'Havani', age: '51'},
  ])

  const products = ref([
    'Бананы',
    'Яблоки',
    'Батон',
    'Грибы',
    'Сметана',
    'Апельсины',
    'Молоко'
  ])

  const query = ref('')
  const queryProducts = computed( () =>{
    return products.value.filter((product) => product.indexOf(query.value) !==-1 );
  })

</script>

<template>
  <main>
    <ul>
      <li v-for="user in users"
        :key="user.id"    
        >
        {{ user.name }}
        <sup 
          v-if="user.age <= '18'" 
            :class="{
            'red fz-24' : user.age <= '18'
          }"
        >
          Baby
        </sup>
        <sup v-else-if="user.age < '40'"> 
          Man
        </sup>
        <sup v-else >
          Old Man
        </sup>
      </li>
    </ul>

    <div>
      <input 
      type="search"
      placeholder="Search"
      v-model="query"
      >
      <br><br>

      {{ query }}


      <ul>
        <li v-for="product in queryProducts"
          :key="product"
        >
          {{ product }}
        </li>
      </ul>
    </div>
    
  </main>
</template>


<style >
.red{
  color: red;
}
.fz-24{
  font-size: 24px;
}
</style>