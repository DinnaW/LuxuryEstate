<template>
  <section
    class="hero"
    @click="handlePageClick"
  >

    <!-- =====================================================
         BACKGROUND VIDEO
    ====================================================== -->
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


    <!-- =====================================================
         HEADER
    ====================================================== -->
    <header class="hero-header">

      <div class="header-inner">

        <!-- LOGO -->
        <a
          href="#"
          class="brand"
        >
          LUXURY ESTATE
        </a>


        <!-- =================================================
             DESKTOP NAVIGATION
        ================================================== -->
        <nav class="header-nav">

          <a
            href="#value-home"
            class="nav-link"
          >
            Value your home
          </a>


          <!-- ===============================================
               SELL WITH US
          ================================================ -->
          <div
            class="sell-menu"
            @click.stop
          >

            <button
              class="sell-trigger nav-link"
              type="button"
              @click="toggleSeller"
            >
              Sell with us

              <svg
                :class="{ rotate: sellerOpen }"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
              >
                <path d="M6 9l6 6 6-6" />
              </svg>

            </button>


            <transition name="drop">

              <div
                v-if="sellerOpen"
                class="seller-dropdown"
              >

                <a href="#">
                  Professional seller
                  <span>(Agent)</span>
                </a>

                <a href="#">
                  Private seller
                  <span>(Owner)</span>
                </a>

              </div>

            </transition>

          </div>


          <!-- ===============================================
               SETTINGS / CURRENCY
          ================================================ -->
          <button
            class="currency-area"
            type="button"
            @click.stop="openSettings"
          >

            <span class="globe">

              <svg viewBox="0 0 24 24">

                <circle
                  cx="12"
                  cy="12"
                  r="9"
                />

                <path d="M3 12h18" />

                <path
                  d="M12 3c2.4 2.5 3.6 5.5 3.6 9S14.4 18.5 12 21"
                />

                <path
                  d="M12 3c-2.4 2.5-3.6 5.5-3.6 9S9.6 18.5 12 21"
                />

              </svg>

            </span>


            <span class="currency-divider"></span>


            <span class="currency">
              {{ selectedCurrency.code }}
            </span>

          </button>


          <!-- ===============================================
               PROFILE
          ================================================ -->
          <div
            class="profile-wrap"
            @click.stop
          >

            <button
              class="profile"
              type="button"
              @click="toggleProfile"
            >
              N
            </button>


            <transition name="drop">

              <div
                v-if="profileOpen"
                class="profile-menu"
              >

                <a href="#">
                  Home
                </a>

                <a href="#">
                  Edit profile
                </a>

                <a href="#">
                  Saved listings
                </a>

                <a href="#">
                  Hidden listings
                </a>

                <a href="#">
                  Saved searches
                </a>

                <a href="#">
                  Sell home
                </a>

                <a href="#">
                  Value home
                </a>

                <div class="profile-menu-line"></div>

                <a href="#">
                  Log out
                </a>

              </div>

            </transition>

          </div>

        </nav>


        <!-- =================================================
             MOBILE BUTTON
        ================================================== -->
        <button
          class="mobile-toggle"
          type="button"
          @click.stop="menuOpen = !menuOpen"
        >

          <span></span>
          <span></span>

        </button>

      </div>


      <!-- =================================================
           MOBILE MENU
      ================================================== -->
      <div
        class="mobile-menu"
        :class="{ open: menuOpen }"
        @click.stop
      >

        <a href="#value-home">
          Value your home
        </a>


        <button
          type="button"
          class="mobile-sell"
          @click="mobileSellerOpen = !mobileSellerOpen"
        >

          Sell with us

          <span>
            {{ mobileSellerOpen ? "−" : "+" }}
          </span>

        </button>


        <div
          v-if="mobileSellerOpen"
          class="mobile-seller-links"
        >

          <a href="#">
            Professional seller (Agent)
          </a>

          <a href="#">
            Private seller (Owner)
          </a>

        </div>


        <button
          class="mobile-settings"
          type="button"
          @click="openSettings"
        >
          Currency & Settings

          <strong>
            {{ selectedCurrency.code }}
          </strong>
        </button>


        <button
          class="mobile-profile"
          type="button"
          @click="profileOpen = !profileOpen"
        >
          Profile

          <span>N</span>
        </button>

      </div>

    </header>



    <!-- =====================================================
         HERO CONTENT
    ====================================================== -->
    <div class="inner">

      <p class="hero-kicker">
        LUXURY REAL ESTATE · WORLDWIDE
      </p>


      <h1>
         Exceptional Residences
      </h1>


      <p class="desc">
         Discover prestigious properties in the world's
  most sought-after destinations.
      </p>


      <!-- ===================================================
           SEARCH
      ==================================================== -->
      <div class="search">

        <!-- TABS -->
        <div class="tabs">

          <button
            v-for="tab in tabs"
            :key="tab"
            type="button"
            :class="{ on: active === tab }"
            @click="active = tab"
          >
            {{ tab }}
          </button>

        </div>


        <!-- SEARCH FORM -->
        <form @submit.prevent>

          <!-- PROPERTY -->
          <label>

            <span class="field-title">
              Property Type
            </span>

            <select>
              <option>
                Select Property Type
              </option>

              <option>
                Luxury Apartment
              </option>

              <option>
                Penthouse
              </option>

              <option>
                Villa
              </option>
            </select>

          </label>


          <!-- LOCATION -->
          <label>

            <span class="field-title">
              Location
            </span>

            <select>
              <option>
                Select Location
              </option>

              <option>
                Colombo
              </option>

              <option>
                Colombo 03
              </option>

              <option>
                Colombo 07
              </option>

              <option>
                Galle
              </option>

              <option>
                Thalpe
              </option>
            </select>

          </label>


          <!-- PRICE -->
          <label>

            <span class="field-title">
              Price Range
            </span>

            <select>
              <option>
                Min. Price - Max. Price
              </option>

              <option>
                USD 250K – 500K
              </option>

              <option>
                USD 500K – 750K
              </option>

              <option>
                USD 750K+
              </option>
            </select>

          </label>


          <button
            class="go"
            type="submit"
          >
            Search
          </button>

        </form>


        <!-- POPULAR -->
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



    <!-- =====================================================
         SETTINGS MODAL
    ====================================================== -->
    <transition name="modal">

      <div
        v-if="settingsOpen"
        class="settings-overlay"
        @click.self="closeSettings"
      >

        <div
          class="settings-modal"
          @click.stop
        >

          <!-- HEADER -->
          <div class="settings-header">

            <h2>
              Settings
            </h2>


            <button
              type="button"
              class="settings-close"
              @click="closeSettings"
            >
              ×
            </button>

          </div>


          <!-- ===============================================
               SETTINGS TABS
          ================================================ -->
          <div class="settings-tabs">

            <button
              v-for="tab in settingTabs"
              :key="tab"
              type="button"
              :class="{ active: settingsTab === tab }"
              @click="settingsTab = tab"
            >
              {{ tab }}
            </button>

          </div>


          <!-- ===============================================
               CURRENCY
          ================================================ -->
          <div
            v-if="settingsTab === 'Currency'"
            class="settings-content"
          >

            <div class="currency-grid">

              <button
                v-for="item in currencies"
                :key="item.code"
                type="button"
                :class="{
                  selected:
                    selectedCurrency.code === item.code
                }"
                @click="selectCurrency(item)"
              >

                <span>
                  {{ item.name }}
                </span>

                <strong>
                  {{ item.symbol }}
                </strong>

              </button>

            </div>

          </div>


          <!-- ===============================================
               LANGUAGE
          ================================================ -->
          <div
            v-if="settingsTab === 'Language'"
            class="settings-content"
          >

            <div class="option-grid">

              <button
                v-for="language in languages"
                :key="language"
                type="button"
                :class="{
                  selected:
                    selectedLanguage === language
                }"
                @click="selectedLanguage = language"
              >
                {{ language }}
              </button>

            </div>

          </div>


          <!-- ===============================================
               AREA UNIT
          ================================================ -->
          <div
            v-if="settingsTab === 'Area unit'"
            class="settings-content"
          >

            <div class="option-grid area-options">

              <button
                v-for="unit in areaUnits"
                :key="unit"
                type="button"
                :class="{
                  selected:
                    selectedAreaUnit === unit
                }"
                @click="selectedAreaUnit = unit"
              >
                {{ unit }}
              </button>

            </div>

          </div>

        </div>

      </div>

    </transition>

  </section>
