<template>
  <div class="team">
    <div class="team__title">Our Team</div>
    <div class="team__selected-member">
      <img src="http://new.ukrea.com.ua/albums/userpics/10001/big_photo.png" alt="" />
      <div class="team__member-discription">
        <div class="team__member-discription_pink">Hai Meirazade</div>
        <div class="team__member-discription_white">Founder & Chief Executive Officer</div>
        <div class="team__member-discription_black">Jerusalem Academy of Music, composer and arranger. He writes for many of the leading Israeli rock musicians, including Berry Sakharof, Hadag Nachash, Ninet Tayeb, Asaf Amdursky, Dudu Tasa, Hemi Rodner, Efrat Gosh and others. In addition to managing the backyard, I lead the project in question Strings</div>
      </div>
    </div>
    <div class="team__members">
      <member :key="key" v-for="(member, key) in content" :member="member"/>
    </div>
  </div>
</template>

<script>
import member from './member.vue'

export default {
  name: 'team',
  props: ['content'],
  components: {
    member
  },
  data () {
    return {}
  }
}
</script>

<style lang="scss" scoped>
.team {
  &__members {
    position: absolute;
    left: 286px;
    top: 448px;
    display: flex;
    justify-content: space-between;
    width: 1024px;
    text-align: center;
  }
  &__title {
    position: absolute;
    left: 286px;
    top: 134px;
    font-family: 'Playfair Display', serif;
    font-size: 36px;
    color: #db3153;
  }
  &__selected-member {
    position: absolute;
    left: 286px;
    top: 223px;
    display: flex;
    img {
      width: 190px;
    }
  }
  &__member-discription {
    margin-left: 27px;
    width: 665px;
    text-align: left;
    align-self: center;
    font-family: 'AvenirNext-Medium';
    &_pink {
      font-size: 24px;
      color: #e44a66;
      margin-bottom: 8px;
    }
    &_white {
      font-size: 18px;
      color: #ffffff;
      margin-bottom: 10px;
    }
    &_black {
      font-size: 12px;
      line-height: 1.67;
      color: #2b2b2b;
    }
  }
}
</style>
