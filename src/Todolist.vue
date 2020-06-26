<template>
  <div>
      <input type="text" v-model="value"><button @click="add">add</button>
      <ul>
          <li v-for="item in list" :key="item.id">
          <span>{{item.name}}</span>
          <button class="finish" @click="finish(item.id)">完成</button>
        </li>
      </ul>
  </div>
</template>

<script>
export default {
    data(){
        return{
            value:'',
            list:[{ id: 1, name: '做作业' }, { id: 2, name: '看电影' }]
        }
    },
    methods:{
        findMaxId(){
            let id = 0;
            this.list.forEach(item => {
                if (item.id > id) id = item.id
            })
            return id
        },
        add(){
            this.list=[...this.list,{id:this.findMaxId()+1,name:this.value}]
            this.value=''
        },
        finish(id){
            this.list = this.list.filter(item => item.id !== id)
        }
    }
}
</script>

<style>

</style>