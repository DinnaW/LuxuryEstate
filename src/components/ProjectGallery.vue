<template>
  <section class="gallery">

    <!-- =========================
         HEADING
    ========================== -->
    <div class="shell">

      <div class="head">

        <p class="kicker">
          PROJECTS GALLERY
        </p>

        <h2 class="title">
          Captured Elegance
        </h2>

        <p class="description">
          A curated visual collection of refined interiors,
          contemporary architecture, and captivating lifestyle moments,
        </p>

      </div>

    </div>


    <!-- =========================
         IMAGE MARQUEE
    ========================== -->
    <div class="marquee">

      <div class="marquee-track">

        <!-- FIRST SET -->
        <figure
          v-for="(img, index) in images"
          :key="`first-${index}`"
          class="gallery-item"
        >
          <img
            :src="img"
            alt="Odiliya Premier residence"
          />
        </figure>


        <!-- DUPLICATE SET -->
        <figure
          v-for="(img, index) in images"
          :key="`second-${index}`"
          class="gallery-item"
          aria-hidden="true"
        >
          <img
            :src="img"
            alt=""
          />
        </figure>

      </div>

    </div>

  </section>
</template>


<script setup>
const images = [
  "https://i.pinimg.com/736x/7a/37/6f/7a376f13c7fe11bde817fcd70ddb7425.jpg",

  "https://i.pinimg.com/1200x/58/27/02/58270273632a4295a47748abb7160e5e.jpg",

  "https://i.pinimg.com/736x/f9/26/92/f926926fbbd48ff445cf642985355705.jpg",

  "https://i.pinimg.com/736x/d3/59/f3/d359f321a1a7b4ae01b67286afc47c3a.jpg",

  "https://i.pinimg.com/1200x/07/82/ae/0782ae978947f00bf0c6ac8808170822.jpg",

  "https://i.pinimg.com/1200x/cd/cf/e7/cdcfe74e7bdba70e13080c05a833318e.jpg"
];
</script>


<style scoped>

/* =========================================================
   RESET
========================================================= */

.gallery,
.gallery *,
.gallery *::before,
.gallery *::after {
  box-sizing: border-box;
  font-family: sans-serif;
}


/* =========================================================
   SECTION
========================================================= */

.gallery {
  width: 100%;

  padding:
    clamp(4.5rem, 8vh, 7rem)
    0;

  background: #0b0b0b;

  color: #ffffff;

  overflow: hidden;
}


/* =========================================================
   CONTAINER
========================================================= */

.shell {
  width: min(91vw, 1550px);

  margin: 0 auto;
}


/* =========================================================
   HEADING
========================================================= */

.head {
  max-width: 920px;

  margin:
    0 auto
    clamp(2.5rem, 5vh, 4rem);

  text-align: center;
}


/* =========================================================
   KICKER
========================================================= */

.kicker {
  margin:
    0
    0
    10px;

  color: #a4864d;

  font-size:
    clamp(
      13px,
      0.82vw,
      15px
    );

  font-weight: 700;

  line-height: 1.4;

  letter-spacing: 0.18em;

  text-transform: uppercase;
}


/* =========================================================
   TITLE
========================================================= */

