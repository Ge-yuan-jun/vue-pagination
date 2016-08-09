<template>
  <div class="page-bar">
    <ul>
      <li><a><</a></li>
      <li><a>1</a></li>
      <li class="active"><a>2</a></li>
      <li title="向前5页" class="jump-prev"><a>···</a></li>
      <li title="向后5页" class="jump-next"><a>···</a></li>
      <li class="page-disabled"><a>></a></li>
    </ul>
  </div>
</template>

<script>
export default {
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
.page-bar .jump-next a, .page-bar .jump-prev a {
  letter-spacing: -8px;
  border:0;
}
.page-bar .page-disabled a{
  cursor: not-allowed;
  color: #eee;
  border-color: #ddd;
}
</style>
