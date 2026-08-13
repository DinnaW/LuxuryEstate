<template>
  <section class="imap">

    <div class="wrap">

      <!-- =========================
           BACKGROUND IMAGE
      ========================== -->
      <img
        class="map-bg"
        :src="residencesMap"
        alt="Luxury residences across the city"
      />


      <!-- SUBTLE OVERLAY -->
      <div class="veil"></div>


      <!-- =========================
           SECTION HEADING
      ========================== -->
      <div class="heading">

        <p class="kicker">
          LIVE AVAILABILITY
        </p>

        <h2 class="title">
          Residences across
          
          the city.
        </h2>

        <p class="description">
          Explore selected luxury addresses and indicative
          pricing across Sri Lanka's most desirable locations.
        </p>

      </div>


      <!-- =========================
           PRICE PINS
      ========================== -->
      <button
        v-for="p in pins"
        :key="p.name"
        type="button"
        class="map-pin"
        :class="{ selected: selected?.name === p.name }"
        :style="{
          left: p.x,
          top: p.y
        }"
        @click="selected = p"
      >

        <span class="pin-dot"></span>

        <span class="pin-price">
          {{ p.price }}
        </span>

      </button>


      <!-- =========================
           PROPERTY DETAIL CARD
      ========================== -->
      <transition name="card">

        <aside
          v-if="selected"
          class="property-card"
        >

          <button
            class="close"
            type="button"
            @click="selected = null"
          >
            ×
          </button>


          <div
            v-if="selected.image"
            class="property-image"
          >

            <img
              :src="selected.image"
              :alt="selected.name"
            />

          </div>


          <div class="property-content">

            <small>
              {{ selected.area }}
            </small>

            <h3>
              {{ selected.name }}
            </h3>

            <p>
              {{ selected.meta }}
            </p>


            <div class="property-price">
              {{ selected.price }}
            </div>


            <div class="features">

              <span>
                {{ selected.beds }} Bedrooms
              </span>

              <span>
                {{ selected.baths }} Bathrooms
              </span>

            </div>


            <a href="#">
              View residence

              <span>
                →
              </span>
            </a>

          </div>

        </aside>

      </transition>


      <!-- =========================
           LOCATION FILTERS
      ========================== -->
      <div class="location-tabs">

        <button
          v-for="location in locations"
          :key="location.name"
          type="button"
          :class="{ active: activeLocation === location.name }"
          @click="activeLocation = location.name"
        >

          <strong>
            {{ location.name }}
          </strong>

          <span>
            {{ location.count }} residences
          </span>

        </button>

      </div>

    </div>

  </section>
</template>


<script setup>
import { ref } from "vue";


/*
=========================================================
YOUR UPLOADED IMAGE

Put your screenshot/image here:

src/images/residences-map.png
=========================================================
*/

import residencesMap from "../images/map.png";


/*
Optional images for clicked property cards.

You can change these later to your own Odiliya Premier images.
*/

import property1 from "../images/Thalpe.webp";
import property2 from "../images/weligama.webp";
import property3 from "../images/Galle.webp";


const selected = ref(null);

const activeLocation = ref("Colombo");


const pins = [

  {
    x: "17%",
    y: "37%",

    price: "USD 520K",

    area: "Colombo 03",

    name: "Ocean Avenue Residence",

    meta: "2,150 sq.ft",

    beds: 3,

    baths: 2,

    image: property1
  },


  {
    x: "38%",
    y: "24%",

    price: "USD 1.25M",

    area: "Colombo 07",

    name: "The Residence",

    meta: "3,850 sq.ft",

    beds: 4,

    baths: 4,

    image: property2
  },


  {
    x: "48%",
    y: "43%",

    price: "USD 685K",

    area: "Colombo",

    name: "Skyline Heights",

    meta: "2,480 sq.ft",

    beds: 3,

    baths: 3,

    image: property3
  },


  {
    x: "35%",
    y: "63%",

    price: "USD 740K",

    area: "Colombo 03",

    name: "Park Avenue",

    meta: "2,950 sq.ft",

    beds: 3,

    baths: 3,

    image: property1
  },


  {
    x: "63%",
    y: "67%",

    price: "USD 1.48M",

    area: "Colombo 07",

    name: "Premier Penthouse",

    meta: "4,600 sq.ft",

    beds: 4,

    baths: 5,

    image: property2
  },


  {
    x: "79%",
    y: "50%",

    price: "USD 910K",

    area: "Colombo",

    name: "City Garden Residence",

    meta: "3,200 sq.ft",

    beds: 4,

    baths: 3,

    image: property3
  },


  {
    x: "16%",
    y: "79%",

    price: "USD 980K",

    area: "Colombo",

    name: "Lake View Residence",

    meta: "3,600 sq.ft",

    beds: 4,

    baths: 4,

    image: property1
  }

];