</template>


<script setup>
import {
  ref,
  onMounted,
  onBeforeUnmount
} from "vue";


/* =========================================================
   HERO TABS
========================================================= */

const tabs = [
  "Buy",
  "Rent",
  "Sell"
];

const active = ref("Buy");


/* =========================================================
   MENUS
========================================================= */

const sellerOpen = ref(false);

const profileOpen = ref(false);

const menuOpen = ref(false);

const mobileSellerOpen = ref(false);


/* =========================================================
   SETTINGS
========================================================= */

const settingsOpen = ref(false);

const settingsTab = ref("Currency");


const settingTabs = [
  "Language",
  "Currency",
  "Area unit"
];


/* =========================================================
   CURRENCY
========================================================= */

const currencies = [

  {
    code: "EUR",
    name: "Euro",
    symbol: "€"
  },

  {
    code: "USD",
    name: "US dollar",
    symbol: "$"
  },

  {
    code: "GBP",
    name: "British pound",
    symbol: "£"
  },

  {
    code: "RUB",
    name: "Russian ruble",
    symbol: "₽"
  },

  {
    code: "JPY",
    name: "Japanese yen",
    symbol: "¥"
  },

  {
    code: "AED",
    name: "UAE dirham",
    symbol: "د.إ"
  },

  {
    code: "AUD",
    name: "Australian dollar",
    symbol: "$"
  },

  {
    code: "BRL",
    name: "Brazilian real",
    symbol: "R$"
  },

  {
    code: "CAD",
    name: "Canadian dollar",
    symbol: "$"
  },

  {
    code: "CHF",
    name: "Swiss franc",
    symbol: "CHF"
  },

  {
    code: "CNY",
    name: "Chinese yuan",
    symbol: "¥"
  },

  {
    code: "CRC",
    name: "Costa Rican colón",
    symbol: "₡"
  },

  {
    code: "HKD",
    name: "Hong Kong dollar",
    symbol: "$"
  },

  {
    code: "ILS",
    name: "Israeli new shekel",
    symbol: "₪"
  },

  {
    code: "KRW",
    name: "South Korean won",
    symbol: "₩"
  },

  {
    code: "PLN",
    name: "Polish zloty",
    symbol: "zł"
  },

  {
    code: "TRY",
    name: "Turkish lira",
    symbol: "₺"
  },

  {
    code: "LKR",
    name: "Sri Lankan rupee",
    symbol: "Rs"
  }

];


