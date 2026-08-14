<template>
  <section class="hero">

    <!-- BACKGROUND VIDEO -->
    <div class="video">
      <iframe
        src="https://www.youtube.com/embed/rutCVOOj4KQ?autoplay=1&mute=1&controls=0&loop=1&playlist=rutCVOOj4KQ&rel=0&modestbranding=1&playsinline=1"
        title="Odiliya Premier"
        frameborder="0"
        allow="autoplay; encrypted-media"
      ></iframe>
    </div>

    <!-- OVERLAY -->
    <div class="shade"></div>


    <!-- =========================
         HEADER
    ========================== -->
    <header class="hero-header">

      <div class="header-inner">

        <a href="#" class="brand">
          LUXURY ESTATE
        </a>

        <nav class="header-nav">

          <a href="#residences">Residences</a>
          <a href="#locations">Locations</a>
          <a href="#investment">Investment</a>
          <a href="#contact">Contact</a>

          <span class="nav-divider"></span>

          <button class="globe" type="button">
            <svg viewBox="0 0 24 24">
              <circle cx="12" cy="12" r="9" />
              <path d="M3 12h18" />
              <path d="M12 3c2.4 2.5 3.6 5.5 3.6 9S14.4 18.5 12 21" />
              <path d="M12 3c-2.4 2.5-3.6 5.5-3.6 9S9.6 18.5 12 21" />
            </svg>
          </button>

          <span class="currency">
            USD
          </span>

          <button class="profile" type="button">
            OP
          </button>

        </nav>


        <button
          class="mobile-toggle"
          type="button"
          @click="menuOpen = !menuOpen"
        >
          <span></span>
          <span></span>
        </button>

      </div>


      <div
        class="mobile-menu"
        :class="{ open: menuOpen }"
      >
        <a href="#residences">Residences</a>
        <a href="#locations">Locations</a>
        <a href="#investment">Investment</a>
        <a href="#contact">Contact</a>
      </div>

    </header>



    <!-- =========================
         HERO CONTENT
    ========================== -->
    <div class="inner">

      <p class="hero-kicker">
        LUXURY RESIDENCES · SRI LANKA
      </p>

      <h1>
        Find Your Home
      </h1>

      <p class="desc">
        Discover exceptional apartments in Sri Lanka's most desirable
        locations, thoughtfully selected  living.
      </p>


      <!-- SEARCH -->
      <div class="search">


        <!-- TABS -->
        <div class="tabs">

          <button
            v-for="t in tabs"
            :key="t"
            type="button"
            :class="{ on: active === t }"
            @click="active = t"
          >
            {{ t }}
          </button>

        </div>


        <!-- SEARCH FORM -->
        <form @submit.prevent>

          <label>

            <span class="field-title">
              Property Type
            </span>

            <select>
              <option>Select Property Type</option>
              <option>Luxury Apartment</option>
              <option>Penthouse</option>
            </select>

          </label>


          <label>

            <span class="field-title">
              Location
            </span>

            <select>
              <option>Select Location</option>
              <option>Colombo</option>
              <option>Colombo 03</option>
              <option>Colombo 07</option>
              <option>Galle</option>
              <option>Thalpe</option>
            </select>

          </label>


          <label>

            <span class="field-title">
              Price Range
            </span>

            <select>
              <option>Min. Price - Max. Price</option>
              <option>USD 250K – 500K</option>
              <option>USD 500K – 750K</option>
              <option>USD 750K+</option>
            </select>

          </label>


          <button
            class="go"
            type="submit"
          >
            Search
          </button>

        </form>


        <!-- POPULAR SEARCH -->
        <div class="quick">

          <span>
            Popular Search:
          </span>

          <button type="button">
            Luxury Apartment
          </button>

          <button type="button">
            Penthouse
          </button>

          <button type="button">
            Ocean View
          </button>

          <button type="button">
            Colombo 03
          </button>

        </div>

      </div>

    </div>

  </section>
