<template>
  <section class="property-filter-section">

    <div class="filter-shell">

      <!-- =====================================================
           TOP CONTENT
      ====================================================== -->
      <div class="filter-heading">

        <div>
          <p class="filter-kicker">
            FIND YOUR PROPERTY
          </p>

          <h2>
            Refine your search.
          </h2>
        </div>


        <p class="filter-description">
          Explore residences by location, property type,
          price, lifestyle and development status.
        </p>

      </div>


      <!-- =====================================================
           MAIN FILTER BAR
      ====================================================== -->
      <div class="filter-card">

        <!-- BUY / RENT -->
        <div class="filter-mode">

          <button
            v-for="item in modes"
            :key="item"
            type="button"
            :class="{ active: filters.mode === item }"
            @click="filters.mode = item"
          >
            {{ item }}
          </button>

        </div>


        <!-- MAIN FILTER FIELDS -->
        <div class="main-filter-grid">

          <!-- PROPERTY TYPE -->
          <div class="filter-field">

            <span class="field-label">
              Property Type
            </span>

            <select v-model="filters.propertyType">
              <option value="">
                All property types
              </option>

              <option
                v-for="item in propertyTypes"
                :key="item"
                :value="item"
              >
                {{ item }}
              </option>
            </select>

          </div>


          <!-- LOCATION -->
          <div class="filter-field">

            <span class="field-label">
              Location
            </span>

            <select v-model="filters.location">
              <option value="">
                All locations
              </option>

              <option
                v-for="item in locations"
                :key="item"
                :value="item"
              >
                {{ item }}
              </option>
            </select>

          </div>


          <!-- PRICE -->
          <div class="filter-field">

            <span class="field-label">
              Price Range
            </span>

            <select v-model="filters.price">
              <option value="">
                Any price
              </option>

              <option
                v-for="item in priceRanges"
                :key="item.value"
                :value="item.value"
              >
                {{ item.label }}
              </option>
            </select>

          </div>


          <!-- BEDROOMS -->
          <div class="filter-field">

            <span class="field-label">
              Bedrooms
            </span>

            <select v-model="filters.bedrooms">
              <option value="">
                Any bedrooms
              </option>

              <option value="1">
                1 Bedroom
              </option>

              <option value="2">
                2 Bedrooms
              </option>

              <option value="3">
                3 Bedrooms
              </option>

              <option value="4">
                4 Bedrooms
              </option>

              <option value="5">
                5+ Bedrooms
              </option>
            </select>

          </div>


          <!-- MORE FILTERS -->
          <button
            class="more-filter-button"
            type="button"
            :class="{ active: moreOpen }"
            @click="moreOpen = !moreOpen"
          >
            <span>
              More Filters
            </span>

            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              :class="{ rotate: moreOpen }"
            >
              <path d="M6 9l6 6 6-6" />
            </svg>
          </button>


          <!-- SEARCH -->
          <button
            class="search-button"
            type="button"
            @click="searchProperties"
          >
            Search Properties

            <span>→</span>
          </button>

        </div>


        <!-- =================================================
             ACTIVE FILTER SUMMARY
        ================================================== -->
        <div
          v-if="activeFilterCount > 0"
          class="active-summary"
        >

          <span>
            {{ activeFilterCount }}
            filter{{ activeFilterCount > 1 ? "s" : "" }}
            selected
          </span>

          <button
            type="button"
            @click="clearAll"
          >
            Clear all
          </button>

        </div>

      </div>


      <!-- =====================================================
           MORE FILTERS PANEL
      ====================================================== -->
      <transition name="more">

        <div
          v-if="moreOpen"
          class="advanced-panel"
        >

          <!-- HEADER -->
          <div class="advanced-head">

            <div>
              <p>
                ADVANCED SEARCH
              </p>

              <h3>
                More Filters
              </h3>
            </div>


            <button
              type="button"
              class="close-more"
              @click="moreOpen = false"
            >
              ×
            </button>

          </div>


          <!-- =================================================
               FILTER GRID
          ================================================== -->
          <div class="advanced-grid">

            <!-- BATHROOMS -->
            <div class="advanced-group">

              <h4>
                Bathrooms
              </h4>

              <div class="choice-row">

                <button
                  v-for="item in bathroomOptions"
                  :key="item.value"
                  type="button"
                  :class="{
                    selected:
                      filters.bathrooms === item.value
                  }"
                  @click="filters.bathrooms = item.value"
                >
                  {{ item.label }}
                </button>

              </div>

            </div>


            <!-- FLOOR AREA -->
            <div class="advanced-group">

              <h4>
                Floor Area
              </h4>

              <div class="range-inputs">

                <label>
                  <span>Min sq.ft</span>

                  <input
                    v-model="filters.minArea"
                    type="number"
                    placeholder="500"
                  />
                </label>


                <span class="range-separator">
                  —
                </span>


                <label>
                  <span>Max sq.ft</span>

                  <input
                    v-model="filters.maxArea"
                    type="number"
                    placeholder="5,000"
                  />
                </label>

              </div>

            </div>


            <!-- PROJECT STATUS -->
            <div class="advanced-group">

              <h4>
                Project Status
              </h4>

              <div class="check-list">

                <label
                  v-for="item in projectStatuses"
                  :key="item"
                >

                  <input
                    v-model="filters.projectStatus"
                    type="checkbox"
                    :value="item"
                  />

                  <span class="custom-check"></span>

                  <span>
                    {{ item }}
                  </span>

                </label>

              </div>

            </div>


            <!-- DEVELOPER -->
            <div class="advanced-group">

              <h4>
                Developer
              </h4>

              <select
                v-model="filters.developer"
                class="advanced-select"
              >
                <option value="">
                  All developers
                </option>

                <option
                  v-for="item in developers"
                  :key="item"
                  :value="item"
                >
                  {{ item }}
                </option>
              </select>

            </div>


            <!-- COMPLETION -->
            <div class="advanced-group">

              <h4>
                Completion
              </h4>

              <select
                v-model="filters.completion"
                class="advanced-select"
              >
                <option value="">
                  Any year
                </option>

                <option value="2026">
                  2026
                </option>

                <option value="2027">
                  2027
                </option>

                <option value="2028">
                  2028
                </option>

                <option value="2029+">
                  2029+
                </option>
              </select>

            </div>


            <!-- PARKING -->
            <div class="advanced-group">

              <h4>
                Parking
              </h4>

              <div class="choice-row">

                <button
                  v-for="item in parkingOptions"
                  :key="item.value"
                  type="button"
                  :class="{
                    selected:
                      filters.parking === item.value
                  }"
                  @click="filters.parking = item.value"
                >
                  {{ item.label }}
                </button>

              </div>

            </div>


            <!-- VIEW -->
            <div class="advanced-group">

              <h4>
                Property View
              </h4>

              <div class="check-list">

                <label
                  v-for="item in viewOptions"
                  :key="item"
                >

                  <input
                    v-model="filters.views"
                    type="checkbox"
                    :value="item"
                  />

                  <span class="custom-check"></span>

                  <span>
                    {{ item }}
                  </span>

                </label>

              </div>

            </div>


            <!-- AMENITIES -->
            <div class="advanced-group amenities-group">

              <h4>
                Amenities
              </h4>

              <div class="amenities-grid">

                <label
                  v-for="item in amenities"
                  :key="item"
                  class="amenity-option"
                >

                  <input
                    v-model="filters.amenities"
                    type="checkbox"
                    :value="item"
                  />

                  <span class="custom-check"></span>

                  <span>
                    {{ item }}
                  </span>

                </label>

              </div>

            </div>

          </div>


          <!-- =================================================
               FOOTER
          ================================================== -->
          <div class="advanced-footer">

            <button
              type="button"
              class="clear-button"
              @click="clearAll"
            >
              Clear All
            </button>


            <button
              type="button"
              class="show-button"
              @click="searchProperties"
            >
              Show Properties
              <span>→</span>
            </button>

          </div>

        </div>

      </transition>

    </div>

  </section>