const locations = [

  {
    name: "Colombo",
    count: 128
  },

  {
    name: "Colombo 03",
    count: 94
  },

  {
    name: "Colombo 07",
    count: 76
  },

  {
    name: "Galle",
    count: 52
  },

  {
    name: "Thalpe",
    count: 38
  }

];

</script>


<style scoped>

/* =========================================================
   SECTION
========================================================= */

.imap {
  width: 100%;

  padding:
    clamp(1rem, 1.8vw, 1.5rem)
    0;

  background: #111111;
}



/* =========================================================
   IMAGE WRAPPER
========================================================= */

.wrap {
  width:
    min(
      98vw,
      1800px
    );

  height:
    clamp(
      620px,
      82vh,
      900px
    );

  margin:
    0 auto;

  position: relative;

  overflow: hidden;

  background: #111111;
}



/* =========================================================
   BACKGROUND IMAGE
========================================================= */

.map-bg {
  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  object-fit: cover;

  object-position: center;

  filter:
    saturate(0.82)
    contrast(0.96)
    brightness(0.88);

  transform:
    scale(1.01);

  transition:
    transform
    1.2s
    ease;
}


.wrap:hover .map-bg {
  transform:
    scale(1.025);
}



/* =========================================================
   OVERLAY
========================================================= */

.veil {
  position: absolute;

  inset: 0;

  pointer-events: none;

  background:
    linear-gradient(
      90deg,
      rgba(0, 0, 0, 0.52) 0%,
      rgba(0, 0, 0, 0.12) 34%,
      rgba(0, 0, 0, 0.03) 65%,
      rgba(0, 0, 0, 0.12) 100%
    );
}



/* =========================================================
   HEADING
========================================================= */

.heading {
  position: absolute;

  z-index: 5;

  top:
    clamp(
      2rem,
      6vh,
      4.5rem
    );

  left:
    clamp(
      1.5rem,
      4vw,
      5rem
    );

  max-width: 520px;

  color: #ffffff;
}


.kicker {
  margin: 0;

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.48rem,
      0.54vw,
      0.62rem
    );

  font-weight: 400;

  letter-spacing: 0.19em;

  text-transform: uppercase;

  color:
    rgba(
      255,
      255,
      255,
      0.72
    );
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

  line-height: 1.59;

  letter-spacing: 0.01em;
}


.description {
  max-width: 400px;

  margin: 0;

  color:
    rgba(
      255,
      255,
      255,
      0.72
    );

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.62rem,
      0.68vw,
      0.76rem
    );

  line-height: 1.65;
}



/* =========================================================
   MAP PIN
========================================================= */

.map-pin {
  position: absolute;

  z-index: 8;

  transform:
    translate(
      -50%,
      -50%
    );

  display: flex;

  flex-direction: column;

  align-items: center;

  gap: 0.35rem;

  padding: 0;

  border: 0;

  background: transparent;

  cursor: pointer;
}



/* PRICE BUBBLE */

.pin-price {
  padding:
    clamp(
      0.4rem,
      0.5vw,
      0.52rem
    )
    clamp(
      0.65rem,
      0.8vw,
      0.85rem
    );

  border-radius: 100px;

  background: #ffffff;

  color: #111111;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.55rem,
      0.62vw,
      0.7rem
    );

  font-weight: 400;

  white-space: nowrap;

  box-shadow:
    0
    7px
    20px
    rgba(0, 0, 0, 0.22);

  transition:
    transform 0.3s ease,
    background 0.3s ease,
    color 0.3s ease;
}



