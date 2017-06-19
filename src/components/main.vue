<template>
  <div class="main" id="fullpage">
    <block v-for="(item,key) in blocksConfig" class="section" :key="key" :links="links" :blockName="item.name" :colors="{ menu: item.menu.colors, button: item.button.colors }" :block-name="item.name" :logo-src="item.logoSrc" :block-bg="item.background">
  
      <!--header-->
      <div v-if="item.name == 'header'" id="header" class="header">
        <div class="header__title">
          <p>Hello! We are
            <span class="header__title_pink">920 solutions</span>, killer creative and result-oriented IT consulting company. We are part of GLCC Solutions consulting firm, which has been providing advises to the governments around the world to achieve rapid economic growth and improve public services.</p>
          <p> Here at 920 Solutions we design and develop real world digital solutions, including mobile apps and web applications for business transformation, business restructuring and growth hacking.</p>
          <p>We are creative thinkers, experienced and dedicated team. We go deep insights to understand your business, your challenges and the end-user’s need and, at the same time, we assure fast and flawless execution of each project. We are here 24/7 to help your business succeed. You just have to get started with us!</p>
        </div>
      </div>
  
      <!--psihology-->
      <div v-if="item.name == 'psihology'" id="psihology" class="psihology">
        <img src="http://new.ukrea.com.ua/albums/userpics/10001/normal_page-1.png" alt="">
        <div class="psihology__discription">
          <h3>
            We Get the Right Things Done
          </h3>
          <p>
            Our team expertise is broad, and deep. We are not only IT developers, our partners have more than 10 years of hands-on experience in leading complex institutional reforms, including organizational changes and business transformation, business restructuring and re-engineering business processes in Georgia, Eastern Europe and Central Asia.
          </p>
          <p>
            Realizing that no processes can be fully re-engineered unless the business strategies are aligned to IT strategy, we conveyed our reforming experience into IT consulting services and established IT development company.
          </p>
          <p>
            We do not only build mobile and web applications, we provide most appropriate digital solutions based on studies of emerging trends, competitors and customer insights. We use user-centered interaction design and scalable software architecture to achieve the best outcomes.
          </p>
          <p>
            We make sure that our work streams are transferable to the Client through continues exchange of feedback at each stage of software development. This is our process: We analyze, we work in team, we evolve, we act and we get results.
          </p>
        </div>
      </div>
  
      <!--portfolio-->
      <div v-if="item.name == 'portfolio'" id="portfolio" class="portfolio">
        <div class="progress">
          <div class="progress__orange-start">
            <div class="progress__bg"></div>
            <div class="progress__text">CASE STUDY</div>
          </div>
          <div class="progress__item">Creative — Design — Advertising — Digital</div>
        </div>
        <div class="portfolio__discription">
          <div class="portfolio__content">
            <h3>
              Nam Nam
              <div class="hr"></div>
            </h3>
            <p>
              NamNam team wanted us to develop mobile and web application, which would help them to stand out from hundreds of other dating apps. NamNam provides totally new ways to socialize. The application is not merely dating platform, it provides possibility to meet people, invite others to join in your activities, explore new entertainment places and manage it all in one place with a simple click.
            </p>
            <div class="portfolio__button">
              EXPLORE ENTIRE PORTFOLIO
            </div>
          </div>
          <img src="http://new.ukrea.com.ua/albums/userpics/10001/phones.png" alt="">
        </div>
        
        
      </div>
  
      <!--services-->
      <div v-if="item.name == 'services'" id="services" class="services">
        <div class="services__block">
          <div class="services__item">
            <div class="services__top">
              <img src="http://new.ukrea.com.ua/albums/userpics/10001/UX.png" />
              <div class="services__title">Outstanding design & UI/UX</div>
            </div>
            <div class="services__bot">Ideas never come out fully formed. We help you to transform your business ideas into viable solutions through outstanding design and easy-to-use interface, incorporating UI/UX best practices. Our designers are working directly with the Clients to catch their insights and deliver applicable and relevant final product. We use powerful design prototyping tools to provide Clients with clickable and interactive prototypes. This approach enables them to better visualize the end result. </div>
          </div>
          <div class="services__item">
            <div class="services__top">
              <img src="http://new.ukrea.com.ua/albums/userpics/10001/development.png" />
              <div class="services__title">Web and Mobile Development</div>
            </div>
            <div class="services__bot">We specialize in apps for iOS and Android, as well as web development. When it comes to software development we constantly go beyond the boundaries what is possible. What us makes different is approaching to each project with open mind and fresh ideas, innovate and always keep track of new technologies as they arise.</div>
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
          <a class="services__line">portfolio</a> for taste of what we do.
        </div>
      </div>
  
      <!--team-->
      <team v-if="item.name === 'team'" id="team" :content="item.content" />
  
      <!--contact-->
      <contact-form v-if="item.name === 'contact'" id="contact" :content="item.content" />
  
    </block>
  </div>
</template>

<script>
import block from './block'
import blocksConfig from '../blocksConfig'
import contactForm from './contact/contact-form'
import team from './team/team'