</template>


<script setup>
import {
  reactive,
  ref,
  computed
} from "vue";


const moreOpen = ref(false);


const modes = [
  "Buy",
  "Rent"
];


const propertyTypes = [
  "Apartments",
  "Villas",
  "Houses",
  "Penthouses",
  "Townhouses",
  "Beachside Homes",
  "Residential Complexes"
];


const locations = [
  "Colombo",
  "Colombo 03",
  "Colombo 07",
  "Thalawathugoda",
  "Galle",
  "Thalpe",
  "Mirissa",
  "Weligama",
  "Nuwara Eliya",
  "Negombo"
];


const priceRanges = [
  {
    label: "Below LKR 25M",
    value: "0-25"
  },

  {
    label: "LKR 25M – 40M",
    value: "25-40"
  },

  {
    label: "LKR 40M – 60M",
    value: "40-60"
  },

  {
    label: "LKR 60M – 100M",
    value: "60-100"
  },

  {
    label: "LKR 100M+",
    value: "100+"
  }
];


const bathroomOptions = [
  {
    label: "Any",
    value: ""
  },

  {
    label: "1",
    value: "1"
  },

  {
    label: "2",
    value: "2"
  },

  {
    label: "3",
    value: "3"
  },

  {
    label: "4+",
    value: "4+"
  }
];


