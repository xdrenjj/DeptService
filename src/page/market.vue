<template>
  <div class="market">
    <div class="top">
      <h3 class="all_money">{{ allMoney }}<span class="small">USTD</span></h3>
      <p class="info">獎勵總金額</p>
    </div>
    <div class="select">
      <router-link tag="div" class="route_box" v-for="(item, index) in list" :key="index" :to="item.route" >
        <img class="icon" :src="item.pic" :alt="item.name">
        <p class="title">{{ item.name }}</p>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'market',
  data () {
    return {
      allMoney: '1,000.0000',
      list: [
        {
          pic: require('../assets//images/reward_list1.png'),
          name: '分享獎',
          route: 'shareReward'
        },
        {
          pic: require('../assets//images/reward_list2.png'),
          name: '國際獎',
          route: ''
        },
        {
          pic: require('../assets//images/reward_list3.png'),
          name: '考核獎',
          route: ''
        },
        {
          pic: require('../assets//images/reward_list4.png'),
          name: '特別獎',
          route: ''
        }
      ]
    }
  },
  mounted () {
    this.$bus.$emit('footer', {
      button: [],
      navShow: true
    })
  },
  beforeDestroy () {
    this.$bus.$emit('footer')
  },
  methods: {
  }
}
</script>

<style lang="scss">
  @import '../assets/scss/style.scss';
  .market {
    .top {
      background-image: url(../assets/images/market_top_bg.png);
      background-size: 100% 100%;
      width: 100vw;
      height: 390px;
      text-align: center;
      .all_money {
        padding-top: 150px;
        font-size: 62px;
        font-style: italic; 
        .small {
          font-size: 24px;
        }
      }
      .info {
        font-size: 28px;
        font-weight: 700;
      }
    }
    .select {
      padding: 65px 30px 100px;
      overflow: hidden;
      .route_box {
        float: left;
        width: 300px;
        background: #1b1e24;
        margin: 0 22px 44px;
        border-radius: 20px;
        text-align: center;
        padding-top: 75px;
        .icon {
          height: 80px;
        }
        .title {
          color: #fff;
          line-height: 88px;
          font-size: 30px;
          padding-bottom: 20px;
        }
      }
    }
  }
</style>
