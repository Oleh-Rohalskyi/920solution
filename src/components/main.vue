<template>
  <div class="main">
    <block v-for="(item,key) in blocksConfig" :key="key" :blockName="item.name" :colors="{ menu: item.menu.colors, button: item.button.colors }" :block-name="item.name" :logo-src="item.logoSrc" :block-bg="item.background">
  
      <div v-if="item.name == 'header'" class="header">
        <div class="header__title">
          Hello. We are
          <span class="header__title_pink">920 solutions</span>, thought-oriented marketing agency. We grow businesses through insightful study, killer creative and flawless exectution
        </div>
      </div>
      <div v-if="item.name == 'psihology'" class="psihology">
        <img src="http://new.ukrea.com.ua/albums/userpics/10001/normal_page-1.png" alt="">
        <div class="psihology__discription">
          <h3>
            It’s not about your budget or the size of your company.
          </h3>
          <p>
            Customers are customers. Needs are needs. Marketplace mentality is the same, regardless if your company does $50,000 or $500,000,000 in sales.
          </p>
          <p>
            At CRE8EGY, we understand this and apply it to our client’s business. We are big creative thinkers, with billions of dollars in results. But we are also explorers. We dive deep to discover small gems that lead to consumer breakthroughs, breakthroughs that build sales and grow businesses. This is our process. We learn. We evolve. We act. We get results.
          </p>
        </div>
      </div>
  
      <div v-if="item.name == 'portfolio'" class="portfolio">
        <div class="progress">
          <div class="progress__orange-start">
            <div class="progress__bg"></div>
            <div class="progress__text">CASE STUDY</div>
          </div>
          <div class="progress__item">Creative — Design — Advertising — Digital</div>
        </div>
        <div class="portfolio__discription">
          <h3>
            Nam Nam
            <div class="hr"></div>
          </h3>
          <p>
            Arsenault Dermatology wanted us to develop a new advertising campaign for their award winning, growing practice. They wanted something that would help them stand out from the hundreds of other local dermatologists. </p>
          </p>
          <img src="http://new.ukrea.com.ua/albums/userpics/10001/phones.png" alt="">
        </div>
        <div class="portfolio__button">
          EXPLORE ENTIRE PORTFOLIO
        </div>
      </div>
  
      <div v-if="item.name == 'services'" class="services">
        <div class="services__block">
          <div class="services__item">
            <div class="services__top">
              <img src="http://new.ukrea.com.ua/albums/userpics/10001/UX.png" />
              <div class="services__title">UI/UX DESIGN</div>
            </div>
            <div class="services__bot">Design-related roles exist in a range of areas from industrial design (cars, furniture) to print (magazines, other publications) to tech (websites, mobile apps).</div>
          </div>
          <div class="services__item">
            <div class="services__top">
              <img src="http://new.ukrea.com.ua/albums/userpics/10001/development.png" />
              <div class="services__title">DEVELOPMENT</div>
            </div>
            <div class="services__bot">Software development is the process of computer programming, documenting, testing, and bug fixing involved in creating and maintaining applications and frameworks resulting in a software product.</div>
          </div>
          <div class="services__item">
            <div class="services__top">
              <img src="http://new.ukrea.com.ua/albums/userpics/10001/consulting.png" />
              <div class="services__title">CONSULTING</div>
            </div>
            <div class="services__bot">In addition to providing advice, IT consultancies often estimate, manage, implement, deploy, and administer IT systems on behalf of their client organizations - a practice known as "outsourcing".</div>
          </div>
        </div>
        <div class="services__subtext">Check our
          <a href="#">portfolio</a> for taste of what we do.
          <div class="services__line"></div>
        </div>
      </div>
  
      <team v-if="item.name === 'team'" :content="item.content"/>
  
      <contact-form v-if="item.name === 'contact'" :content="item.content" />

    </block>
  </div>
</template>

<script>
import block from './block'
import blocksConfig from '../blocksConfig'
import contactForm from './contact/contact-form'
import team from './team/team'

