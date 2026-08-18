<template>
  <section class="places">

    <div class="shell">

      <!-- =========================
           HEADER
      ========================== -->
      <div class="section-head">

        <div class="heading-left">

   <p class="eyebrow">
  EXPLORE PROPERTY TYPES
</p>

<h2>
  Find the way you want to live.
</h2>

        </div>


        <div class="heading-right">

          <p>
            Discover distinctive neighbourhoods, coastal escapes
            and connected city addresses selected for refined
            modern living.
          </p>

          <a href="#">
            Explore all locations
            <span>→</span>
          </a>

        </div>

      </div>

    </div>


    <!-- =========================
         LOCATION PANELS
    ========================== -->
    <div class="location-row">

      <a
        v-for="(area, index) in areas"
        :key="area.name"
        href="#"
        class="location-card"
      >

        <!-- IMAGE -->
        <img
          :src="area.img"
          :alt="area.name"
        />


        <!-- DARK OVERLAY -->
        <div class="overlay"></div>


        <!-- NUMBER -->
        <span class="index">
          0{{ index + 1 }}
        </span>


        <!-- CONTENT -->
        <div class="location-copy">

          <span class="location-type">
            {{ area.type }}
          </span>


          <h3>
            {{ area.name }}
          </h3>


          <div class="location-bottom">

            <p>
              {{ area.description }}
            </p>


            <span class="view-link">
              Explore Properties

              <i>
                →
              </i>
            </span>

          </div>

        </div>

      </a>

    </div>

  </section>
</template>


<script setup>
const areas = [

  {
    name: "Apartments",

    type:
      "URBAN LIVING",

    description:
      "Contemporary apartments designed for connected city living and everyday comfort.",

    img:
      "src/images/Colombo.jpeg"
  },


  {
    name: "Hotels",

    type:
      "HOSPITALITY",

    description:
      "Premium hospitality properties positioned in distinctive leisure and city destinations.",

    img:
      "src/images/Galle.webp"
  },


  {
    name: "Private Houses",

    type:
      "PRIVATE LIVING",

    description:
      "Distinctive private homes shaped around space, privacy and refined modern living.",

    img:
      "src/images/mirissa.webp"
  },


  {
    name: "Beachside Homes",

    type:
      "COASTAL LIVING",

    description:
      "Exceptional residences positioned close to the ocean for relaxed coastal lifestyles.",

    img:
      "src/images/Thalpe.webp"
  },


  {
    name: "Luxury Villas",

    type:
      "EXCLUSIVE LIVING",

    description:
      "Private luxury villas combining generous spaces, premium amenities and distinctive surroundings.",

    img:
      "src/images/weligama.webp"
  }

];
</script>


<style scoped>

/* =========================================================
   GLOBAL
========================================================= */

.places,
.places *,
.places *::before,
.places *::after {
  box-sizing: border-box;

  font-family: sans-serif;
}


/* =========================================================
   SECTION
========================================================= */

.places {
  width: 100%;

  padding:
    clamp(4rem, 7vh, 6rem)
    0
    0;

  background: #0b0b0b;

  color: #ffffff;

  overflow: hidden;
}


.shell {
  width:
    min(94vw, 1650px);

  margin:
    0 auto;
}


/* =========================================================
   HEADER
========================================================= */

.section-head {
  display: grid;

  grid-template-columns:
    1fr
    0.75fr;

  align-items: end;

  gap:
    clamp(3rem, 8vw, 9rem);

  padding-bottom:
    clamp(2rem, 4vh, 3rem);
}


.eyebrow {
  margin:
    0
    0
    9px;

  color: #9d7e46;

  font-size:
    clamp(
      10px,
      0.68vw,
      12px
    );

  font-weight: 700;

  letter-spacing: 0.18em;

  line-height: 1.4;

  text-transform: uppercase;
}


.heading-left h2 {
 
  margin: 0;

  color: #ffffff;

  font-size:
    clamp(
      32px,
      2.35vw,
      44px
    );

  font-weight: 400;

  line-height: 1.15;

  letter-spacing: -0.035em;
}