.title {
  margin: 0;

  color: #ffffff;

  font-size:
    clamp(
      48px,
      3.4vw,
      64px
    );

  font-weight: 400;

  line-height: 1.12;

  letter-spacing: -0.035em;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.description {
  max-width: 650px;

  margin:
    16px
    auto
    0;

  color:
    rgba(255, 255, 255, 0.58);

  font-size:
    clamp(
      16px,
      1.02vw,
      18px
    );

  font-weight: 400;

  line-height: 1.7;
}


/* =========================================================
   MARQUEE
========================================================= */

.marquee {
  width: 100%;

  position: relative;

  overflow: hidden;
}


.marquee-track {
  width: max-content;

  display: flex;

  align-items: stretch;

  gap:
    clamp(
      0.7rem,
      0.9vw,
      1rem
    );

  animation:
    galleryScroll
    42s
    linear
    infinite;

  will-change: transform;
}


/* =========================================================
   PAUSE ON HOVER
========================================================= */

.marquee:hover .marquee-track {
  animation-play-state: paused;
}


/* =========================================================
   MARQUEE ANIMATION
========================================================= */

@keyframes galleryScroll {

  from {
    transform: translateX(0);
  }

  to {
    transform: translateX(-50%);
  }

}


/* =========================================================
   IMAGE CARDS
========================================================= */

.gallery-item {
  width:
    clamp(
      300px,
      29vw,
      500px
    );

  height:
    clamp(
      260px,
      34vh,
      380px
    );

  flex-shrink: 0;

  margin: 0;

  position: relative;

  overflow: hidden;

  background: #161616;
}


/* =========================================================
   DIFFERENT IMAGE WIDTHS
========================================================= */

.gallery-item:nth-child(5n + 1) {
  width:
    clamp(
      260px,
      22vw,
      370px
    );
}


.gallery-item:nth-child(5n + 2) {
  width:
    clamp(
      380px,
      35vw,
      590px
    );
}


.gallery-item:nth-child(5n + 3) {
  width:
    clamp(
      300px,
      28vw,
      470px
    );
}


.gallery-item:nth-child(5n + 4) {
  width:
    clamp(
      280px,
      25vw,
      420px
    );
}


.gallery-item:nth-child(5n + 5) {
  width:
    clamp(
      330px,
      31vw,
      520px
    );
}


/* =========================================================
   IMAGES
========================================================= */

.gallery-item img {
  width: 100%;
  height: 100%;

  display: block;

  object-fit: cover;

  transition:
    transform
    0.8s
    cubic-bezier(
      0.22,
      1,
      0.36,
      1
    ),
    filter
    0.6s
    ease;
}


/* =========================================================
   IMAGE HOVER
========================================================= */

.gallery-item:hover img {
  transform: scale(1.055);

  filter: brightness(1.05);
}


/* =========================================================
   EDGE FADES
========================================================= */

.marquee::before,
.marquee::after {
  content: "";

  position: absolute;

  z-index: 5;

  top: 0;
  bottom: 0;

  width:
    clamp(
      20px,
      3vw,
      55px
    );

  pointer-events: none;
}


.marquee::before {
  left: 0;

  background:
    linear-gradient(
      90deg,
      #0b0b0b 0%,
      rgba(11, 11, 11, 0) 100%
    );
}


.marquee::after {
  right: 0;

  background:
    linear-gradient(
      270deg,
      #0b0b0b 0%,
      rgba(11, 11, 11, 0) 100%
    );
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 850px) {

  .gallery {
    padding:
      clamp(4rem, 7vh, 5.5rem)
      0;
  }


  .head {
    max-width: 760px;
  }


  .kicker {
    font-size: 12px;
  }


  .title {
    font-size:
      clamp(
        42px,
        6vw,
        56px
      );
  }


  .description {
    max-width: 580px;

    font-size: 16px;
  }


  .gallery-item,
  .gallery-item:nth-child(5n + 1),
  .gallery-item:nth-child(5n + 2),
  .gallery-item:nth-child(5n + 3),
  .gallery-item:nth-child(5n + 4),
  .gallery-item:nth-child(5n + 5) {

    width:
      clamp(
        280px,
        52vw,
        420px
      );

    height:
      clamp(
        360px,
        52vh,
        500px
      );
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 560px) {

  .gallery {
    padding:
      3.8rem
      0;
  }


  .shell {
    width: 90vw;
  }


  .head {
    width: 100%;

    margin-bottom: 2rem;
  }


  .kicker {
    margin-bottom: 8px;

    font-size: 12px;
  }


  .title {
    font-size:
      clamp(
        40px,
        10vw,
        52px
      );

    line-height: 1.12;

    letter-spacing: -0.03em;
  }


  .description {
    width: 94%;

    max-width: 460px;

    margin-top: 14px;

    font-size: 16px;

    line-height: 1.65;
  }


  .marquee-track {
    gap: 0.65rem;

    animation-duration: 48s;
  }


  .gallery-item,
  .gallery-item:nth-child(5n + 1),
  .gallery-item:nth-child(5n + 2),
  .gallery-item:nth-child(5n + 3),
  .gallery-item:nth-child(5n + 4),
  .gallery-item:nth-child(5n + 5) {

    width:
      clamp(
        250px,
        78vw,
        330px
      );

    height:
      clamp(
        340px,
        55vh,
        440px
      );
  }

}


/* =========================================================
   REDUCED MOTION
========================================================= */

@media (prefers-reduced-motion: reduce) {

  .marquee-track {
    animation: none;
  }

}

</style>