const parkingOptions = [
  {
    label: "Any",
    value: ""
  },

  {
    label: "1 Slot",
    value: "1"
  },

  {
    label: "2+ Slots",
    value: "2+"
  }
];


const projectStatuses = [
  "Newly Launched",
  "Under Construction",
  "Ready to Move",
  "Completed"
];


const developers = [
  "Odiliya Premier",
  "Home Lands Skyline",
  "Prime Residencies",
  "Blue Ocean Group"
];


const viewOptions = [
  "Ocean View",
  "City View",
  "Garden View",
  "Pool View",
  "Mountain View"
];


const amenities = [
  "Swimming Pool",
  "Gym",
  "24/7 Security",
  "Dedicated Parking",
  "Rooftop Terrace",
  "Kids Play Area",
  "Smart Home",
  "Concierge",
  "EV Charging",
  "Private Garden"
];


const filters = reactive({

  mode:
    "Buy",

  propertyType:
    "",

  location:
    "",

  price:
    "",

  bedrooms:
    "",

  bathrooms:
    "",

  minArea:
    "",

  maxArea:
    "",

  projectStatus:
    [],

  developer:
    "",

  completion:
    "",

  parking:
    "",

  views:
    [],

  amenities:
    []

});


const activeFilterCount = computed(() => {

  let count = 0;

  if (filters.propertyType) count++;

  if (filters.location) count++;

  if (filters.price) count++;

  if (filters.bedrooms) count++;

  if (filters.bathrooms) count++;

  if (filters.minArea || filters.maxArea) count++;

  if (filters.projectStatus.length) count++;

  if (filters.developer) count++;

  if (filters.completion) count++;

  if (filters.parking) count++;

  if (filters.views.length) count++;

  if (filters.amenities.length) count++;

  return count;

});


const clearAll = () => {

  filters.mode =
    "Buy";

  filters.propertyType =
    "";

  filters.location =
    "";

  filters.price =
    "";

  filters.bedrooms =
    "";

  filters.bathrooms =
    "";

  filters.minArea =
    "";

  filters.maxArea =
    "";

  filters.projectStatus =
    [];

  filters.developer =
    "";

  filters.completion =
    "";

  filters.parking =
    "";

  filters.views =
    [];

  filters.amenities =
    [];

};


const searchProperties = () => {

  console.log(
    "Selected Filters:",
    JSON.parse(
      JSON.stringify(filters)
    )
  );

};
</script>


<style scoped>

/* =========================================================
   GLOBAL
========================================================= */

.property-filter-section,
.property-filter-section *,
.property-filter-section *::before,
.property-filter-section *::after {
  box-sizing: border-box;
  font-family: sans-serif;
}


