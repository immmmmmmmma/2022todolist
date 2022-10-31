<template>
  <div class="searchInput">
      <input type="text" class="inp" placeholder="오늘꺼"
      v-model="newItem">
      <div class="btn" @click="todoItem">확인</div>
  </div>
  
  <transition name="mView">
    <modal-view v-if="modal" @click="modal=false">
      <template v-slot:header>경고</template>
      <template v-slot:body>자료 입력</template>
    </modal-view>
  </transition>


</template>

<script>
import ModalView from "@/components/ModalView.vue"
export default {
  components:{ModalView},

  data(){
    return{
      newItem:'',
      modal:false,
      }
  },
  methods:{
    todoItem:function(){
      if(this.newItem != ""){
        let value = this.newItem && this.newItem.trim();
        this.$emit("addTodo",value);
      }else{
        this.modal = true
      }
      this.newItem = ''
    }
  }
}

</script>

<style lang="scss">
    .searchInput{
        display: flex;
        .inp{
            flex: 1 0 auto;
            text-indent: 10px;
        }
        .btn{
            line-height: 40px;
            padding: 0 10px;
            background: gray;
            color: #fff;
            cursor: pointer;
        }
    }
    .mView-enter-from{opacity: 0; transform: translateY(-300px);}
    .mView-enter-active{transition: 0.3s;}
    .mView-enter-to{opacity: 1; transform: translateY(0);}

    .mView-leave-from{opacity: 1;}
    .mView-leave-active{transition: 0.3s;}
    .mView-leave-to{opacity: 0;}
</style>