</template>


<script setup>
import { ref } from "vue";

const tabs = [
  "Buy",
  "Rent",
  "Sell"
];

const active = ref("Buy");

const menuOpen = ref(false);
</script>


<style scoped>

/* =========================================================
   HERO
========================================================= */

.hero {
  width: 100%;
  height: 100vh;
  min-height: 720px;

  position: relative;
  overflow: hidden;

  display: grid;
  place-items: center;

  background: #111111;
  color: #ffffff;
}


/* =========================================================
   VIDEO
========================================================= */

.video {
  position: absolute;
  inset: 0;
  overflow: hidden;
}

.video iframe {
  position: absolute;

  top: 50%;
  left: 50%;

  width: 177.78vh;
  min-width: 100%;

  height: 56.25vw;
  min-height: 100%;

  transform: translate(-50%, -50%);

  pointer-events: none;
}


/* =========================================================
   OVERLAY
========================================================= */

.shade {
  position: absolute;
  inset: 0;
  z-index: 1;

  background:
    linear-gradient(
      180deg,
      rgba(0, 0, 0, 0.42) 0%,
      rgba(0, 0, 0, 0.14) 42%,
      rgba(0, 0, 0, 0.22) 65%,
      rgba(0, 0, 0, 0.42) 100%
    );
}


/* =========================================================
   HEADER
========================================================= */

.hero-header {
  position: absolute;

  top: 0;
  left: 0;

  width: 100%;

  z-index: 20;
}

.header-inner {
  width: min(91vw, 1550px);

  min-height:
    clamp(
      68px,
      7.5vh,
      82px
    );

  margin: 0 auto;

  display: flex;

  align-items: center;
  justify-content: space-between;

  gap: 2rem;
}


/* =========================================================
   LOGO
========================================================= */

.brand {
  min-height: 39px;

  padding:
    0
    clamp(
      0.85rem,
      1.1vw,
      1.15rem
    );

  display: inline-flex;

  align-items: center;

  border:
    1px solid
    rgba(255, 255, 255, 0.9);

  border-radius: 100px;

  color: #ffffff;

   font-family:
    sans-serif;

  font-size:
    clamp(
      1rem,
      1.15vw,
      1.35rem
    );

  font-weight: 400;

  line-height: 1;

  letter-spacing: 0.04em;

  text-decoration: none;

  white-space: nowrap;
}


/* =========================================================
   NAVIGATION
========================================================= */

.header-nav {
  display: flex;

  align-items: center;

  gap:
    clamp(
      1rem,
      1.6vw,
      1.7rem
    );
}

.header-nav a {
  color:
    rgba(255, 255, 255, 0.95);

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.68rem,
      10.72vw,
      0.9rem
    );

  font-weight: 500;

  line-height: 1;

  text-decoration: none;

  transition:
    opacity 0.3s ease;
}

.header-nav a:hover {
  opacity: 0.65;
}

.nav-divider {
  width: 1px;
  height: 22px;

  background:
    rgba(255, 255, 255, 0.5);
}


/* =========================================================
   GLOBE
========================================================= */

.globe {
  width: 29px;
  height: 29px;

  padding: 0;

  display: grid;
  place-items: center;

  border: 0;

  background: transparent;

  color: #ffffff;

  cursor: pointer;
}

.globe svg {
  width: 20px;
  height: 20px;

  fill: none;

  stroke: currentColor;

  stroke-width: 1.3;
}


/* =========================================================
   CURRENCY
========================================================= */

.currency {
  color: #ffffff;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.67rem,
      0.7vw,
      0.78rem
    );

  font-weight: 500;
}


/* =========================================================
   PROFILE
========================================================= */

.profile {
  width: 36px;
  height: 36px;

  display: grid;
  place-items: center;

  border:
    1px solid
    rgba(255, 255, 255, 0.55);

  border-radius: 50%;

  background:
    rgba(17, 17, 17, 0.45);

  color: #ffffff;

   font-family:
    sans-serif;

  font-size: 0.64rem;

  cursor: pointer;
}