/* =========================================================
   HEADER RIGHT
========================================================= */

.heading-right {
  max-width: 520px;

  justify-self: end;
}


.heading-right p {
  margin: 0;

  color:
    rgba(
      255,
      255,
      255,
      0.52
    );

   font-size:
    clamp(
      13px,
      0.82vw,
      15px
    );



  line-height: 1.65;
}


.heading-right a {
  width: fit-content;

  display: inline-flex;

  align-items: center;

  gap: 0.75rem;

  margin-top: 1.1rem;

  padding-bottom: 0.25rem;

  border-bottom:
    1px solid
    rgba(
      255,
      255,
      255,
      0.45
    );

  color: #ffffff;

  font-size:
    clamp(10px, 0.44vw, 9px);

  font-weight: 700;

  letter-spacing: 0.08em;

  text-decoration: none;

  text-transform: uppercase;
}


.heading-right a span {
  transition:
    transform 0.3s ease;
}


.heading-right a:hover span {
  transform:
    translateX(4px);
}


/* =========================================================
   LOCATION ROW
========================================================= */

.location-row {
  width: 100%;

  display: flex;

  overflow: hidden;

  border-top:
    1px solid
    rgba(
      255,
      255,
      255,
      0.12
    );

  border-bottom:
    1px solid
    rgba(
      255,
      255,
      255,
      0.12
    );
}


/* =========================================================
   LOCATION CARD
========================================================= */

.location-card {
  position: relative;

  flex:
    1 1 20%;

  min-width: 0;

  height:
    clamp(
      420px,
      55vh,
      610px
    );

  overflow: hidden;

  color: #ffffff;

  text-decoration: none;

  border-right:
    1px solid
    rgba(
      255,
      255,
      255,
      0.18
    );

  transition:
    flex
    0.75s
    cubic-bezier(
      0.22,
      1,
      0.36,
      1
    );
}


.location-card:last-child {
  border-right: 0;
}


/* =========================================================
   EXPANDING HOVER
========================================================= */

.location-row:hover
.location-card {
  flex:
    0.88 1 17%;
}


.location-row
.location-card:hover {
  flex:
    1.65 1 28%;
}


/* =========================================================
   IMAGE
========================================================= */

.location-card img {
  width: 100%;

  height: 100%;

  display: block;

  object-fit: cover;

  filter:
    saturate(0.78)
    brightness(0.78);

  transform:
    scale(1.015);

  transition:
    transform
    0.9s
    cubic-bezier(
      0.22,
      1,
      0.36,
      1
    ),
    filter
    0.6s ease;
}


.location-card:hover img {
  transform:
    scale(1.065);

  filter:
    saturate(0.95)
    brightness(0.9);
}


/* =========================================================
   OVERLAY
========================================================= */

.overlay {
  position: absolute;

  inset: 0;

  background:
    linear-gradient(
      180deg,
      rgba(0, 0, 0, 0.04) 20%,
      rgba(0, 0, 0, 0.16) 52%,
      rgba(0, 0, 0, 0.84) 100%
    );

  transition:
    background 0.5s ease;
}


.location-card:hover
.overlay {
  background:
    linear-gradient(
      180deg,
      rgba(0, 0, 0, 0.02) 18%,
      rgba(0, 0, 0, 0.08) 48%,
      rgba(0, 0, 0, 0.78) 100%
    );
}


/* =========================================================
   INDEX NUMBER
========================================================= */

.index {
  position: absolute;

  z-index: 3;

  top:
    clamp(
      1rem,
      1.4vw,
      1.4rem
    );

  right:
    clamp(
      1rem,
      1.3vw,
      1.3rem
    );

  color:
    rgba(
      255,
      255,
      255,
      0.5
    );

  font-size:
    clamp(8px, 0.44vw, 9px);

  font-weight: 600;

  letter-spacing: 0.12em;
}


/* =========================================================
   CARD CONTENT
========================================================= */

