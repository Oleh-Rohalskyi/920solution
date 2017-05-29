<template>
<div class="team__member" >
    <img :src="member.img" alt="">
    <div class="team__member-name" v-text="member.name"></div>
    <div class="team__member-position" v-text="member.position"></div>
</div>
</template>

<script>
export default {
  name: 'team',
  props: ['member'],
  data () {
    return {}
  }
}
</script>

<style lang="scss" scoped>
.team__member {
    font-family: 'AvenirNext-Medium';
    color: #2b2b2b;
    img {
      width: 140px;
    }
    &-name {
      font-size: 14px;
      margin-top: 9px;
    }
    &-position {
      font-size: 12px;
      margin-top: 4px;
    }
  }
</style>
