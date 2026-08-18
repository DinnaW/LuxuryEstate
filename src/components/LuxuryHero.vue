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
          <span class="brand-mark">LE</span>
          <span class="brand-name">Luxury Estate</span>
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
        <span class="kicker-line"></span>
        Luxury Real Estate · Worldwide
      </p>


      <h1>
         Exceptional Residences
      </h1>


      <p class="desc">
         Discover prestigious properties in the world's
  most soughtgg most.
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

.hero {
  --gold: #c6a87c;
  --ink: #0a0a0a;
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

  background: var(--ink);
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

  filter: saturate(0.92) contrast(1.03);
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
      rgba(6, 6, 6, 0.62) 0%,
      rgba(6, 6, 6, 0.12) 26%,
      rgba(6, 6, 6, 0.22) 64%,
      rgba(6, 6, 6, 0.6) 100%
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

  background: linear-gradient(180deg, rgba(6, 6, 6, 0.5) 0%, rgba(6, 6, 6, 0) 100%);
}

.header-inner {
  width: min(90vw, 1720px);
  min-height: clamp(84px, 9vh, 104px);
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
  display: inline-flex;
  align-items: center;
  gap: 12px;

  color: #ffffff;
  text-decoration: none;
}

.brand-mark {
  width: 38px;
  height: 38px;

  display: grid;
  place-items: center;

  border: 1px solid rgba(255, 255, 255, 0.5);
  border-radius: 50%;

  font-family: sans-serif;
  font-size: clamp(11px, 0.72vw, 13px);
  letter-spacing: 0.02em;
}

.brand-name {
   font-family: sans-serif;
  font-size: clamp(17px, 1.15vw, 21px);
  font-weight: 400;
  letter-spacing: 0.05em;
  white-space: nowrap;
}


/* =========================================================
   HEADER NAV
========================================================= */

.header-nav {
  display: flex;
  align-items: center;
  gap: clamp(1.5rem, 2.4vw, 2.6rem);
}

.nav-link {
  position: relative;
  color: rgba(255, 255, 255, 0.88);
  text-decoration: none;
  white-space: nowrap;

  font-size: clamp(11px, 0.72vw, 13px);
  font-weight: 500;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

.nav-link::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -8px;
  width: 0;
  height: 1px;
  background: var(--gold);
  transition: width 0.35s ease;
}

.nav-link:hover::after {
  width: 100%;
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
  gap: 0.6rem;

  padding: 0;
  border: 0;
  background: transparent;
  color: rgba(255, 255, 255, 0.88);

  font-size: clamp(11px, 0.72vw, 13px);
  font-weight: 500;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  cursor: pointer;
}

.sell-trigger svg {
  width: 12px;
  height: 12px;
  stroke-width: 1.6;
  color: var(--gold);
  transition: transform 0.3s ease;
}

.sell-trigger svg.rotate {
  transform: rotate(180deg);
}

.seller-dropdown {
  position: absolute;
  top: calc(100% + 22px);
  right: -80px;
  width: 275px;

  padding: 0.5rem;
  background: #ffffff;
  box-shadow: 0 24px 60px rgba(0, 0, 0, 0.2);
}

.seller-dropdown a {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;

  padding: 0.9rem 0.9rem;
  color: #1a1a1a;
  font-size: clamp(11px, 0.72vw, 13px);
  text-decoration: none;
  transition: background 0.25s ease;
}

.seller-dropdown a:hover {
  background: #f7f5f2;
}

.seller-dropdown a span {
  color: #999999;
  font-size: clamp(9px, 0.58vw, 11px);
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
  color: rgba(255, 255, 255, 0.88);
  cursor: pointer;
  position: relative;
}

.currency-area::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -8px;
  width: 0;
  height: 1px;
  background: var(--gold);
  transition: width 0.3s ease;
}

.currency-area:hover::after {
  width: 100%;
}

.globe {
  width: 26px;
  height: 26px;
  display: grid;
  place-items: center;
}

.globe svg {
  width: 19px;
  height: 19px;
  fill: none;
  stroke: currentColor;
  stroke-width: 1.3;
}

