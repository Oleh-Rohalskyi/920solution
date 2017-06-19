<template>
  <div class="contact">
    <div class="contact__title">Feel free to drop us a line at hi@cre8egy.com</div>
    <div class="contact__form">
      <div class="contact__input">
        <label for="email-contact-input">YOUR EMAIL</label>
        <input id="email-contact-input" type="text" />
      </div>
      <div class="contact__input">
        <label for="budget-contact-input">YOUR APPROXIMATE BUDGET</label>
        <multiselect id="budget-contact-input" 
          v-model="form.budget" 
          track-by="library" 
          :options="content" 
          :multiple="false" 
          :custom-label="customLabel">
        </multiselect>
      </div>
      <div class="contact__input">
        <label for="discription-contact-input">QUICK DESCRIPTION OF YOUR PROJECT</label>
        <textarea v-model="form.discription" id="discription-contact-input"></textarea>
      </div>
      <button class="contact__submit">
        GET A QUOTE
      </button>
    </div>
  </div>
</template>

<script>
import Multiselect from 'vue-multiselect'

export default {
  name: 'contact-form',
  props: ['content'],
  components: {
    Multiselect
  },
  data () {
    return {
      form: {
        discription: '',
        email: '',
        budget: ''
      }
    }
  },
  methods: {
    customLabel (option) {
      return option.text
    }
  }
}
</script>

<style lang="scss" scoped>
.contact {
  margin: 8%;
  &__submit {
    cursor: pointer;
    display: block;
    border: none;
    margin: 23px auto;
    width: 174px;
    height: 48px;
    background-color: #ffffff;
    font-family: "FuturaPTMedium";
    white-space: nowrap;
    font-size: 14px;
    letter-spacing: 2px;
    text-align: center;
    color: #89243c;
  }
  &__title {
    font-family: 'Playfair Display', serif;
    font-size: 36px;
    line-height: 1.44;
    color: #ffffff;
  }
  &__form {
    width: 420px;
  }
  &__input {
    &>label {
      display: block;
      font-family: "FuturaPTMedium";
      font-size: 14px;
      font-weight: 500;
      letter-spacing: 2px;
      color: #430f1b;
      margin-bottom: 4px;
      margin-top: 20px;
    }
    #email-contact-input {
      position: relative;
      width: 403px;
      height: 50px;
      background-color: #89233c;
      border: none;
      border-radius: 0;
      padding-left: 16px;
      font-family: 'helvetica';
      font-size: 18px;
      color: #ffffff;
      font-weight: 300;
    }
    #discription-contact-input {
      width: 402px;
      height: 246px;
      background-color: #89233c;
      border: none;
      padding-top: 14px;
      padding-left: 16px;
      font-family: 'helvetica';
      font-size: 18px;
      color: #ffffff;
      font-weight: 300;
    }
  }
}
</style>