/* PIN DOT */

.pin-dot {
  width:
    clamp(
      18px,
      1.5vw,
      25px
    );

  height:
    clamp(
      18px,
      1.5vw,
      25px
    );

  border:
    clamp(
      5px,
      0.5vw,
      7px
    )
    solid
    rgba(
      255,
      255,
      255,
      0.75
    );

  border-radius: 50%;

  background: #77736e;

  box-shadow:
    0
    4px
    15px
    rgba(0, 0, 0, 0.2);

  transition:
    background 0.3s ease,
    transform 0.3s ease;
}



/* HOVER */

.map-pin:hover .pin-price {
  background: #111111;

  color: #ffffff;

  transform:
    translateY(-3px);
}


.map-pin:hover .pin-dot {
  background: #111111;

  transform:
    scale(1.12);
}



/* SELECTED */

.map-pin.selected .pin-price {
  background: #111111;

  color: #ffffff;
}


.map-pin.selected .pin-dot {
  background: #111111;
}



/* =========================================================
   PROPERTY CARD
========================================================= */

.property-card {
  position: absolute;

  z-index: 20;

  top:
    clamp(
      3rem,
      7vh,
      5rem
    );

  right:
    clamp(
      1.5rem,
      4vw,
      4rem
    );

  width:
    min(
      300px,
      83vw
    );

  overflow: hidden;

  background: #ffffff;

  color: #111111;

  border-radius:
    clamp(
      0.8rem,
      1vw,
      1rem
    );

  box-shadow:
    0
    25px
    65px
    rgba(0, 0, 0, 0.2);
}



/* =========================================================
   PROPERTY IMAGE
========================================================= */

.property-image {
  width: 100%;

  height:
    clamp(
      130px,
      12vw,
      175px
    );

  overflow: hidden;
}


.property-image img {
  width: 100%;
  height: 100%;

  object-fit: cover;
}



/* =========================================================
   CARD CONTENT
========================================================= */

.property-content {
  padding:
    clamp(
      1rem,
      1.3vw,
      1.3rem
    );
}


.property-content small {
  display: block;

  margin-bottom: 0.35rem;

  color: #88837d;

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.5rem,
      0.55vw,
      0.62rem
    );

  letter-spacing: 0.08em;

  text-transform: uppercase;
}


.property-content h3 {
  margin:
    0
    0
    0.45rem;

    font-family:
    sans-serif;

  font-size:
    clamp(
      1.3rem,
      1.6vw,
      1.8rem
    );

  font-weight: 400;

  line-height: 1.05;
}


.property-content > p {
  margin: 0;

  color: #77736e;

    font-family:
    sans-serif;

  font-size:
    clamp(
      0.58rem,
      0.63vw,
      0.7rem
    );
}



/* =========================================================
   PRICE
========================================================= */

.property-price {
  margin:
    clamp(
      0.8rem,
      1.2vh,
      1rem
    )
    0
    0.65rem;

    font-family:
    sans-serif;

  font-size:
    clamp(
      1.35rem,
      1.8vw,
      2rem
    );

  font-weight: 400;
}



/* =========================================================
   FEATURES
========================================================= */

.features {
  display: flex;

  flex-wrap: wrap;

  gap: 0.45rem;

  margin-bottom: 1rem;
}


.features span {
  padding:
    0.34rem
    0.55rem;

  background: #f1f0ed;

  border-radius: 100px;

  color: #55514d;

    font-family:
    sans-serif;

  font-size:
    clamp(
      0.48rem,
      0.53vw,
      0.59rem
    );
}



/* =========================================================
   CARD LINK
========================================================= */