export default {
  name: 'main',
  components: {
    block,
    contactForm,
    team
  },
  data () {
    return {
      blocksConfig
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
$blockHeightIndex: 100/798;
$blockWidthIndex: 100/1440;

.menu_header {
  //text-shadow: black 1px 0px, black 1px 1px, black 0px 1px, black -1px 1px, black -1px 0px, black -1px -1px, black 0px -1px, black 1px -1px;
  li.selected {
    & a {
      margin-left: 0 !important;
    }
    &:before {
      content: '' !important;
    }
  }
}

.header {
  &__title {
    position: absolute;
    left: 324px;
    top: 269px;
    width: 790px;
    font-family: 'Playfair Display', serif;
    font-size: 36px;
    line-height: 1.44;
    color: #ffffff;
    &_pink {
      color: #db3153;
    }
  }
}

.services {
  position: absolute;
  top: 215px;
  left: 325px;
  width: 990px;
  &__subtext {
    position: absolute;
    top: 385px;
    left: 0;
    font-size: 36px;
    font-family: 'Playfair Display', serif;
    color: #0b0c11;
    a {
      color: #25b694;
    }
  }
  &__line {
    position: absolute;
    left: 194px;
    top: 39px;
    border-bottom: 1px solid #25b694;
    width: 120px;
  }
  &__block {
    display: flex;
    text-align: left;
    justify-content: space-between;
  }
  &__item {
    width: 262px;
    .services__top {
      display: flex;
      width: 115px;
      font-family: FuturaPT;
      font-size: 14px;
      font-weight: 500;
      color: #25c0a5;
      img {
        width: 84px;
        display: block;
      }
      .services__title {
        align-self: center;
        margin-left: 12px;
        white-space: nowrap;
      }
    }
  }
  &__bot {
    font-family: 'FuturaStd-Book';
    font-size: 14px;
    line-height: 1.5;
    color: #202020;
    margin-top: 22px;
  }
}

.portfolio {
  img {
    display: block;
    position: absolute;
    width: 441px;
    top: 0;
    left: 550px;
  }
  &__button {
    position: absolute;
    top: 46%;
    left: 22.5%;
    font-family: "FuturaPTMedium";
    font-size: 14px;
    font-weight: 500;
    line-height: 3.5;
    text-align: center;
    color: #a6d4da;
    width: 264px;
    height: 48px;
    background-color: #ffffff;
    cursor: pointer;
  }
  height: 100%;
  width: 100%;
  .progress {
    position: absolute;
    left: 22.3%;
    top: 11.5%;
    display: flex;
    &__text {
      position: absolute;
      top: 3px;
      left: 8px;
    }
    &__bg {
      background-color: #ff8a5b;
      width: 104px;
      height: 100%;
      transform: skewX(-20deg);
      position: absolute;
      top: 0;
      left: -10px;
    }
    &__orange-start {
      overflow-x: hidden;
      position: relative;
      width: 96px;
      height: 20px;
      font-family: "FuturaPTMedium";
      font-size: 14px;
      font-weight: 500;
      color: #ffffff;
    }
    &__item {
      padding-top: 3px;
      margin-left: 15px;
      font-family: 'Playfair Display', serif;
      font-size: 14px;
      color: #2b2b2b;
    }
  }
  &__discription {
    color: #2b2b2b;
    position: absolute;
    top: $blockHeightIndex*142%;
    left: $blockWidthIndex*324%;
    font-family: 'Playfair Display', serif;
    font-size: 36px;
    width: 509px;
    text-align: left;
    h3 {
      .hr {
        margin-top: 5px;
        width: 160px;
        opacity: 0.42;
        border-top: solid 2px #87B3B6;
      }
      line-height: 1.17;
      font-size: 36px;
      margin-bottom: 18px;
    }
    p {
      font-size: 18px;
      line-height: 1.56;
    }
  }
}

.psihology {
  height: 100%;
  width: 100%;
  img {
    height: 100%;
    position: absolute;
    right: 0;
    z-index: -1;
  }
  &__discription {
    color: #2b2b2b;
    position: absolute;
    top: $blockHeightIndex*191%;
    left: $blockWidthIndex*324%;
    font-family: 'Playfair Display', serif;
    font-size: 36px;
    width: 509px;
    text-align: left;
    h3 {
      line-height: 1.17;
      font-size: 36px;
      margin-bottom: 62px
    }
    p {
      font-size: 18px;
      line-height: 1.56;
    }
    p:nth-child(3) {
      font-size: 18px;
      margin-top: 40px;
    }
  }
}
</style>
