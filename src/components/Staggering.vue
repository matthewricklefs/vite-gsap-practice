<script setup>
import { gsap, Expo } from "gsap";
defineProps({});

document.addEventListener("DOMContentLoaded", function (event) {
  let tl = gsap.timeline({ Defaults: { Easing: Expo.EaseOut } });

  tl.from(".bg", {
    scale: 0.6,
    duration: 2,
    opacity: 0,
    ease: Expo.easeOut,
    delay: 0.2,
  })
    .to(
      ".text-reveal",
      {
        clipPath: "polygon(0 0, 100% 0, 100% 100%, 0 100%)",
        y: 0,
        stagger: 0.3,
        duration: 1,
      },
      "-=2.9"
    )
    .to(".text-reveal", {
      clipPath: "polygon(0 0, 100% 0, 100% 0, 0 0)",
      y: -200,
      duration: 0.2,
      delay: 0.5,
    })
    .to(".text-reveal", {
      clipPath: "polygon(0 0, 100% 0, 100% 100%, 0 100%)",
      stagger: 0.3,
      duration: 0.3,
      delay: 0.5,
    })
    .to("svg", { clipPath: "polygon(0 0, 100% 0, 100% 100%, 0 100%)", y: -150 })
    .to(
      ".local",
      {
        clipPath: "polygon(0 0, 100% 0, 100% 100%, 0 100%)",
        y: 0,
        stagger: 0.3,
        opacity: 1,
        duration: 1,
      },
      "-=1.4"
    );
});
</script>

<template>
  <div class="bg"></div>

  <div class="container">
    <div class="content">
      <div class="content-inner">
        <h1 class="text-reveal">Find your beach</h1>
        <p class="text-reveal">
          Spend 14 nights in the world's most luxurious locations.
        </p>
      </div>

      <svg viewBox="0 0 24 122" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M10.9393 121.061C11.5251 121.646 12.4749 121.646 13.0607 121.061L22.6066 111.515C23.1924 110.929 23.1924 109.979 22.6066 109.393C22.0208 108.808 21.0711 108.808 20.4853 109.393L12 117.879L3.51471 109.393C2.92893 108.808 1.97918 108.808 1.39339 109.393C0.807607 109.979 0.807607 110.929 1.39339 111.515L10.9393 121.061ZM10.5 -6.55671e-08L10.5 120L13.5 120L13.5 6.55671e-08L10.5 -6.55671e-08Z"
          fill="white"
        />
      </svg>
    </div>
  </div>

  <div class="locations-container">
    <div class="local">
      <img src="../assets/unsplash1.jpg" alt="Sand and ocean" />
      <div class="info">
        <p class="title">Los<span>Alacos</span></p>
        <p>
          Pellentesque aliquam et fermentum odio ultricies nibh dolor massa.
          Malesuada magna amet suscipit netus nisl ullamcorper.
        </p>
      </div>
    </div>
    <div class="local">
      <img src="../assets/unsplash2.jpg" alt="Sand and ocean" />
      <div class="info">
        <p class="title">Los<span>Alacos</span></p>
        <p>
          Pellentesque aliquam et fermentum odio ultricies nibh dolor massa.
          Malesuada magna amet suscipit netus nisl ullamcorper.
        </p>
      </div>
    </div>
    <div class="local">
      <img src="../assets/unsplash3.jpg" alt="Sand and ocean" />
      <div class="info">
        <p class="title">Los<span>Alacos</span></p>
        <p>
          Pellentesque aliquam et fermentum odio ultricies nibh dolor massa.
          Malesuada magna amet suscipit netus nisl ullamcorper.
        </p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
body {
  margin: 0;
  font-family: "Playfair Display";
  height: 100vh;
  background: black;
  overflow: hidden;
}

.bg {
  height: 100vh;
  background-image: url("https://assets.codepen.io/2621168/background.jpg");
  background-size: cover;
}

svg {
  width: 1em;
  margin: 2em auto;
  display: block;
  clip-path: polygon(0 0, 100% 0, 100% 0, 0 0);
}

.container {
  position: absolute;
  top: 0;
  height: 100vh;
  width: 100%;
  display: grid;
  place-content: center;
}

.content {
  color: white;
  text-align: center;

  h1 {
    font-size: 4rem;
    margin-bottom: 0;
    font-weight: normal;
  }

  p {
    font-size: 1.3rem;
  }

  .text-reveal {
    clip-path: polygon(0 0, 100% 0, 100% 0, 0 0);
    transition: all 1.5s;
    transform: translateY(-3em);
  }
}

.locations-container {
  position: absolute;
  bottom: 0;
  display: flex;

  .info {
    background: white;
    padding: 3em;
    position: relative;
    margin-top: -0.5em;

    .title {
      font-size: 2rem;
      margin-top: -5.5em;
      margin-bottom: 2.5em;
      font-weight: bold;

      span {
        display: block;
      }
    }
  }
}

.local {
  clip-path: polygon(0 0, 100% 0, 100% 0, 0 0);
  opacity: 0;
  transform: translateY(2em);
}

img {
  width: 100%;
  height: 15em;
  object-fit: cover;
}
</style>