/* =========================================================
   SECTION
========================================================= */

.property-filter-section {
  width: 100%;

  padding:
    clamp(4rem, 7vh, 6rem)
    0;

  background: #f4f2ed;

  color: #111111;
}


.filter-shell {
  width:
    min(92vw, 1600px);

  margin: 0 auto;
}


/* =========================================================
   HEADING
========================================================= */

.filter-heading {
  display: grid;

  grid-template-columns:
    1fr
    0.7fr;

  align-items: end;

  gap:
    clamp(2rem, 7vw, 8rem);

  margin-bottom:
    clamp(1.5rem, 3vh, 2.3rem);
}


.filter-kicker {
  margin:
    0
    0
    0.55rem;

  color: #9d7d47;

  font-size:
    clamp(
      0.5rem,
      0.55vw,
      0.62rem
    );

  font-weight: 700;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}


.filter-heading h2 {
  margin: 0;

  font-size:
    clamp(
      2rem,
      2.7vw,
      3.6rem
    );

  font-weight: 400;

  line-height: 1;

  letter-spacing: -0.045em;
}


.filter-description {
  max-width: 470px;

  margin: 0;

  justify-self: end;

  color: #77726c;

  font-size:
    clamp(
      0.68rem,
      0.74vw,
      0.82rem
    );

  line-height: 1.65;
}


/* =========================================================
   FILTER CARD
========================================================= */

.filter-card {
  overflow: hidden;

  background: #ffffff;

  border:
    1px solid #ddd9d2;

  box-shadow:
    0
    12px
    35px
    rgba(0,0,0,0.035);
}


/* =========================================================
   BUY / RENT
========================================================= */

.filter-mode {
  display: flex;

  padding:
    0.7rem
    0.8rem
    0;

  border-bottom:
    1px solid #ebe8e3;
}


.filter-mode button {
  min-width: 82px;

  padding:
    0.8rem
    1.2rem;

  border: 0;

  border-bottom:
    2px solid transparent;

  background: transparent;

  color: #88837c;

  font-size: 0.67rem;

  font-weight: 700;

  cursor: pointer;
}


.filter-mode button.active {
  color: #111111;

  border-bottom-color: #111111;
}


/* =========================================================
   MAIN FILTER GRID
========================================================= */

.main-filter-grid {
  display: grid;

  grid-template-columns:
    1.2fr
    1.15fr
    1fr
    0.85fr
    auto
    auto;

  align-items: stretch;
}


/* =========================================================
   FIELD
========================================================= */

.filter-field {
  min-width: 0;

  padding:
    1rem
    clamp(
      0.8rem,
      1.2vw,
      1.2rem
    );

  border-right:
    1px solid #ebe8e3;
}


.field-label {
  display: block;

  margin-bottom: 0.4rem;

  color: #9a958e;

  font-size: 0.48rem;

  font-weight: 700;

  letter-spacing: 0.12em;

  text-transform: uppercase;
}


.filter-field select,
.advanced-select {
  width: 100%;

  border: 0;

  outline: none;

  background: transparent;

  color: #171717;

  font-size:
    clamp(
      0.66rem,
      0.72vw,
      0.8rem
    );

  font-weight: 500;

  cursor: pointer;
}


/* =========================================================
   MORE FILTER BUTTON
========================================================= */

.more-filter-button {
  min-width: 135px;

  display: flex;

  align-items: center;

  justify-content: center;

  gap: 0.6rem;

  padding:
    0
    1rem;

  border: 0;

  border-right:
    1px solid #ebe8e3;

  background: #faf9f7;

  color: #111111;

  font-size: 0.62rem;

  font-weight: 700;

  cursor: pointer;
}


.more-filter-button svg {
  width: 13px;

  height: 13px;

  stroke-width: 1.8;

  transition:
    transform 0.3s ease;
}


.more-filter-button svg.rotate {
  transform:
    rotate(180deg);
}


/* =========================================================
   SEARCH
========================================================= */

