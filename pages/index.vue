<template>
  <div class="main-container container">
      <div class="cardlist card mb-2" v-for="item in todoList" :key="item.id">
        <p class="text-danger">{{ item.title }}</p>
          <div class="sub-cards card mb-2" v-for="card in item.cards" :key="card.id">
            <p class="text-success">{{ card.title }}</p>
          </div>
          <div>
          <input type="text" v-model="subCard.title">
          <button @click="addCard(item.id)">Add Card</button>
          </div>
          
      </div>
      <div class="add-btn">
      <input type="text" v-model="newItem.title" >
      <button class="" type="save-btn" @click="saveTodo()">Add</button>
      <button type="button">Add todo</button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return{
      newItem:{},
      subCard:{},
      todoList:[
        {
          id:1,
          title:"Books",
          cards:[
            {
              id:1,
              title:"Books card1",
              description:"test descriptions"
            },
            {
              id:2,
              title:"Books card2",
              description:"test descriptions"
            }
          ]
        },
        {
          id:2,
          title:"Books 2",
          cards:[
            {
              id:1,
              title:"Books card1",
              description:"test descriptions"
            },
            {
              id:2,
              title:"Books card2",
              description:"test descriptions"
            }
          ]
        }
      ]
    }
  },
  methods:{
    saveTodo(){
      var listLength = this.todoList.length;
      var id = this.todoList[listLength - 1].id + 1;
      this.newItem.id = id;
      this.todoList.push(this.newItem);
      this.newItem = {}
    },
    addCard(id){
      this.todoList.map((v) =>{
        if(v.id == id){
          if( v?.cards){
            // var cardLength = v.cards.length;
            console.log("no cards")
          }
          // this.subCard.id = v.cards[cardLength -1 ].id + 1;
          // v.cards.push(this.subCard);
          // this.subCard={}
        }
      })
    }
  },
  mounted(){

  }
}
</script>
<style>
body{
  margin: 0;
  padding: 0;
}
</style>
