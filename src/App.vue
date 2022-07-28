<template>
  <div style="margin:20px;width:100%;">
    <center>
      <h2>Vue 3 Flip Card Take Home Assignment - Darius</h2>
      <br>
    </center>
    <section class="section-tours">
      <div class="container" style="width:100%;">
        <div class="row">
          <div v-for="(image, index) in my_imgs" :key="index" style="width:20%;">
            <br>
            <div class="my-flip-container">
              <div class="my-flip-inner my-flip-right">
                <div class="my-flip-inner-wrapper">
                  <div class="my-flip-side my-flip-front">
                    <div class="my-flip-image my-flip-image--1">
                      <h2 style="padding-top:20px;" id="header">Header {{ index+1 }}</h2>
                      <img id="body-section" src="./assets/logo.png">
                    </div>
                    <div class="my-flip-details">
                      <h4 class="my-flip-heading">Card Turned Back</h4>
                      <div id="footer-section" class="my-flip-text">
                        <p>Footer: <br>Hover to flip =) <br> </p>
                      </div>
                    </div>
                  </div>
                  <div class="my-flip-side my-flip-back my-flip-back-1">
                    <img style="height:auto;width: 100%;" :src="image">
                    <div class="my-flip-back-inner">
                      <div class="my-flip-price">
                        <h5 style="margin-top: 30px;">Doggie {{ index+1 }}</h5>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
  //Bootstrap
  import 'bootstrap/dist/css/bootstrap.min.css';
  export default {
    data() {
      return {
        imgs: [],
        my_imgs: []
      }
    },
    created() {
      this.fetchData();
    },
    methods: {
      fetchData() {
        fetch('https://dog.ceo/api/breeds/image/random/10').then(res => res.json()).then(data => this.imgs = data).then(data => this.my_imgs = data.message).catch(err => console.log(err.message))
      }
    }
  }
</script>
<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  a:hover {
    text-decoration: none;
  }

  .my-flip-inner-wrapper {
    position: relative;
  }

  .my-flip-side {
    display: block;
    height: fit-content;
    top: 0;
    right: 0;
    left: 0;
    box-shadow: 0 1.5rem 4rem rgba(0, 0, 0, 0.15);
    transition: all .8s ease;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }

  .my-flip-back {
    height: 100%;
    transform: rotateY(180deg);
    color: #fff;
    position: absolute;
    z-index: -1;
    box-shadow: 0 1.5rem 4rem rgba(0, 0, 0, 0.15);
    padding: 46px;
    padding-bottom: 100px !important;
  }

  .my-flip-back-1 {
    background: linear-gradient(to right bottom, #ffb900, #ff7730);
  }

  .my-flip-back-2 {
    background: linear-gradient(to right bottom, #000428, #004e92);
  }

  .my-flip-back-3 {
    background: linear-gradient(to right bottom, #2998ff, #5643fa);
  }

  .my-flip-inner-wrapper:hover .my-flip-front {
    transform: rotateY(-180deg);
  }

  .my-flip-inner-wrapper:hover .my-flip-back {
    transform: rotateY(0);
  }

  .my-flip-image {
    height: 15rem;
    background-blend-mode: screen;
    clip-path: polygon(0 0, 100% 0, 100% 85%, 0 100%);
  }

  .my-flip-image img {
    width: 100%;
    height: fit-content;
    background-blend-mode: screen;
    object-fit: cover;
  }

  .my-flip-heading {
    margin: 0 0 15px;
  }

  .my-flip-details {
    padding: 2rem;
  }

  .my-flip-details p {
    font-size: 15px;
    margin: 0;
    line-height: 2;
    color: #848484;
  }

  .my-flip-back-inner ul {
    list-style: none;
    margin: 0 0 1.5rem;
    padding: 0;
  }

  .my-flip-back-inner ul li:not(:last-child) {
    border-bottom: 1px solid #ffffff;
  }

  .my-flip-price {
    color: #fff;
    text-align: center;
    margin-bottom: 1rem;
  }

  .my-flip-price h3 {
    font-size: 3rem;
    font-weight: 300;
  }

  .my-flip-btn-box {
    text-align: center;
  }

  .my-flip-btn {
    text-transform: uppercase;
    padding: 1rem 1.8rem;
    font-size: 1rem;
    background-color: #fff;
    color: #000;
    border-radius: 10rem;
    display: inline-block;
    transition: all .2s;
    color: initial;
    position: relative;
  }

  .my-flip-btn:hover {
    transform: translateY(-4px);
    box-shadow: 0 1rem 2rem rgba(0, 0, 0, 0.2);
    color: #000;
  }
</style>