.search-button {
  min-width: 175px;

  display: flex;

  align-items: center;

  justify-content: center;

  gap: 0.7rem;

  margin: 0.5rem;

  border: 0;

  background: #111111;

  color: #ffffff;

  font-size: 0.62rem;

  font-weight: 700;

  letter-spacing: 0.03em;

  cursor: pointer;
}


.search-button span {
  transition:
    transform 0.3s ease;
}


.search-button:hover span {
  transform:
    translateX(4px);
}


/* =========================================================
   ACTIVE SUMMARY
========================================================= */

.active-summary {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 1rem;

  padding:
    0.6rem
    1rem;

  border-top:
    1px solid #ebe8e3;

  background: #faf9f7;
}


.active-summary span {
  color: #8d8881;

  font-size: 0.56rem;
}


.active-summary button {
  padding: 0;

  border: 0;

  background: transparent;

  color: #111111;

  font-size: 0.52rem;

  font-weight: 700;

  text-decoration: underline;

  cursor: pointer;
}


/* =========================================================
   ADVANCED PANEL
========================================================= */

.advanced-panel {
  margin-top: 1rem;

  overflow: hidden;

  background: #ffffff;

  border:
    1px solid #ddd9d2;

  box-shadow:
    0
    20px
    50px
    rgba(0,0,0,0.055);
}


/* =========================================================
   ADVANCED HEADER
========================================================= */

.advanced-head {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 2rem;

  padding:
    1.3rem
    1.5rem;

  border-bottom:
    1px solid #ebe8e3;
}


.advanced-head p {
  margin:
    0
    0
    0.25rem;

  color: #a0814b;

  font-size: 0.44rem;

  font-weight: 700;

  letter-spacing: 0.15em;
}


.advanced-head h3 {
  margin: 0;

  font-size: 1.15rem;

  font-weight: 500;
}


.close-more {
  width: 34px;

  height: 34px;

  border: 0;

  background: transparent;

  color: #111111;

  font-size: 1.4rem;

  font-weight: 300;

  cursor: pointer;
}


/* =========================================================
   ADVANCED GRID
========================================================= */

.advanced-grid {
  display: grid;

  grid-template-columns:
    repeat(
      4,
      minmax(0, 1fr)
    );

  gap:
    0;

  padding: 0;
}


.advanced-group {
  min-height: 165px;

  padding:
    1.3rem
    1.4rem;

  border-right:
    1px solid #ebe8e3;

  border-bottom:
    1px solid #ebe8e3;
}


.advanced-group:nth-child(4n) {
  border-right: 0;
}


.advanced-group h4 {
  margin:
    0
    0
    0.9rem;

  color: #111111;

  font-size: 0.66rem;

  font-weight: 700;
}


/* =========================================================
   CHOICE BUTTONS
========================================================= */

.choice-row {
  display: flex;

  flex-wrap: wrap;

  gap: 0.4rem;
}


.choice-row button {
  min-width: 46px;

  min-height: 36px;

  padding:
    0.45rem
    0.7rem;

  border:
    1px solid #d7d3cc;

  background: #ffffff;

  color: #5f5a55;

  font-size: 0.57rem;

  cursor: pointer;

  transition:
    background 0.25s ease,
    color 0.25s ease,
    border 0.25s ease;
}


.choice-row button:hover,
.choice-row button.selected {
  background: #111111;

  border-color: #111111;

  color: #ffffff;
}


/* =========================================================
   RANGE INPUTS
========================================================= */

.range-inputs {
  display: flex;

  align-items: center;

  gap: 0.5rem;
}


.range-inputs label {
  flex: 1;

  min-width: 0;
}


.range-inputs label span {
  display: block;

  margin-bottom: 0.3rem;

  color: #99938d;

  font-size: 0.46rem;
}


.range-inputs input {
  width: 100%;

  min-height: 38px;

  padding:
    0
    0.65rem;

  border:
    1px solid #d7d3cc;

  outline: none;

  color: #111111;

  font-size: 0.6rem;
}


.range-separator {
  margin-top: 0.8rem;

  color: #aaa59e;
}


/* =========================================================
   CHECK LIST
========================================================= */