const selectedCurrency = ref(
  currencies[0]
);


/* =========================================================
   LANGUAGE
========================================================= */

const languages = [
  "English",
  "සිංහල",
  "தமிழ்",
  "French",
  "German",
  "Italian",
  "Spanish",
  "Arabic"
];


const selectedLanguage = ref(
  "English"
);


/* =========================================================
   AREA UNIT
========================================================= */

const areaUnits = [
  "Square feet",
  "Square metres",
  "Perches",
  "Acres"
];


const selectedAreaUnit = ref(
  "Square feet"
);


/* =========================================================
   ACTIONS
========================================================= */

const toggleSeller = () => {

  sellerOpen.value =
    !sellerOpen.value;

  profileOpen.value =
    false;

};


const toggleProfile = () => {

  profileOpen.value =
    !profileOpen.value;

  sellerOpen.value =
    false;

};


const openSettings = () => {

  settingsOpen.value =
    true;

  sellerOpen.value =
    false;

  profileOpen.value =
    false;

  menuOpen.value =
    false;

};


const closeSettings = () => {

  settingsOpen.value =
    false;

};


const selectCurrency = (currency) => {

  selectedCurrency.value =
    currency;

};


const handlePageClick = () => {

  sellerOpen.value =
    false;

  profileOpen.value =
    false;

};


/* =========================================================
   ESC CLOSE
========================================================= */

const handleKeydown = (event) => {

  if (event.key === "Escape") {

    settingsOpen.value =
      false;

    sellerOpen.value =
      false;

    profileOpen.value =
      false;

    menuOpen.value =
      false;

  }

};


onMounted(() => {

  window.addEventListener(
    "keydown",
    handleKeydown
  );

});


onBeforeUnmount(() => {

  window.removeEventListener(
    "keydown",
    handleKeydown
  );

});
</script>


<style scoped>

/* =========================================================
   GLOBAL
========================================================= */

.hero,
.hero *,
.hero *::before,
.hero *::after {
  box-sizing: border-box;

  font-family: sans-serif;
}


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

  transform:
    translate(
      -50%,
      -50%
    );

  pointer-events: none;
}


