<template>
  <div class="mainPage">
    <div class="mainPage" v-if="!otherVideoVisable">
      <video :src="startVideoUrl" autoplay loop @click="handleClickStart" height="700px"></video>
    </div>
    <div class="mainPage" v-if="otherVideoVisable">
      <video :src="videoUrl" autoplay @ended="handleVideoEnd" height="700px">其他视频</video>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return{
      otherVideoVisable: false,
      startVideoUrl: '../../video/0.mp4',
      videoUrl: '',
      videoNum: 0,
    }
  },
  methods:{
    handleClickStart(){
      console.log("调用handleClickStart方法");
      this.createRandomNum();
      console.log(this.videoNum);
      this.videoUrl = '../../video/' + this.videoNum +'.mp4'
      this.otherVideoVisable = true;
    },
    handleVideoEnd(){
      console.log("测试视频结束")
      this.otherVideoVisable = false;
    },
    createRandomNum(){
      this.videoNum = Math.floor(Math.random() * 48 + 1);
    },
  }
}
</script>

<style scoped>
  .mainPage{
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
  .end{
    margin-top: 300px
  }
</style>