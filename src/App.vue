<template>
  <div class="page-bar">
    <ul>
      <li :class="{'page-disabled' : pageArr[0].active}"><a><</a></li>
      <li v-for="item in pageArr" :class="{'jump':item.jump,'active':item.active}" @click="btnClick(item.page)"><a>{{item.page}}</a></li>
      <li :class="{'page-disabled' : pageArr[pageArr.length - 1].active}"><a>></a></li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      totalPage: 10, // 总页数
      pageArr: [{}]
    }
  },
  ready () {
    this.pageArr = this.showPage(1)
  },
  methods: {
    /**
     * 展示页数
     * @param page 当前页数
     * @param total 总页数
     */
    showPage (page) {
      // 添加初始化的页数
      let [arr, total] = [[{
        page,
        active: 1
      }], this.totalPage]
      // 左右分别添加3页
      for (let i = 1; i <= 3; i++) {
        if (page - i > 1) {
          arr.unshift({
            page: page - i,
            active: 0
          })
        }
        if (page + i < total) {
          arr.push({
            page: page + i,
            active: 0
          })
        }
      }

      // 判断左边是否添加'···'
      if (page - 4 > 1) {
        arr.unshift({
          page: '···',
          active: 0,
          jump: 1
        })
      }
      if (page + 4 < total) {
        arr.push({
          page: '···',
          active: 0,
          jump: 2
        })
      }

      // 添加第一页和最后一页
      if (page > 1) {
        arr.unshift({
          page: 1,
          active: 0
        })
      }

      if (page < total) {
        arr.push({
          page: total,
          active: 0
        })
      }
      arr.forEach((v) => {
        console.log(v.page)
      })
      return arr
    },
    btnClick (page) {
      this.pageArr = this.showPage(page)
    }
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

ul, li {
  margin: 0;
  padding: 0;
}

.page-bar li{
  list-style: none;
  display: inline-block;
}
.page-bar li:first-child>a {
  margin-left: 0px
}

.page-bar a{
  box-sizing: border-box;
  border: 1px solid #ddd;
  border-radius: 6px;
  text-decoration: none;
  position: relative;
  float: left;
  height: 28px;
  line-height: 28px;
  min-width:28px;
  text-align: center;
  color: #aaa;
  cursor: pointer;
  -webkit-user-select: none;
  margin-right: 8px;
  font-size: 14px;
}
.page-bar a:hover{
  color: #2db7f5;
  border-color: #2db7f5;
}
.page-bar .active a{
  color: #fff;
  cursor: default;
  background-color: #2db7f5;
  border-color: #2db7f5;
}
.page-bar .jump a {
  letter-spacing: -8px;
  border:0;
}
.page-bar .page-disabled a{
  cursor: not-allowed;
  color: #eee;
  border-color: #ddd;
}
</style>