/* =========================================================
   SHADE
========================================================= */

.shade {
  position: absolute;

  z-index: 1;

  inset: 0;

  background:
    linear-gradient(
      180deg,
      rgba(0,0,0,0.38),
      rgba(0,0,0,0.08) 38%,
      rgba(0,0,0,0.18) 67%,
      rgba(0,0,0,0.43)
    );
}


/* =========================================================
   HEADER
========================================================= */

.hero-header {
  position: absolute;

  z-index: 30;

  top: 0;
  left: 0;

  width: 100%;
}


.header-inner {
  width:
    min(
      90vw,
      1720px
    );

  min-height:
    clamp(
      72px,
      8vh,
      88px
    );

  margin: 0 auto;

  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 2rem;
}


/* =========================================================
   BRAND
========================================================= */

.brand {
  min-height: 44px;

  padding:
    0
    clamp(
      0.85rem,
      1.2vw,
      1.3rem
    );

  display: inline-flex;

  align-items: center;

  border:
    1px solid
    rgba(255,255,255,0.9);

  border-radius: 4px;

  color: #ffffff;

  font-size:
    clamp(
      1rem,
      1.25vw,
      1.45rem
    );

  font-weight: 400;

  letter-spacing: 0.035em;

  line-height: 1;

  text-decoration: none;

  white-space: nowrap;

  clip-path:
    polygon(
      4% 0,
      96% 0,
      100% 50%,
      96% 100%,
      4% 100%,
      0 50%
    );
}


/* =========================================================
   HEADER NAV
========================================================= */

.header-nav {
  display: flex;

  align-items: center;

  gap:
    clamp(
      1.3rem,
      2vw,
      2.2rem
    );
}


/* =========================================================
   UNDERLINE HOVER
========================================================= */

.nav-link {
  position: relative;

  color: #ffffff;

  text-decoration: none;

  white-space: nowrap;
}


.nav-link::after {
  content: "";

  position: absolute;

  left: 0;
  bottom: -7px;

  width: 0;

  height: 1px;

  background: #ffffff;

  transition:
    width 0.32s ease;
}


.nav-link:hover::after {
  width: 100%;
}


.header-nav > a {
  font-size:
    clamp(
      0.7rem,
      0.78vw,
      0.88rem
    );

  font-weight: 600;
}


/* =========================================================
   SELL
========================================================= */

.sell-menu {
  position: relative;
}


.sell-trigger {
  display: flex;

  align-items: center;

  gap: 0.65rem;

  padding: 0;

  border: 0;

  background: transparent;

  color: #ffffff;

  font-size:
    clamp(
      0.7rem,
      0.78vw,
      0.88rem
    );

  font-weight: 600;

  cursor: pointer;
}


.sell-trigger svg {
  width: 13px;

  height: 13px;

  stroke-width: 1.8;

  transition:
    transform 0.3s ease;
}


.sell-trigger svg.rotate {
  transform:
    rotate(180deg);
}


/* =========================================================
   SELL DROPDOWN
========================================================= */

.seller-dropdown {
  position: absolute;

  top: calc(100% + 18px);

  right: -80px;

  width: 275px;

  padding: 0.6rem;

  border-radius: 12px;

  background: #ffffff;

  box-shadow:
    0 18px 50px
    rgba(0,0,0,0.18);
}


.seller-dropdown a {
  display: flex;

  align-items: center;

  justify-content: space-between;

  width: 100%;

  padding:
    0.85rem
    0.8rem;

  border-radius: 8px;

  color: #222222;

  font-size: 0.8rem;

  text-decoration: none;

  transition:
    background 0.25s ease;
}


.seller-dropdown a:hover {
  background: #eeeeee;
}


.seller-dropdown a span {
  color: #888888;

  font-size: 0.7rem;
}


/* =========================================================
   CURRENCY BUTTON
========================================================= */

.currency-area {
  display: flex;

  align-items: center;

  gap: 0.7rem;

  padding: 0;

  border: 0;

  background: transparent;

  color: #ffffff;

  cursor: pointer;

  position: relative;
}


.currency-area::after {
  content: "";

  position: absolute;

  left: 0;
  bottom: -7px;

  width: 0;

  height: 1px;

  background: #ffffff;

  transition:
    width 0.3s ease;
}


.currency-area:hover::after {
  width: 100%;
}