.currency-divider {
  width: 1px;
  height: 22px;
  background: rgba(255, 255, 255, 0.3);
}

.currency {
  font-size: clamp(11px, 0.72vw, 13px);
  font-weight: 500;
  letter-spacing: 0.04em;
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
  border: 1px solid rgba(255, 255, 255, 0.4);
  border-radius: 50%;

  background: transparent;
  color: #ffffff;
  font-family: sans-serif;
  font-size: clamp(11px, 0.72vw, 13px);
  cursor: pointer;

  transition: border-color 0.3s ease, background 0.3s ease;
}

.profile:hover {
  border-color: var(--gold);
  background: rgba(198, 168, 124, 0.12);
}

.profile-menu {
  position: absolute;
  top: calc(100% + 22px);
  right: 0;
  width: clamp(210px, 16vw, 255px);

  padding: 0.9rem 0;
  background: #ffffff;
  box-shadow: 0 24px 60px rgba(0, 0, 0, 0.2);
}

.profile-menu a {
  position: relative;
  display: block;

  padding: 0.65rem 1.3rem;
  color: #1a1a1a;
  font-size: clamp(11px, 0.70vw, 13px);
  font-weight: 400;
  text-decoration: none;
}

.profile-menu a::after {
  content: "";
  position: absolute;
  left: 1.3rem;
  bottom: 0.4rem;
  width: 0;
  height: 1px;
  background: var(--gold);
  transition: width 0.3s ease;
}

.profile-menu a:hover::after {
  width: calc(100% - 2.6rem);
}

.profile-menu-line {
  height: 1px;
  margin: 0.5rem 1.3rem;
  background: #ececec;
}


/* =========================================================
   DROPDOWN TRANSITION
========================================================= */

.drop-enter-active,
.drop-leave-active {
  transition: opacity 0.2s ease, transform 0.2s ease;
}

.drop-enter-from,
.drop-leave-to {
  opacity: 0;
  transform: translateY(-7px);
}


/* =========================================================
   HERO CONTENT
========================================================= */

.inner {
  position: relative;
  z-index: 5;
  width: min(90vw, 1100px);
  text-align: center;
  transform: translateY(-1vh);
}

.hero-kicker {
  display: inline-flex;
  align-items: center;
  gap: 12px;

  margin: 0 0 1.1rem;

  color: rgba(255, 255, 255, 0.75);
  font-size: clamp(10px, 0.66vw, 12px);
  font-weight: 500;
  letter-spacing: 0.28em;
  text-transform: uppercase;
}

.kicker-line {
  width: 30px;
  height: 1px;
  background: var(--gold);
}

h1 {
  margin: 0;
  color: #ffffff;

  font-family: sans-serif;
  font-size: clamp(46px, 4.1vw, 66px);
  font-weight: 400;
  line-height: 1.04;
  letter-spacing: -0.025em;
}

.desc {
  max-width: 560px;
  margin: 1.1rem auto 2.2rem;

  color: rgba(255, 255, 255, 0.68);
  font-size: clamp(13px, 0.86vw, 15px);
  font-weight: 400;
  line-height: 1.7;
}


/* =========================================================
   SEARCH
========================================================= */

.search {
  width: min(68vw, 900px);
  margin: 0 auto;
  text-align: left;
}

.tabs {
  display: flex;
  gap: 2px;
}

.tabs button {
  width: 92px;
  height: 44px;

  border: 0;
  background: rgba(10, 10, 10, 0.55);
  backdrop-filter: blur(6px);
  color: rgba(255, 255, 255, 0.8);

  font-size: clamp(10px, 0.66vw, 12px);
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  cursor: pointer;

  transition: background 0.3s ease, color 0.3s ease;
}

.tabs .on {
  background: #ffffff;
  color: var(--ink);
}


/* =========================================================
   FORM
========================================================= */

form {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 130px;

  min-height: 82px;
  overflow: hidden;

  background: rgba(255, 255, 255, 0.98);
  color: var(--ink);

  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.22);
}

