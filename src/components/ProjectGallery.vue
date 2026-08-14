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
          contemporary architecture and considered living spaces.
        </p>

      </div>

    </div>


    <!-- =========================
         IMAGE ONLY MARQUEE
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

  "https://images.unsplash.com/photo-1600607687920-4e2a09cf159d?auto=format&fit=crop&w=1200&q=90",

  "https://images.unsplash.com/photo-1600566753086-00f18fb6b3ea?auto=format&fit=crop&w=1200&q=90",

  "https://images.unsplash.com/photo-1600573472550-8090b5e0745e?auto=format&fit=crop&w=1200&q=90",

  "https://images.unsplash.com/photo-1600607687939-ce8a6c25118c?auto=format&fit=crop&w=1200&q=90",

  "https://images.unsplash.com/photo-1600210492486-724fe5c67fb0?auto=format&fit=crop&w=1200&q=90",

  "https://images.unsplash.com/photo-1600585154340-be6161a56a0c?auto=format&fit=crop&w=1200&q=90"

];

</script>


<style scoped>

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


.shell {
  width: min(91vw, 1550px);

  margin: 0 auto;
}


/* =========================================================
   HEADING
========================================================= */

.head {
  max-width: 850px;

  margin:
    0 auto
    clamp(2.5rem, 5vh, 4rem);

  text-align: center;
}


.kicker {
  margin: 0;

  color:
    rgba(255, 255, 255, 0.48);

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.52rem,
      0.58vw,
      0.68rem
    );

  font-weight: 400;

  letter-spacing: 0.18em;

  text-transform: uppercase;
}


.title {
    margin:
    clamp(
      0.45rem,
      0.8vh,
      0.7rem
    )
    0
    0;

font-family:
    sans-serif;


  font-size:
    clamp(
      1.7rem,
      2.1vw,
      4.8rem
    );

  font-weight: 400;

  line-height: 1.76;

  letter-spacing: 0.01em;
}


.description {
  max-width: 650px;

  margin: 0 auto;

  color:
    rgba(255, 255, 255, 0.52);

  font-family:
    sans-serif;


  font-size:
    clamp(
      0.68rem,
      0.76vw,
      0.86rem
    );

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


/* PAUSE WHEN HOVERING */

.marquee:hover .marquee-track {
  animation-play-state: paused;
}


/* =========================================================
   ANIMATION
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
   NO TEXT INSIDE
========================================================= */

.gallery-item {
  width: clamp(300px, 29vw, 500px);

  /* SMALLER IMAGE HEIGHT */
  height: clamp(260px, 34vh, 380px);

  flex-shrink: 0;
  margin: 0;
  position: relative;
  overflow: hidden;
  background: #161616;
}


/* Different widths like reference */

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
    transform 0.8s cubic-bezier(
      0.22,
      1,
      0.36,
      1
    ),
    filter 0.6s ease;
}


/* IMAGE HOVER ONLY */

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


  .head {
    width: 90vw;

    margin-bottom: 2rem;
  }


  .title {
    font-size:
      clamp(
        2.3rem,
        10vw,
        3.3rem
      );
  }


  .description {
    width: 92%;

    font-size: 0.72rem;
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