.location-copy {
  position: absolute;

  z-index: 4;

  left:
    clamp(
      1.1rem,
      1.5vw,
      1.6rem
    );

  right:
    clamp(
      1.1rem,
      1.5vw,
      1.6rem
    );

  bottom:
    clamp(
      1.1rem,
      1.6vw,
      1.7rem
    );

  transition:
    transform
    0.5s
    cubic-bezier(
      0.22,
      1,
      0.36,
      1
    );
}


.location-card:hover
.location-copy {
  transform:
    translateY(-7px);
}


/* =========================================================
   TYPE
========================================================= */

.location-type {
  display: block;

  margin-bottom: 0.45rem;

  color:
    rgba(
      255,
      255,
      255,
      0.56
    );

  font-size:
    clamp(9px, 0.40vw, 8px);

  font-weight: 700;

  letter-spacing: 0.15em;

  text-transform: uppercase;
}


/* =========================================================
   LOCATION NAME
========================================================= */

.location-copy h3 {
  margin: 0;

  color: #ffffff;

  font-size:
    clamp(
      20px,
      2.35vw,
      25px
    );

  font-weight: 450;

  line-height: 1;

  letter-spacing: -0.03em;
}


/* =========================================================
   BOTTOM DETAILS
========================================================= */

.location-bottom {
  max-height: 0;

  overflow: hidden;

  opacity: 0;

  transform:
    translateY(12px);

  transition:
    max-height 0.55s ease,
    opacity 0.4s ease,
    transform 0.5s ease;
}


.location-card:hover
.location-bottom {
  max-height: 150px;

  opacity: 1;

  transform:
    translateY(0);
}


.location-bottom p {
  max-width: 280px;

  margin:
    0.65rem
    0
    0.8rem;

  color:
    rgba(
      255,
      255,
      255,
      0.6
    );

  font-size:
    clamp(13px, 0.54vw, 11px);

  line-height: 1.5;
}


/* =========================================================
   VIEW LINK
========================================================= */

.view-link {
  width: fit-content;

  display: inline-flex;

  align-items: center;

  gap: 0.6rem;

  padding-bottom: 0.2rem;

  border-bottom:
    1px solid
    rgba(
      255,
      255,
      255,
      0.72
    );

  color: #ffffff;

  font-size:
    clamp(7px, 0.43vw, 9px);

  font-weight: 700;

  letter-spacing: 0.08em;

  text-transform: uppercase;
}


.view-link i {
  font-style: normal;

  transition:
    transform 0.3s ease;
}


.location-card:hover
.view-link i {
  transform:
    translateX(4px);
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 950px) {

  .section-head {
    grid-template-columns:
      1fr;

    gap: 1.5rem;
  }


  .heading-right {
    justify-self: start;
  }


  .location-row {
    display: grid;

    grid-template-columns:
      repeat(
        2,
        minmax(0, 1fr)
      );
  }


  .location-card,
  .location-row:hover
  .location-card,
  .location-row
  .location-card:hover {
    flex: none;
  }


  .location-card {
    height:
      clamp(
        380px,
        50vh,
        520px
      );
  }


  .location-bottom {
    max-height: 150px;

    opacity: 1;

    transform: none;
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 560px) {

  .heading-right p {
    font-size: 12px;
    line-height: 1.65;
  }

  .heading-right a {
    font-size: 9px;
  }

  .location-type {
    font-size: 8px;
  }

  .location-bottom p {
    font-size: 10px;
    line-height: 1.55;
  }

  .view-link {
    font-size: 9px;
  }



  .places {
    padding-top:
      3rem;
  }


  .shell {
    width:
      91vw;
  }


  .heading-left h2 {
    font-size:
      clamp(25px, 7.5vw, 32px);
  }


  .location-row {
    grid-template-columns:
      1fr;
  }


  .location-card {
    height:
      clamp(
        390px,
        68vh,
        520px
      );
  }


  .location-copy h3 {
    font-size:
      21px;
  }

}
</style>