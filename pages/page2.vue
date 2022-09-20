<template>
  <div class="main-wrapper">
    <div class="main-container container pt-5">
      <div class="grid-view">
        <div class="todo-list-wrapper" v-for="item in workSpaceList" :key="item.id">
          <div class="todo-contents">
            <div class="todo-header">
              <p>{{ item.name }}</p>
            </div>
            <input type="text" v-model="item.newCardName">
            <button @click="createColumn(item)">Add coulmn</button>
            <div class="todo-add-card">
                <ul>
                    <li v-for="card in item.items" :key="card.id">
                        {{ card.name }}
                    </li>
                </ul>
            </div>
          </div>
        </div>
        <div class="workspace-add">
          <div class="input-field">
            <input type="text" v-model="workspaceName">
            <button class="btn btn-primary" @click="createWorkspace()">Save</button>
          </div>
          <div class="">
            <p>Add Another List</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        workspaceName: '',
        workSpaceList: [],
        newItem: ''
      }
    },
    methods: {
      createWorkspace() {
        var id = Math.floor((Math.random() * 1000));
        this.workSpaceList.push({
          id: id,
          name: this.workspaceName,
          newCardName:'',
          items:[]
        })
      },
      createColumn(column) {
        const id = Math.floor((Math.random() * 1000));
        column.items.push({
            id:id,
            name:column.newCardName        })
      }
    },
  }

</script>
<style>
  body {
    background: #41b3A4;
  }

  .grid-view {
    display: flex;
    gap: 1rem;
  }

  .todo-list-wrapper {
    height: 100%;
    width: 275px;
    background-color: #adadad;
    padding: 1rem;
    border-radius: .5rem;
    overflow: hidden;
    display: flex;
  }

  .todo-header p {
    font-size: 1.2rem;
    font-weight: 700;
    color: #557a95;
  }

</style>