.property-content > a {
  display: flex;

  align-items: center;

  justify-content: space-between;

  padding-top: 0.8rem;

  border-top:
    1px solid
    #ebe9e5;

  color: #111111;

    font-family:
    sans-serif;

  font-size:
    clamp(
      0.5rem,
      0.56vw,
      0.63rem
    );

  letter-spacing: 0.07em;

  text-decoration: none;

  text-transform: uppercase;
}



/* =========================================================
   CLOSE
========================================================= */

.close {
  position: absolute;

  z-index: 5;

  top: 0.45rem;

  right: 0.55rem;

  width: 27px;
  height: 27px;

  display: grid;

  place-items: center;

  padding: 0;

  border: 0;

  border-radius: 50%;

  background:
    rgba(
      255,
      255,
      255,
      0.9
    );

  color: #111111;

  font-size: 1rem;

  cursor: pointer;
}



/* =========================================================
   LOCATION FILTER
========================================================= */

.location-tabs {
  position: absolute;

  z-index: 12;

  left: 50%;

  bottom:
    clamp(
      1rem,
      3vh,
      2rem
    );

  transform:
    translateX(-50%);

  display: flex;

  align-items: stretch;

  max-width: 92%;

  overflow-x: auto;

  scrollbar-width: none;

  box-shadow:
    0
    15px
    45px
    rgba(0, 0, 0, 0.18);
}


.location-tabs::-webkit-scrollbar {
  display: none;
}


.location-tabs button {
  min-width:
    clamp(
      105px,
      8vw,
      135px
    );

  padding:
    clamp(
      0.6rem,
      0.8vw,
      0.85rem
    );

  border: 0;

  border-right:
    1px solid
    rgba(
      255,
      255,
      255,
      0.15
    );

  background:
    rgba(
      30,
      30,
      30,
      0.74
    );

  backdrop-filter:
    blur(8px);

  color: #ffffff;

  text-align: center;

  cursor: pointer;

  transition:
    background
    0.3s
    ease,
    color
    0.3s
    ease;
}


.location-tabs button:last-child {
  border-right: 0;
}


.location-tabs strong {
  display: block;

    font-family:
    sans-serif;

  font-size:
    clamp(
      0.58rem,
      0.64vw,
      0.72rem
    );

  font-weight: 400;
}


.location-tabs span {
  display: block;

  margin-top: 0.25rem;

  color:
    rgba(
      255,
      255,
      255,
      0.65
    );

    font-family:
    sans-serif;

  font-size:
    clamp(
      0.45rem,
      0.5vw,
      0.56rem
    );
}


.location-tabs button.active {
  background: #ffffff;

  color: #111111;
}


.location-tabs button.active span {
  color: #77736e;
}



/* =========================================================
   TRANSITION
========================================================= */

.card-enter-active,
.card-leave-active {
  transition:
    opacity
    0.3s
    ease,
    transform
    0.3s
    ease;
}


.card-enter-from,
.card-leave-to {
  opacity: 0;

  transform:
    translateY(12px);
}



/* =========================================================
   TABLET
========================================================= */

@media (max-width: 900px) {

  .heading {
    max-width: 400px;
  }


  .property-card {
    width: 270px;
  }

}



/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 600px) {

  .imap {
    padding: 0;
  }


  .wrap {
    width: 100%;

    height: 760px;
  }


  .heading {
    top: 2rem;

    left: 1.2rem;

    right: 1.2rem;
  }


  .title {
    font-size:
      clamp(
        2.2rem,
        11vw,
        3.2rem
      );
  }


  .description {
    max-width: 310px;
  }


  .pin-price {
    font-size: 0.48rem;

    padding:
      0.32rem
      0.48rem;
  }


  .pin-dot {
    width: 16px;

    height: 16px;

    border-width: 4px;
  }


  .property-card {
    top: auto;

    right: 1rem;

    bottom: 7rem;

    left: 1rem;

    width: auto;
  }


  .property-image {
    height: 120px;
  }


  .location-tabs {
    left: 1rem;

    right: 1rem;

    bottom: 1rem;

    transform: none;

    max-width: none;
  }


  .location-tabs button {
    min-width: 110px;
  }

}

</style>