.check-list {
  display: flex;

  flex-direction: column;

  gap: 0.55rem;
}


.check-list label,
.amenity-option {
  display: flex;

  align-items: center;

  gap: 0.55rem;

  color: #66615b;

  font-size: 0.57rem;

  cursor: pointer;
}


.check-list input,
.amenity-option input {
  display: none;
}


.custom-check {
  width: 15px;

  height: 15px;

  position: relative;

  flex-shrink: 0;

  border:
    1px solid #bcb7b0;

  background: #ffffff;
}


input:checked + .custom-check {
  background: #111111;

  border-color: #111111;
}


input:checked + .custom-check::after {
  content: "✓";

  position: absolute;

  top: 50%;

  left: 50%;

  transform:
    translate(
      -50%,
      -54%
    );

  color: #ffffff;

  font-size: 0.55rem;
}


/* =========================================================
   ADVANCED SELECT
========================================================= */

.advanced-select {
  min-height: 40px;

  padding:
    0
    0.65rem;

  border:
    1px solid #d7d3cc;

  background: #ffffff;
}


/* =========================================================
   AMENITIES
========================================================= */

.amenities-group {
  grid-column:
    span 2;
}


.amenities-grid {
  display: grid;

  grid-template-columns:
    repeat(
      2,
      minmax(0, 1fr)
    );

  gap:
    0.6rem
    1rem;
}


/* =========================================================
   ADVANCED FOOTER
========================================================= */

.advanced-footer {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 1rem;

  padding:
    1rem
    1.4rem;
}


.clear-button {
  border: 0;

  background: transparent;

  color: #68635d;

  font-size: 0.56rem;

  font-weight: 700;

  text-decoration: underline;

  cursor: pointer;
}


.show-button {
  min-width: 180px;

  min-height: 46px;

  display: flex;

  align-items: center;

  justify-content: center;

  gap: 0.7rem;

  border: 0;

  background: #111111;

  color: #ffffff;

  font-size: 0.58rem;

  font-weight: 700;

  cursor: pointer;
}


/* =========================================================
   TRANSITION
========================================================= */

.more-enter-active,
.more-leave-active {
  transition:
    opacity 0.3s ease,
    transform 0.3s ease;
}


.more-enter-from,
.more-leave-to {
  opacity: 0;

  transform:
    translateY(-8px);
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 1100px) {

  .main-filter-grid {
    grid-template-columns:
      repeat(
        2,
        minmax(0, 1fr)
      );
  }


  .filter-field {
    border-bottom:
      1px solid #ebe8e3;
  }


  .more-filter-button,
  .search-button {
    min-height: 58px;
  }


  .advanced-grid {
    grid-template-columns:
      repeat(
        2,
        minmax(0, 1fr)
      );
  }


  .advanced-group:nth-child(4n) {
    border-right:
      1px solid #ebe8e3;
  }


  .advanced-group:nth-child(2n) {
    border-right: 0;
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 600px) {

  .property-filter-section {
    padding:
      3rem
      0;
  }


  .filter-shell {
    width: 91vw;
  }


  .filter-heading {
    grid-template-columns:
      1fr;

    gap: 1rem;
  }


  .filter-description {
    justify-self: start;
  }


  .main-filter-grid {
    grid-template-columns: 1fr;
  }


  .filter-field {
    border-right: 0;
  }


  .more-filter-button {
    border-right: 0;

    border-bottom:
      1px solid #ebe8e3;
  }


  .search-button {
    margin: 0.6rem;

    min-height: 48px;
  }


  .advanced-grid {
    grid-template-columns: 1fr;
  }


  .advanced-group,
  .advanced-group:nth-child(2n),
  .advanced-group:nth-child(4n) {
    min-height: auto;

    border-right: 0;
  }


  .amenities-group {
    grid-column: auto;
  }


  .amenities-grid {
    grid-template-columns: 1fr;
  }


  .advanced-footer {
    align-items: stretch;

    flex-direction: column;
  }


  .show-button {
    width: 100%;
  }

}
</style>