/* =========================================================
   MOBILE MENU BUTTON
========================================================= */

.mobile-toggle {
  display: none;

  width: 36px;
  height: 36px;

  padding: 0;

  border: 0;

  background: transparent;

  cursor: pointer;
}

.mobile-toggle span {
  display: block;

  width: 21px;
  height: 1px;

  margin: 5px auto;

  background: #ffffff;
}

.mobile-menu {
  display: none;
}


/* =========================================================
   MAIN HERO CONTENT
========================================================= */

.inner {
  position: relative;

  z-index: 5;

  width: min(
    90vw,
    1100px
  );

  text-align: center;

  transform:
    translateY(-1vh);
}


/* =========================================================
   SMALL TOP TEXT
========================================================= */

.hero-kicker {
  margin:
    0
    0
    0.55rem;

  color:
    rgba(255, 255, 255, 0.88);

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.62rem,
      7.57vw,
      0.65rem
    );

  font-weight: 500;

  line-height: 1.3;

  letter-spacing: 0.22em;

  text-transform: uppercase;
}


/* =========================================================
   MAIN TITLE
========================================================= */

h1 {
  margin: 0;

  color: #ffffff;

   font-family:
    sans-serif;

  font-size:
    clamp(
      3rem,
      3.9vw,
      4.8rem
    );

  font-weight: 400;

  line-height: 1.06;

  letter-spacing: -0.015em;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.desc {
  max-width: 610px;

  margin:
    0.75rem
    auto
    clamp(
      1.7rem,
      3vh,
      2.1rem
    );

  color:
    rgba(255, 255, 255, 0.88);

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.6rem,
      5.76vw,
      0.84rem
    );

  font-weight: 400;

  line-height: 1.65;

  letter-spacing: 0.005em;
}


/* =========================================================
   SEARCH CONTAINER
========================================================= */

.search {
  width: min(
    68vw,
    870px
  );

  margin: 0 auto;

  text-align: left;
}


/* =========================================================
   BUY / RENT / SELL
========================================================= */

.tabs {
  display: flex;
}

.tabs button {
  width: 80px;

  height: 42px;

  border: 0;

  background:
    rgba(24, 24, 24, 0.96);

  color: #ffffff;

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.66rem,
      0.7vw,
      0.78rem
    );

  font-weight: 500;

  cursor: pointer;

  transition:
    background 0.3s ease,
    color 0.3s ease;
}

.tabs button:first-child {
  border-radius:
    0.5rem
    0
    0
    0;
}

.tabs button:last-child {
  border-radius:
    0
    0.5rem
    0
    0;
}

.tabs .on {
  background: #ffffff;
  color: #111111;
}


/* =========================================================
   SEARCH FORM
========================================================= */

form {
  display: grid;

  grid-template-columns:
    1fr
    1fr
    1fr
    115px;

  min-height: 76px;

  overflow: hidden;

  background: #ffffff;

  color: #111111;

  border-radius:
    0
    0.65rem
    0.65rem
    0.65rem;

  box-shadow:
    0
    12px
    30px
    rgba(0, 0, 0, 0.13);
}


/* =========================================================
   SEARCH FIELD
========================================================= */

label {
  padding:
    0.8rem
    clamp(
      0.9rem,
      1.1vw,
      1.15rem
    );

  display: flex;

  flex-direction: column;

  justify-content: center;

  border-right:
    1px solid
    #e8e8e8;
}


/* =========================================================
   FIELD TITLE
========================================================= */

.field-title {
  color: #111111;

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.66rem,
      0.8vw,
      0.78rem
    );

  font-weight: 600;

  line-height: 1.3;

  letter-spacing: 0.005em;
}


/* =========================================================
   SELECT TEXT
========================================================= */