.globe {
  width: 28px;

  height: 28px;

  display: grid;

  place-items: center;
}


.globe svg {
  width: 22px;

  height: 22px;

  fill: none;

  stroke: currentColor;

  stroke-width: 1.4;
}


.currency-divider {
  width: 1px;

  height: 27px;

  background:
    rgba(255,255,255,0.65);
}


.currency {
  font-size:
    clamp(
      0.7rem,
      0.77vw,
      0.86rem
    );

  font-weight: 600;
}


/* =========================================================
   PROFILE
========================================================= */

.profile-wrap {
  position: relative;
}


.profile {
  width: 40px;

  height: 40px;

  display: grid;

  place-items: center;

  padding: 0;

  border:
    1px solid
    rgba(255,255,255,0.32);

  border-radius: 50%;

  background:
    rgba(83,52,45,0.92);

  color: #ffffff;

  font-size: 0.72rem;

  cursor: pointer;

  transition:
    transform 0.3s ease,
    background 0.3s ease;
}


.profile:hover {
  transform: scale(1.05);

  background:
    rgba(105,65,54,0.96);
}


/* =========================================================
   PROFILE DROPDOWN
========================================================= */

.profile-menu {
  position: absolute;

  top: calc(100% + 18px);

  right: 0;

  width:
    clamp(
      210px,
      16vw,
      255px
    );

  padding:
    1rem
    0;

  background: #ffffff;

  box-shadow:
    0
    18px
    50px
    rgba(0,0,0,0.17);
}


.profile-menu a {
  position: relative;

  display: block;

  padding:
    0.65rem
    1.25rem;

  color: #282828;

  font-size:
    clamp(
      0.68rem,
      0.74vw,
      0.82rem
    );

  font-weight: 500;

  text-decoration: none;
}


.profile-menu a::after {
  content: "";

  position: absolute;

  left: 1.25rem;

  bottom: 0.4rem;

  width: 0;

  height: 1px;

  background: #111111;

  transition:
    width 0.3s ease;
}


.profile-menu a:hover::after {
  width:
    calc(
      100% - 2.5rem
    );
}


.profile-menu-line {
  height: 1px;

  margin:
    0.45rem
    1.25rem;

  background: #eeeeee;
}


/* =========================================================
   DROPDOWN TRANSITION
========================================================= */

.drop-enter-active,
.drop-leave-active {
  transition:
    opacity 0.2s ease,
    transform 0.2s ease;
}


.drop-enter-from,
.drop-leave-to {
  opacity: 0;

  transform:
    translateY(-7px);
}


/* =========================================================
   HERO CONTENT
========================================================= */

.inner {
  position: relative;

  z-index: 5;

  width:
    min(
      90vw,
      1100px
    );

  text-align: center;

  transform:
    translateY(-1vh);
}


.hero-kicker {
  margin:
    0
    0
    0.55rem;

  color:
    rgba(255,255,255,0.88);

  font-size:
    clamp(
      0.52rem,
      0.58vw,
      0.65rem
    );

  font-weight: 500;

  letter-spacing: 0.22em;

  text-transform: uppercase;
}


h1 {
  margin: 0;

  color: #ffffff;

  font-size:
    clamp(
      3rem,
      3.9vw,
      4.8rem
    );

  font-weight: 400;

  line-height: 1.06;

  letter-spacing: -0.025em;
}


.desc {
  max-width: 610px;

  margin:
    0.75rem
    auto
    1.9rem;

  color:
    rgba(255,255,255,0.88);

  font-size:
    clamp(
      0.64rem,
      0.7vw,
      0.82rem
    );

  line-height: 1.65;
}


/* =========================================================
   SEARCH
========================================================= */

.search {
  width:
    min(
      68vw,
      870px
    );

  margin: 0 auto;

  text-align: left;
}


.tabs {
  display: flex;
}


.tabs button {
  width: 80px;

  height: 42px;

  border: 0;

  background:
    rgba(24,24,24,0.96);

  color: #ffffff;

  font-size: 0.7rem;

  font-weight: 500;

  cursor: pointer;
}