label {
  padding: 0.9rem 1.15rem;

  display: flex;
  flex-direction: column;
  justify-content: center;

  border-right: 1px solid #ececec;
}

.field-title {
  color: #8a8a8a;
  font-size: clamp(9px, 0.60vw, 11px);
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

select {
  width: 100%;
  margin-top: 0.4rem;

  border: 0;
  outline: none;
  background: transparent;

  color: var(--ink);
  font-size: clamp(12px, 0.80vw, 14px);
  cursor: pointer;
}

.go {
  width: 100%;
  height: 100%;
  align-self: stretch;
  margin: 0;
  padding: 0;

  display: flex;
  align-items: center;
  justify-content: center;

  border: 0;
  background: var(--ink);
  color: #ffffff;

  font-size: clamp(10px, 0.66vw, 12px);
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  cursor: pointer;

  transition: background 0.3s ease;
}

.go:hover {
  background: var(--gold);
  color: var(--ink);
}


/* =========================================================
   QUICK
========================================================= */

.quick {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.6rem;

  margin-top: 1.1rem;

  color: rgba(255, 255, 255, 0.6);
  font-size: clamp(10px, 0.68vw, 12px);
  letter-spacing: 0.02em;
}

.quick button {
  padding: 0.4rem 0.85rem;

  border: 1px solid rgba(255, 255, 255, 0.3);
  background: transparent;
  color: rgba(255, 255, 255, 0.85);

  font-size: clamp(10px, 0.68vw, 12px);
  cursor: pointer;

  transition: border-color 0.3s ease, color 0.3s ease;
}

.quick button:hover {
  border-color: var(--gold);
  color: var(--gold);
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

  background: rgba(6, 6, 6, 0.6);
  backdrop-filter: blur(3px);
}

.settings-modal {
  width: min(92vw, 830px);
  min-height: 520px;
  overflow: hidden;

  background: #ffffff;
  color: #1a1a1a;

  box-shadow: 0 30px 80px rgba(0, 0, 0, 0.28);
}

.settings-header {
  position: relative;
  min-height: 86px;

  display: flex;
  align-items: center;
  justify-content: center;

  border-bottom: 1px solid #ececec;
}

.settings-header h2 {
  margin: 0;

  font-family: sans-serif;
  font-size: clamp(18px, 1.15vw, 21px);
  font-weight: 400;
}

.settings-close {
  position: absolute;
  top: 50%;
  right: 1.7rem;
  transform: translateY(-50%);

  width: 35px;
  height: 35px;

  border: 0;
  background: transparent;
  color: #444444;
  font-size: 26px;
  font-weight: 300;
  cursor: pointer;
}

.settings-tabs {
  display: flex;
  align-items: flex-end;
  gap: 1.4rem;

  margin: 2.1rem 1.7rem 0;
  border-bottom: 1px solid #ececec;
}

.settings-tabs button {
  position: relative;

  padding: 0 0.3rem 0.85rem;
  border: 0;
  background: transparent;
  color: #a3a3a3;

  font-size: clamp(10px, 0.68vw, 12px);
  font-weight: 500;
  letter-spacing: 0.03em;
  cursor: pointer;
}

.settings-tabs button::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -1px;
  width: 0;
  height: 1px;
  background: var(--gold);
  transition: width 0.3s ease;
}

.settings-tabs button:hover::after,
.settings-tabs button.active::after {
  width: 100%;
}

.settings-tabs button.active {
  color: #1a1a1a;
}

.settings-content {
  padding: 1.5rem 1.7rem 2.1rem;
}


/* =========================================================
   CURRENCY GRID
========================================================= */

.currency-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 0.4rem 1.1rem;
}

.currency-grid button {
  min-height: 48px;

  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.35rem;

  padding: 0.6rem 0.8rem;
  border: 1px solid #e8e8e8;
  background: transparent;
  color: #333333;

  font-size: clamp(11px, 0.72vw, 13px);
  cursor: pointer;

  transition: border-color 0.25s ease, background 0.25s ease;
}