select {
  width: 100%;

  margin-top: 0.38rem;

  border: 0;
  outline: none;

  background: transparent;

  color: #777777;

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.62rem,
      0.76vw,
      0.74rem
    );

  font-weight: 400;

  line-height: 1.5;

  cursor: pointer;
}


/* =========================================================
   SEARCH BUTTON
========================================================= */

.go {
  margin: 7px;

  border: 0;

  border-radius: 7px;

  background: #111111;

  color: #ffffff;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.68rem,
      0.72vw,
      0.8rem
    );

  font-weight: 600;

  letter-spacing: 0.01em;

  cursor: pointer;

  transition:
    background 0.3s ease,
    transform 0.3s ease;
}

.go:hover {
  background: #292929;
}


/* =========================================================
   POPULAR SEARCH
========================================================= */

.quick {
  display: flex;

  align-items: center;
  justify-content: center;

  flex-wrap: wrap;

  gap:
    clamp(
      0.4rem,
      0.55vw,
      0.6rem
    );

  margin-top:
    clamp(
      0.75rem,
      1.4vh,
      1rem
    );

  color:
    rgba(255, 255, 255, 0.9);

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.8rem,
      0.94vw,
      0.72rem
    );

  font-weight: 500;
}

.quick button {
  padding:
    0.38rem
    0.72rem;

  border:
    1px solid
    rgba(255, 255, 255, 0.25);

  border-radius: 0.3rem;

  background: #ffffff;

  color: #111111;

   font-family:
    sans-serif;

  font-size:
    clamp(
      0.58rem,
      0.72vw,
      0.7rem
    );

  font-weight: 400;

  cursor: pointer;

  transition:
    background 0.25s ease,
    transform 0.25s ease;
}

.quick button:hover {
  background: #eeeeee;

  transform:
    translateY(-1px);
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 900px) {

  .header-nav {
    display: none;
  }

  .mobile-toggle {
    display: block;
  }

  .mobile-menu {
    width: 91vw;

    margin: 0 auto;

    padding: 1rem;

    background:
      rgba(10, 10, 10, 0.96);
  }

  .mobile-menu.open {
    display: flex;

    flex-direction: column;

    gap: 1rem;
  }

  .mobile-menu a {
    color: #ffffff;

    font-family:
    sans-serif;

    font-size: 0.78rem;

    text-decoration: none;
  }

  .search {
    width: 88vw;
  }

  form {
    grid-template-columns:
      1fr
      1fr;
  }

  .go {
    grid-column:
      1 / -1;

    min-height: 46px;
  }
}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 560px) {

  .hero {
    min-height: 870px;
  }

  .header-inner {
    width: 92vw;
  }

  .brand {
    min-height: 35px;

    padding:
      0
      0.75rem;

    font-size: 0.9rem;
  }

  .inner {
    width: 92vw;

    transform: none;
  }

  .hero-kicker {
    font-size: 0.5rem;

    letter-spacing: 0.18em;
  }

  h1 {
    font-size:
      clamp(
        2.7rem,
        11vw,
        3.5rem
      );

    line-height: 1.05;
  }

  .desc {
    width: 92%;

    font-size: 0.68rem;

    line-height: 1.6;

    margin-bottom: 1.6rem;
  }

  .search {
    width: 100%;
  }

  .tabs button {
    width: 72px;

    height: 39px;

    font-size: 0.66rem;
  }

  form {
    grid-template-columns: 1fr;
  }

  label {
    min-height: 64px;

    padding:
      0.72rem
      0.9rem;
  }

  .field-title {
    font-size: 0.68rem;
  }

  select {
    font-size: 0.64rem;
  }

  .go {
    grid-column: auto;

    min-height: 46px;

    font-size: 0.7rem;
  }

  .quick {
    margin-top: 0.8rem;

    font-size: 0.62rem;
  }

  .quick span {
    width: 100%;

    text-align: center;
  }

  .quick button {
    font-size: 0.6rem;

    padding:
      0.36rem
      0.65rem;
  }
}

</style>