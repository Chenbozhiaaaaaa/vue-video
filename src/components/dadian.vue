<!--  -->
<template>
  <div>
    <el-dialog :visible.sync="dialogVisible5">
      <video id="video" width="320" height="240" controls autoplay  ref="vdo">
        <source src="http://www.w3school.com.cn/i/movie.mp4" type="video/mp4">
      </video>
      <canvas id="canvas" width="200" height="150"></canvas>
      <br>
      <el-button @click="capture">抓图</el-button>
      <el-button @click="addT">新建打点</el-button>

      <fieldset class="dad">
        <legend>视频打点</legend>
        <table border="1" width="100%" height="100%" cellpadding="1" cellspacing="0"  :data="data">
          <thead>
            <tr>
              <th class="dds">标题名称</th>
              <th>打点开始时间</th>
              <th>获取时间</th>
              <th></th>
              <th>打点结束时间</th>
              <th>获取时间</th>
              <th></th>
              <th></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item,index) in data" :key="index">
              <td></td>
              <td>{{item.start}}</td>
              <td>
                <el-button @click="dad(index)">开始打点</el-button>
              </td>
              <td>
                <el-button type icon="el-icon-video-play" @click="tz(index)"></el-button>
              </td>
              <td>{{item.end}}</td>
              <td>
                      <el-button @click="end(index)">结束打点</el-button>
              </td>
          
              <td>
                <el-button type icon="el-icon-video-play" @click="tzj(index)"></el-button>
              </td>
              <td>
                <el-button type icon="el-icon-circle-close" @click="del(index)"></el-button>
              </td>
            </tr>
          </tbody>
        </table>
      </fieldset>
    </el-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data:[
        {
          start:'',
          end:''
        },
         {
          start:'',
          end:''
        }
      ],
      dialogVisible5: true
    };
  },
  methods: {
    capture() {
      console.log(1);
      // console.log(canvas);
      let ctx = canvas.getContext("2d");
      console.log(ctx);
      ctx.drawImage(video, 0, 0, 200, 150);
      console.log(this);
    },
    dad(index){      
      let times = this.$refs.vdo.currentTime.toFixed(2)
      console.log(index);
      console.log(this.data[index]);
      this.data[index].start=times
      // console.log(times);
      console.log(this.data); 
    },
    end(index){
    let times = this.$refs.vdo.currentTime.toFixed(2)
      console.log(index);
      console.log(this.data[index]);  
      this.data[index].end=times
      // console.log(times);
      console.log(this.data);
      
    },
    tz(index){
      console.log(this.data[index].start);
      let times =this.data[index].start
      this.$refs.vdo.currentTime =times
    },
    tzj(index){
   console.log(this.data[index].start);
      let times =this.data[index].end
      this.$refs.vdo.currentTime =times
    },
    addT(){
      console.log(this.data);
      this.data.push({
          start:'',
          end:''
        })
    },
    del(index){
      this.data.splice(index,1)
    }
  }
};
</script>
<style >
</style>