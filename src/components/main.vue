<template>
  <div class="main">
    <block v-for="(item,key) in blocksConfig" :key="key" :links="links" :blockName="item.name" :colors="{ menu: item.menu.colors, button: item.button.colors }" :block-name="item.name" :logo-src="item.logoSrc" :block-bg="item.background">
  
      <div v-if="item.name == 'header'" id="header" class="header">
        <div class="header__title">
          <p>Hello! We are <span class="header__title_pink">920 solutions</span>, killer creative and result-oriented IT consulting company. We are part of GLCC Solutions consulting firm, which has been providing advises to the governments around the world
            to achieve rapid economic growth and improve public services.</p>
          <p> Here at 920 Solutions we design and develop real world digital solutions, including mobile apps and web applications for business transformation, business restructuring and growth hacking.</p>
          <p>We are creative thinkers, experienced and dedicated team. We go deep insights to understand your business, your challenges and the end-user’s need and, at the same time, we assure fast and flawless execution of each project. We are here 24/7 to
            help your business succeed. You just have to get started with us!</p>
        </div>
      </div>
      <div v-if="item.name == 'psihology'" id="psihology" class="psihology">
        <img src="http://new.ukrea.com.ua/albums/userpics/10001/normal_page-1.png" alt="">
        <div class="psihology__discription">
          <h3>
            We Get the Right Things Done
          </h3>
          <p>
            Our team expertise is broad, and deep. We are not only IT developers, our partners have more than 10 years of hands-on experience in leading complex institutional reforms, including organizational changes and business transformation, business restructuring
            and re-engineering business processes in Georgia, Eastern Europe and Central Asia.
          </p>
          <p>
            Realizing that no processes can be fully re-engineered unless the business strategies are aligned to IT strategy, we conveyed our reforming experience into IT consulting services and established IT development company.
          </p>
          <p>
            We do not only build mobile and web applications, we provide most appropriate digital solutions based on studies of emerging trends, competitors and customer insights. We use user-centered interaction design and scalable software architecture to achieve
            the best outcomes.
          </p>
          <p>
            We make sure that our work streams are transferable to the Client through continues exchange of feedback at each stage of software development. This is our process: We analyze, we work in team, we evolve, we act and we get results.
          </p>
        </div>
      </div>
  
      <div v-if="item.name == 'portfolio'" id="portfolio" class="portfolio">
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
            NamNam team wanted us to develop mobile and web application, which would help them to stand out from hundreds of other dating apps. NamNam provides totally new ways to socialize. The application is not merely dating platform, it provides possibility to meet people, invite others to join in your activities, explore new entertainment places and manage it all in one place with a simple click.
          </p>
          <img src="http://new.ukrea.com.ua/albums/userpics/10001/phones.png" alt="">
        </div>
        <div class="portfolio__button">
          EXPLORE ENTIRE PORTFOLIO
        </div>
      </div>
  
      <div v-if="item.name == 'services'" id="services" class="services">
        <div class="services__block">
          <div class="services__item">
            <div class="services__top">
              <img src="http://new.ukrea.com.ua/albums/userpics/10001/UX.png" />
              <div class="services__title">Outstanding design & UI/UX</div>
            </div>
            <div class="services__bot">Ideas never come out fully formed. We help you to transform your business ideas into viable solutions through outstanding design and easy-to-use interface, incorporating UI/UX best practices. Our designers are working directly with the Clients to catch their insights and deliver applicable and relevant final product. We use powerful design prototyping tools to provide Clients with clickable and interactive prototypes. This approach enables them to better visualize the end result.   </div>
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
          <a hid="#">portfolio</a> for taste of what we do.
          <div class="services__line"></div>
        </div>
      </div>
  
      <team v-if="item.name === 'team'" id="team" :content="item.content" />
  
      <contact-form v-if="item.name === 'contact'" id="contact" :content="item.content" />
  
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
    created () {
      this.links = this.linksMap()
    },
    components: {
      block,
      contactForm,
      team
    },
    data () {
      return {
        blocksConfig,
        links: ''
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