import $ from 'jquery'
import 'fullpage.js/dist/jquery.fullPage.js'
import 'jquery.scrollbar'

export default {
  name: 'main',
  created () {
    this.links = this.linksMap()
    $(document).ready(function () {
      $('#fullpage').fullpage()
    })
  },
  components: {
    block,
    contactForm,
    team
  },
  data () {
    return {
      blocksConfig,
      links: '',
      opts: {
        start: 0,
        dir: 'v',
        duration: 500,
        beforeChange: function (prev, next) {
        },
        afterChange: function (prev, next) {
        }
      }
    }
  },
  methods: {
    linksMap () {
      return blocksConfig.filter(i => i.linkText).map(i => {
        return {
          name: i.name,
          linkText: i.linkText
        }
      })
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
  margin: 10% 0 10% 10%;
  padding-right: 10%;
  &__title {
    overflow-y: scroll;

    height: 100%;
    max-width: 790px;
    font-family: 'Playfair Display', serif;
    font-size: 36px;
    line-height: 1.44;
    color: #ffffff;
    &_pink {
      color: #db3153;
    }
    & p {
      margin-top: 20px;
    }
  }
}

.services {
  margin-top: 10%;
  margin-left: 10%;
  margin-right: 200px;
  margin-bottom: 10%;
  width: 100%;
  &__subtext {
    margin-left: 10%;
    margin-top: 90px;
    font-size: 36px;
    font-family: 'Playfair Display', serif;
    color: #0b0c11;
    a {
      color: #25b694;
    }
  }
  &__line {
    position: relative;
    &:after {
      content: "";
      position: absolute;
      bottom: 3px;
      border-bottom: 1px solid #25b694;
      width: 124px;
      left: 15px;
    }
  }
  &__block {
    display: flex;
    text-align: left;
    justify-content: space-around;
  }
  &__item {
    width: 277px;
    padding: 0 7px;
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
  margin: 10% 0 10% 10%;
  width: 100%;
  img {
    display: block;
    width: 441px;
  }
  &__button {
    margin-top: 50px;
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
  .progress {
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
  &__content {
    padding: 30px 50px 30px 0;
  }
  &__arrow {
    padding: 30px 50px 30px 0;
  }
  &__discription {
    display: flex;
    color: #2b2b2b;
    font-family: 'Playfair Display', serif;
    font-size: 36px;
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
  padding: 200px 0;
  margin-left: 10%;
  position: relative;
  img {
    height: 100%;
    position: absolute;
    top: 0;
    right: 0;
    z-index: -1;
  }
  &__discription {
    color: #2b2b2b;
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

fieldset[disabled] .multiselect {
  pointer-events: none
}

.multiselect__spinner {
  position: absolute;
  right: 1px;
  top: 1px;
  width: 48px;
  height: 35px;
  background: #fff;
  display: block
}

.multiselect__spinner:after,
.multiselect__spinner:before {
  position: absolute;
  content: "";
  top: 50%;
  left: 50%;
  margin: -8px 0 0 -8px;
  width: 16px;
  height: 16px;
  border-radius: 100%;
  border-color: #41b883 transparent transparent;
  border-style: solid;
  border-width: 2px;
  box-shadow: 0 0 0 1px transparent
}

.multiselect__spinner:before {
  animation: a 2.4s cubic-bezier(.41, .26, .2, .62);
  animation-iteration-count: infinite
}

.multiselect__spinner:after {
  animation: a 2.4s cubic-bezier(.51, .09, .21, .8);
  animation-iteration-count: infinite
}

.multiselect__loading-enter-active,
.multiselect__loading-leave-active {
  transition: opacity .4s ease-in-out;
  opacity: 1
}

.multiselect__loading-enter,
.multiselect__loading-leave-active {
  opacity: 0
}

.multiselect,
.multiselect__input,
.multiselect__single {
  font-family: inherit;
  font-size: 14px;
  -ms-touch-action: manipulation;
  touch-action: manipulation
}

.multiselect {
  box-sizing: content-box;
  display: block;
  position: relative;
  width: 100%;
  min-height: 40px;
  text-align: left;
  color: #35495e;
  font-family: "AvenirNext-Medium";
}

.multiselect * {
  box-sizing: border-box
}

.multiselect:focus {
  outline: none
}

.multiselect--disabled {
  pointer-events: none;
  opacity: .6
}

.multiselect--active {
  z-index: 1
}

.multiselect--active .multiselect__current,
.multiselect--active .multiselect__input,
.multiselect--active .multiselect__tags {
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0
}

.multiselect--active .multiselect__select {
  transform: rotate(180deg)
}

.multiselect--above.multiselect--active .multiselect__current,
.multiselect--above.multiselect--active .multiselect__input,
.multiselect--above.multiselect--active .multiselect__tags {
  border-top-left-radius: 0;
  border-top-right-radius: 0
}

.multiselect__input,
.multiselect__single {
  position: relative;
  display: inline-block;
  min-height: 20px;
  line-height: 20px;
  border: none;
  border-radius: 5px;
  background: #89233c;
  padding: 1px 0 0 5px;
  width: 100%;
  color: white;
  transition: border .1s ease;
  box-sizing: border-box;
  margin-bottom: 8px
}

.multiselect__tag~.multiselect__input,
.multiselect__tag~.multiselect__single {
  width: auto
}

.multiselect__input:hover,
.multiselect__single:hover {
  border-color: #cfcfcf
}

.multiselect__input:focus,
.multiselect__single:focus {
  border-color: #a8a8a8;
  outline: none
}

.multiselect__single {
  padding-left: 6px;
  margin-bottom: 8px
}

.multiselect__tags {
  min-height: 40px;
  display: block;
  padding: 8px 40px 0 8px;
  border: 1px solid #89233c;
  background: #89233c
}

.multiselect__tag {
  position: relative;
  display: inline-block;
  padding: 4px 26px 4px 10px;
  border-radius: 5px;
  margin-right: 10px;
  color: #fff;
  line-height: 1;
  background: #41b883;
  margin-bottom: 8px;
  white-space: nowrap
}

.multiselect__tag-icon {
  cursor: pointer;
  margin-left: 7px;
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
  font-weight: 700;
  font-style: normal;
  width: 22px;
  text-align: center;
  line-height: 22px;
  transition: all .2s ease;
  border-radius: 5px
}

.multiselect__tag-icon:after {
  content: "\D7";
  color: white;
  font-size: 16px
}

.multiselect__tag-icon:focus,
.multiselect__tag-icon:hover {
  background: #369a6e
}

.multiselect__tag-icon:focus:after,
.multiselect__tag-icon:hover:after {
  color: #fff
}

.multiselect__current {
  min-height: 40px;
  overflow: hidden;
  padding: 8px 12px 0;
  padding-right: 30px;
  white-space: nowrap;
  border-radius: 5px;
  border: 1px solid #e8e8e8
}

.multiselect__current,
.multiselect__select {
  line-height: 16px;
  box-sizing: border-box;
  display: block;
  margin: 0;
  text-decoration: none;
  cursor: pointer
}

.multiselect__select {
  position: absolute;
  width: 40px;
  height: 38px;
  right: 1px;
  top: 1px;
  padding: 4px 8px;
  text-align: center;
  transition: transform .2s ease
}

.multiselect__select:before {
  position: relative;
  right: 0;
  top: 65%;
  color: white;
  margin-top: 4px;
  border-style: solid;
  border-width: 5px 5px 0;
  border-color: white transparent transparent;
  content: ""
}

.multiselect__placeholder {
  color: #adadad;
  display: inline-block;
  margin-bottom: 10px;
  padding-top: 2px
}

.multiselect--active .multiselect__placeholder {
  display: none
}

.multiselect__content {
  position: absolute;
  list-style: none;
  display: block;
  background: #fff;
  width: 100%;
  max-height: 240px;
  overflow: auto;
  padding: 0;
  margin: 0;
  border: 1px solid #e8e8e8;
  border-top: none;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  z-index: 1
}

.multiselect--above .multiselect__content {
  bottom: 100%;
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  border-bottom: none;
  border-top: 1px solid #e8e8e8
}

.multiselect__content::webkit-scrollbar {
  display: none
}

.multiselect__element {
  display: block
}

.multiselect__option {
  display: block;
  padding: 12px;
  min-height: 40px;
  line-height: 16px;
  text-decoration: none;
  text-transform: none;
  vertical-align: middle;
  position: relative;
  cursor: pointer;
  white-space: nowrap
}

.multiselect__option:after {
  top: 0;
  right: 0;
  position: absolute;
  line-height: 40px;
  padding-right: 12px;
  padding-left: 20px
}

.multiselect__option--highlight {
  background: #41b883;
  outline: none;
  color: #fff
}

.multiselect__option--highlight:after {
  content: attr(data-select);
  background: #41b883;
  color: #fff
}

.multiselect__option--selected {
  background: #f3f3f3;
  color: #35495e;
  font-weight: 700
}

.multiselect__option--selected:after {
  content: attr(data-selected);
  color: silver
}

.multiselect__option--selected.multiselect__option--highlight {
  background: #ff6a6a;
  color: #fff
}

.multiselect__option--selected.multiselect__option--highlight:after {
  background: #ff6a6a;
  content: attr(data-deselect);
  color: #fff
}

.multiselect--disabled {
  background: #ededed;
  pointer-events: none
}

.multiselect--disabled .multiselect__current,
.multiselect--disabled .multiselect__select,
.multiselect__option--disabled {
  background: #ededed;
  color: #a6a6a6
}

.multiselect__option--disabled {
  cursor: text;
  pointer-events: none
}

.multiselect__option--disabled.multiselect__option--highlight {
  background: #dedede!important
}

.multiselect-enter-active,
.multiselect-leave-active {
  transition: all .15s ease
}

.multiselect-enter,
.multiselect-leave-active {
  opacity: 0
}

@keyframes a {
  0% {
    transform: rotate(0)
  }
  to {
    transform: rotate(2turn)
  }
}
</style>
