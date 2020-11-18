<template>
  <view class="index">
    <scroll-view scroll-y :scroll-into-view="lastMsgId">
      <view class="msg-item" v-for="item in list" :key="item.id" :id="'msg-'+ item.id">content is :{{item.content}} ,id is : {{'msg-'+ item.id}}</view>
    </scroll-view>
    <button @tap="addItem">添加一条</button>
  </view>
</template>

<script>
export default {
  name: 'Index',
  data() {
    return {
      list: [],
      lastMsgId: ''
    }
  },
  methods: {
    addItem() {
      console.log('addItem')
      this.list.push({id: new Date().getTime(), content: this.list.length})
      this.scrollToBottom()
    },
    scrollToBottom(){
      this.scrollTo(this.list[this.list.length-1].id)
    },
    scrollTo(id) {
      setTimeout(() => {
        this.lastMsgId = 'msg-' + id
      }, 200)
    },
  },
}
</script>

<style>
.index {
  height: 100vh;
}
  .msg-item{
    padding: 10px;
    border: 1px solid black;
    margin-bottom: 10px;
  }
</style>
