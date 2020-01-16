<template>
  <div class="block">
    <el-carousel>
      <el-carousel-item v-for="(item, index) in beijing" :key="index">
        <div
          class="beijing"
          :style="
            `background:url(${$axios.defaults.baseURL +
              item.url}) center center no-repeat; background-size:contain contain`
          "
        >
          <!-- <img :src="item.url" alt="" /> -->
        </div>
      </el-carousel-item>
    </el-carousel>

    <!-- 搜素栏 -->
    <!-- 搜索框 -->
    <div class="banner-content">
      <div class="search-bar">
        <!-- tab栏 -->
        <el-row type="flex" class="search-tab">
          <span
            v-for="(item, index) in lanmu"
            :key="index"
            @click="dianji(index)"
          >
            <i>{{ item.text }}</i>
          </span>
        </el-row>

        <!-- 输入框 -->
        <el-row type="flex" align="middle" class="search-input">
          <input
            :placeholder="lanmu[gaolian].tishi"
            v-model="searchValue"
            @keyup.enter="handleSearch"
          />
          <i class="el-icon-search" @click="handleSearch()"></i>
        </el-row>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    //
    return {
      beijing: [
        { url: "http://157.122.54.189:9095/assets/images/th03.jfif" },
        { url: "http://157.122.54.189:9095/assets/images/th04.jfif" }
      ],
      lanmu: [
        {
          text: "攻略",
          tishi: "搜索城市"
        },
        {
          text: "酒店",
          tishi: "搜索城市酒店"
        },
        {
          text: "机票",
          tishi: "搜索城市"
        }
      ],
      gaolian: 0
    };
  },
  mounted() {
    //请求线上数据
    this.$axios({
      url: "/scenics/banners"
    }).then(res => {
      let { data } = res.data;
      this.beijing = data;
    });
  },
  methods: {
    dianji(index) {
      this.gaolian = index;
      if(index===2){
         this.$router.push('./air')
      }
    }
  }
};
</script>

<style lang="less" scoped>
.block {
  min-width: 1000px;
  margin: 0 auto;
  position: relative;
  /deep/.el-carousel__container {
    height: 700px;
  }
}

.beijing {
  width: 100%;
  height: 100%;
}

.banner-content {
  z-index: 9;
  width: 1000px;
  position: absolute;
  left: 50%;
  top: 45%;
  margin-left: -500px;
  border-top: 1px transparent solid;

  .search-bar {
    width: 552px;
    margin: 0 auto;
  }

  .search-tab {
    .active {
      i {
        color: #333;
      }
      &::after {
        background: #eee;
      }
    }

    span {
      width: 82px;
      height: 36px;
      display: block;
      position: relative;
      margin-right: 8px;
      cursor: pointer;

      i {
        position: absolute;
        z-index: 2;
        display: block;
        width: 100%;
        height: 100%;
        line-height: 30px;
        text-align: center;
        color: #fff;
      }

      &:after {
        position: absolute;
        left: 0;
        top: 0;
        display: block;
        content: "";
        width: 100%;
        height: 100%;
        border: 1px rgba(255, 255, 255, 0.2) solid;
        border-bottom: none;
        transform: scale(1.1, 1.3) perspective(0.7em) rotateX(2.2deg);
        transform-origin: bottom left;
        background: rgba(0, 0, 0, 0.5);
        border-radius: 1px 2px 0 0;
        box-sizing: border-box;
      }
    }
  }

  .search-input {
    width: 550px;
    height: 46px;
    background: #fff;
    border-radius: 0 4px 4px 4px;
    border: 1px rgba(255, 255, 255, 0.2) solid;
    border-top: none;
    box-sizing: unset;

    input {
      flex: 1;
      height: 20px;
      padding: 13px 15px;
      outline: none;
      border: 0;
      font-size: 16px;
    }

    .el-icon-search {
      cursor: pointer;
      font-size: 22px;
      padding: 0 10px;
      font-weight: bold;
    }
  }
}
</style>