.currency-grid button:hover {
  border-color: #cccccc;
  background: #faf9f7;
}

.currency-grid button.selected {
  border-color: var(--gold);
  background: rgba(198, 168, 124, 0.08);
}

.currency-grid button strong {
  font-weight: 600;
}


/* =========================================================
   LANGUAGE / AREA GRID
========================================================= */

.option-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 0.6rem;
}

.option-grid button {
  min-height: 48px;

  padding: 0.6rem 0.8rem;
  border: 1px solid #e8e8e8;
  background: #ffffff;
  color: #333333;

  font-size: clamp(11px, 0.72vw, 13px);
  cursor: pointer;

  transition: background 0.25s ease, border 0.25s ease;
}

.option-grid button:hover {
  border-color: #cccccc;
  background: #faf9f7;
}

.option-grid button.selected {
  border-color: var(--ink);
  background: var(--ink);
  color: #ffffff;
}


/* =========================================================
   MODAL TRANSITION
========================================================= */

.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.25s ease;
}

.modal-enter-active .settings-modal,
.modal-leave-active .settings-modal {
  transition: transform 0.25s ease, opacity 0.25s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .settings-modal,
.modal-leave-to .settings-modal {
  opacity: 0;
  transform: translateY(15px) scale(0.985);
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

    background: rgba(8, 8, 8, 0.97);
  }

  .mobile-menu > a {
    padding: 0.75rem 0;
    color: #ffffff;
    font-size: 0.76rem;
    text-decoration: none;
  }

  .mobile-sell,
  .mobile-settings,
  .mobile-profile {
    width: 100%;

    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 0.8rem 0;
    border: 0;
    border-top: 1px solid rgba(255, 255, 255, 0.12);
    background: transparent;
    color: #ffffff;
    font-size: 0.76rem;
  }

  .mobile-seller-links {
    display: flex;
    flex-direction: column;
    padding: 0.5rem 0.75rem;
    background: rgba(255, 255, 255, 0.06);
  }

  .mobile-seller-links a {
    padding: 0.5rem 0;
    color: rgba(255, 255, 255, 0.7);
    font-size: 0.68rem;
    text-decoration: none;
  }

  .mobile-profile span {
    width: 28px;
    height: 28px;
    display: grid;
    place-items: center;
    border-radius: 50%;
    border: 1px solid rgba(255, 255, 255, 0.4);
  }

  .search {
    width: 88vw;
  }

  form {
    grid-template-columns: 1fr 1fr;
  }

  /* =========================================================
   SEARCH BUTTON — FULL BLACK, NO WHITE SPACE
========================================================= */

.go {
  margin: 0;
  padding: 0;

  display: flex;
  align-items: center;
  justify-content: center;

  border: 0;
  background: var(--ink);
  color: #ffffff;

  font-size: clamp(10px, 0.66vw, 12px);
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  cursor: pointer;

  transition: background 0.3s ease;
}
.go:hover {
  background: #1c1c1c;
  color: #ffffff;
}

  .settings-modal {
    min-height: 470px;
  }

  .currency-grid,
  .option-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
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

  .brand-name {
    font-size: 16px;
  }

  .inner {
    width: 92vw;
    transform: none;
  }

  h1 {
    font-size: clamp(38px, 10.5vw, 50px);
  }

  .desc {
    width: 94%;
    font-size: 13px;
  }

  .search {
    width: 100%;
  }

  form {
    grid-template-columns: 1fr;
  }

  label {
    min-height: 66px;
  }

  .go {
    grid-column: auto;
    min-height: 48px;
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
    min-height: 68px;
  }

  .settings-tabs {
    margin: 1.4rem 1rem 0;
    gap: 0.5rem;
  }

  .settings-tabs button {
    font-size: 10px;
    padding-bottom: 0.7rem;
  }

  .settings-content {
    padding: 1rem 1rem 1.5rem;
  }

  .currency-grid,
  .option-grid {
    grid-template-columns: 1fr;
  }

  .currency-grid button,
  .option-grid button {
    min-height: 44px;
  }
}
</style>