.tabs .on {
  background: #ffffff;

  color: #111111;
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


/* =========================================================
   FORM
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
    0 12px 30px
    rgba(0,0,0,0.13);
}


label {
  padding:
    0.8rem
    1rem;

  display: flex;

  flex-direction: column;

  justify-content: center;

  border-right:
    1px solid #e8e8e8;
}


.field-title {
  color: #111111;

  font-size: 0.7rem;

  font-weight: 600;
}


select {
  width: 100%;

  margin-top: 0.38rem;

  border: 0;

  outline: none;

  background: transparent;

  color: #777777;

  font-size: 0.66rem;

  cursor: pointer;
}


.go {
  margin: 7px;

  border: 0;

  border-radius: 7px;

  background: #111111;

  color: #ffffff;

  font-size: 0.72rem;

  font-weight: 600;

  cursor: pointer;
}


/* =========================================================
   QUICK
========================================================= */

.quick {
  display: flex;

  align-items: center;

  justify-content: center;

  flex-wrap: wrap;

  gap: 0.5rem;

  margin-top: 0.8rem;

  color:
    rgba(255,255,255,0.9);

  font-size: 0.65rem;
}


.quick button {
  padding:
    0.38rem
    0.7rem;

  border: 0;

  border-radius: 4px;

  background: #ffffff;

  color: #111111;

  font-size: 0.62rem;

  cursor: pointer;
}


/* =========================================================
   SETTINGS OVERLAY
========================================================= */

.settings-overlay {
  position: fixed;

  z-index: 999;

  inset: 0;

  display: flex;

  align-items: center;

  justify-content: center;

  padding: 2rem;

  background:
    rgba(0,0,0,0.53);

  backdrop-filter: blur(2px);
}


/* =========================================================
   SETTINGS MODAL
========================================================= */

.settings-modal {
  width:
    min(
      92vw,
      830px
    );

  min-height: 520px;

  overflow: hidden;

  background: #ffffff;

  color: #222222;

  box-shadow:
    0
    25px
    70px
    rgba(0,0,0,0.25);
}


/* =========================================================
   SETTINGS HEADER
========================================================= */

.settings-header {
  position: relative;

  min-height: 82px;

  display: flex;

  align-items: center;

  justify-content: center;

  border-bottom:
    1px solid #dddddd;
}


.settings-header h2 {
  margin: 0;

  font-size:
    clamp(
      1rem,
      1.1vw,
      1.25rem
    );

  font-weight: 700;
}


.settings-close {
  position: absolute;

  top: 50%;
  right: 1.6rem;

  transform:
    translateY(-50%);

  width: 35px;

  height: 35px;

  border: 0;

  background: transparent;

  color: #333333;

  font-size: 1.7rem;

  font-weight: 300;

  cursor: pointer;
}


/* =========================================================
   SETTINGS TABS
========================================================= */

.settings-tabs {
  display: flex;

  align-items: flex-end;

  gap: 1rem;

  margin:
    2rem
    1.6rem
    0;

  border-bottom:
    1px solid #cccccc;
}


.settings-tabs button {
  position: relative;

  padding:
    0
    0.3rem
    0.8rem;

  border: 0;

  background: transparent;

  color: #999999;

  font-size:
    clamp(
      0.7rem,
      0.78vw,
      0.88rem
    );

  font-weight: 600;

  cursor: pointer;
}


.settings-tabs button::after {
  content: "";

  position: absolute;

  left: 0;

  bottom: -1px;

  width: 0;

  height: 2px;

  background: #111111;

  transition:
    width 0.3s ease;
}


.settings-tabs button:hover::after,
.settings-tabs button.active::after {
  width: 100%;
}


.settings-tabs button.active {
  color: #222222;
}


/* =========================================================
   SETTINGS CONTENT
========================================================= */

.settings-content {
  padding:
    1.4rem
    1.6rem
    2rem;
}


/* =========================================================
   CURRENCY GRID
========================================================= */

.currency-grid {
  display: grid;

  grid-template-columns:
    repeat(
      3,
      minmax(0, 1fr)
    );

  gap:
    0.35rem
    1.1rem;
}


.currency-grid button {
  min-height: 48px;

  display: flex;

  align-items: center;

  justify-content: center;

  gap: 0.35rem;

  padding:
    0.6rem
    0.8rem;

  border:
    1px solid transparent;

  border-radius: 30px;

  background: transparent;

  color: #292929;

  font-size:
    clamp(
      0.68rem,
      0.76vw,
      0.84rem
    );

  cursor: pointer;

  transition:
    border 0.25s ease,
    background 0.25s ease;
}


.currency-grid button:hover {
  background: #f3f3f3;
}


.currency-grid button.selected {
  border-color: #222222;

  background: #ffffff;
}


.currency-grid button strong {
  font-weight: 600;
}


/* =========================================================
   LANGUAGE / AREA GRID
========================================================= */

.option-grid {
  display: grid;

  grid-template-columns:
    repeat(
      3,
      minmax(0, 1fr)
    );

  gap: 0.65rem;
}


.option-grid button {
  min-height: 48px;

  padding:
    0.6rem
    0.8rem;

  border:
    1px solid #dddddd;

  border-radius: 30px;

  background: #ffffff;

  color: #222222;

  font-size: 0.76rem;

  cursor: pointer;

  transition:
    background 0.25s ease,
    border 0.25s ease;
}


.option-grid button:hover {
  background: #f3f3f3;
}


.option-grid button.selected {
  border-color: #111111;

  background: #111111;

  color: #ffffff;
}


/* =========================================================
   MODAL TRANSITION
========================================================= */

.modal-enter-active,
.modal-leave-active {
  transition:
    opacity 0.25s ease;
}


.modal-enter-active .settings-modal,
.modal-leave-active .settings-modal {
  transition:
    transform 0.25s ease,
    opacity 0.25s ease;
}


.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}


