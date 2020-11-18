<template>
  <view class="index">
    <scroll-view scroll-y :scroll-into-view="lastMsgId">
      <view v-for="item in list" :key="item.id" :id="'msg-'+ item.id">{{item.content}}</view>
    </scroll-view>
    <button @click="addItem">添加一条</button>
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
</style>
