<template>
  <div class="address">
    <div class="wel">恭请光临</div>
    <div class="detail">
      <div>地址：成都市郫都区望丛中路1088号</div>
      <div>席设：天之府温德姆至尊豪庭大酒店</div>
    </div>
    <a-map></a-map>

  </div>
</template>

<script>
  import AMap from './a-map'

  export default {
    components: {
      AMap
    }
  }
</script>


<style lang="less" scoped>
  .address {
    background-color: #efefef;
  }

  .wel {
    font-size: 23px;
    padding: 10px 0 ;
    text-align: center;
  }

  .detail {
    padding: 0 20px;
  }

</style>