.modal-enter-from .settings-modal,
.modal-leave-to .settings-modal {
  opacity: 0;

  transform:
    translateY(15px)
    scale(0.985);
}


/* =========================================================
   MOBILE BUTTON
========================================================= */

.mobile-toggle {
  display: none;

  width: 38px;

  height: 38px;

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
   TABLET
========================================================= */

@media (max-width: 900px) {

  .header-nav {
    display: none;
  }


  .mobile-toggle {
    display: block;
  }


  .mobile-menu.open {
    width: 91vw;

    margin: 0 auto;

    padding: 1rem;

    display: flex;

    flex-direction: column;

    background:
      rgba(10,10,10,0.97);
  }


  .mobile-menu > a {
    padding:
      0.7rem
      0;

    color: #ffffff;

    font-size: 0.74rem;

    text-decoration: none;
  }


  .mobile-sell,
  .mobile-settings,
  .mobile-profile {
    width: 100%;

    display: flex;

    align-items: center;

    justify-content: space-between;

    padding:
      0.75rem
      0;

    border: 0;

    border-top:
      1px solid
      rgba(255,255,255,0.12);

    background: transparent;

    color: #ffffff;

    font-size: 0.74rem;
  }


  .mobile-seller-links {
    display: flex;

    flex-direction: column;

    padding:
      0.5rem
      0.75rem;

    background:
      rgba(255,255,255,0.06);
  }


  .mobile-seller-links a {
    padding:
      0.5rem
      0;

    color:
      rgba(255,255,255,0.7);

    font-size: 0.66rem;

    text-decoration: none;
  }


  .mobile-profile span {
    width: 28px;

    height: 28px;

    display: grid;

    place-items: center;

    border-radius: 50%;

    background: #5c3b33;
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


  .settings-modal {
    min-height: 470px;
  }


  .currency-grid {
    grid-template-columns:
      repeat(
        2,
        minmax(0, 1fr)
      );
  }


  .option-grid {
    grid-template-columns:
      repeat(
        2,
        minmax(0, 1fr)
      );
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


  h1 {
    font-size:
      clamp(
        2.7rem,
        11vw,
        3.5rem
      );
  }


  .desc {
    width: 92%;

    font-size: 0.68rem;
  }


  .search {
    width: 100%;
  }


  form {
    grid-template-columns: 1fr;
  }


  label {
    min-height: 64px;
  }


  .go {
    grid-column: auto;

    min-height: 46px;
  }


  .settings-overlay {
    padding: 0.8rem;
  }


  .settings-modal {
    width: 100%;

    max-height: 88vh;

    min-height: auto;

    overflow-y: auto;
  }


  .settings-header {
    min-height: 65px;
  }


  .settings-tabs {
    margin:
      1.3rem
      1rem
      0;

    gap: 0.45rem;
  }


  .settings-tabs button {
    font-size: 0.65rem;

    padding-bottom: 0.65rem;
  }


  .settings-content {
    padding:
      1rem
      1rem
      1.4rem;
  }


  .currency-grid,
  .option-grid {
    grid-template-columns: 1fr;
  }


  .currency-grid button,
  .option-grid button {
    min-height: 43px;
  }

}
</style>