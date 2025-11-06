<template>
  <div class="q-pa-md q-gutter-sm">
    <q-btn push color="white" text-color="primary" label="Unread Mails">
      <q-badge color="orange" v-model="unread" floating>{{unread}}</q-badge>
    </q-btn>

    <q-btn dense color="purple" round icon="email" class="q-ml-md">
      <q-badge color="red" v-model="open" floating>{{ open }}</q-badge>
    </q-btn>
  </div>

  <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card bg-secondary text-white" v-for="item in msg" :key="item">
      <q-card-section>
        <div class="text-h6">{{item.title }}</div>
        <div class="text-subtitle2">{{item.autor}}</div>
      </q-card-section>

      <q-card-section>
        {{ item.tekst }}
      </q-card-section>

      <q-separator dark />

      <q-card-actions>
        <q-btn flat @click="openMsg()">Open</q-btn>
        <q-btn flat @click="deleteMsg()">Delete</q-btn>
      </q-card-actions>
    </q-card>
  </div>
  <div class="q-pa-md row items-start q-gutter-md">
    <q-input v-model="title" label="Title" />
    <q-input v-model="autor" label="Autor" />
    <q-input v-model="text" label="Tekst" />
    <q-btn flat @click="save()">save</q-btn>

  </div>
  
</template>

<script setup>
  import {ref} from 'vue'
  const msg =[{
    title:"Changing planet",
    autor:"John Doe",
    tekst:"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
  },
  {
    title:"New",
    autor:"John Pork",
    tekst:"Lagano."
  },
  {
    title:"0 planet",
    autor:"Doe John",
    tekst:"Zadnji preživljeli na planetu 0."
  },
]
 /// const title='Changing planet'
  ///const autor='John Doe'
  ///const tekst='Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  let unread = ref(22)
  let open = ref(4)
  let title=ref('')
  let autor=ref('')
  let tekst=ref('')



  function openMsg() {
    if (open.value>0){
      open.value -= 1 
      console.log("open"+open.value)
    }
    else{
      console.log("nema više napročitanih poruka")
    }  
  }
  function deleteMsg() {
    if (unread.value > 0 ){
      unread.value -=1
    console.log("delete"+unread.value)
  }
  else{
    console.log("nema više nepročitanih poruka")
  }
}
  function save(){
    msg.push({title:title.value, autor:autor.value, tekst:tekst.value})
    console.log(title.value+""+autor.value+""+tekst.value)
  }
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 250px
</style>