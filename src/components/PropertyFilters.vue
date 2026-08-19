<template>
  <section class="property-section">

<div class="property-container">

  <!-- =========================
       HEADING
  ========================== -->
  <div class="section-heading">

    <div>
      <p class="eyebrow">
        PROPERTY COLLECTION
      </p>

      <h2>
        Find your ideal residence.
      </h2>
    </div>

    <p class="heading-copy">
      Explore selected residences and refine the collection
      by price, location, property type and lifestyle.
    </p>

  </div>


  <!-- =========================
       MOBILE FILTER BUTTON
  ========================== -->
  <button
    class="mobile-filter-button"
    type="button"
    @click="filterOpen = true"
  >
    <span>Filters</span>

    <span
      v-if="activeFilterCount"
      class="filter-count"
    >
      {{ activeFilterCount }}
    </span>
  </button>


  <!-- =========================
       MAIN LAYOUT
  ========================== -->
  <div class="property-layout">

    <!-- =====================================
         FILTER SIDEBAR
    ====================================== -->
    <aside
      class="filter-panel"
      :class="{ open: filterOpen }"
    >

      <!-- FILTER HEADER -->
      <div class="filter-header">

        <div>
          <span class="small-label">
            REFINE SEARCH
          </span>

          <h3>
            Filters
          </h3>
        </div>


        <div class="filter-header-actions">

          <button
            v-if="activeFilterCount"
            class="clear-top"
            type="button"
            @click="clearAll"
          >
            Clear
          </button>


          <button
            class="close-filter"
            type="button"
            @click="filterOpen = false"
          >
            ×
          </button>

        </div>

      </div>


      <!-- =====================================
           FILTER SCROLL
      ====================================== -->
      <div class="filter-scroll">

        <!-- =================================
             PRICE RANGE
        ================================== -->
        <div class="filter-section price-section">

          <h4>
            Price Range
          </h4>

          <p class="average-price">
            The average property price is
            <strong>LKR {{ averagePropertyPrice }}M</strong>
          </p>


          <!-- HISTOGRAM — now an ascending curve, so the
               bars visibly climb from PRICE_MIN to PRICE_MAX.
               This makes it obvious at a glance that moving
               the handles right raises the price threshold,
               and the highlighted region always shows exactly
               how much of that climb the current range covers. -->
          <div class="histogram">

            <span
              v-for="bar in priceBars"
              :key="bar.price"
              class="histogram-bar"
              :class="{
                active: isPriceBarActive(bar.price)
              }"
              :style="{
                height: `${bar.height}px`
              }"
              :title="`LKR ${bar.price}M`"
            ></span>

          </div>


          <!-- RANGE -->
          <div class="dual-slider">

            <div class="slider-track"></div>

            <div
              class="slider-active"
              :style="priceRangeStyle"
            ></div>


            <!-- MIN -->
            <input
              v-model.number="filters.minPrice"
              class="min-slider"
              type="range"
              :min="PRICE_MIN"
              :max="PRICE_MAX"
              :step="PRICE_STEP"
              @input="handleMinPrice"
            />


            <!-- MAX -->
            <input
              v-model.number="filters.maxPrice"
              class="max-slider"
              type="range"
              :min="PRICE_MIN"
              :max="PRICE_MAX"
              :step="PRICE_STEP"
              @input="handleMaxPrice"
            />

          </div>


          <!-- LIVE RANGE VALUES -->
          <div class="range-readout">
            <span>
              LKR {{ filters.minPrice }}M
            </span>

            <span>
              LKR {{ filters.maxPrice }}M
            </span>
          </div>


          <!-- MIN/MAX -->
          <div class="price-inputs">

            <label class="price-box">

              <span>
                Min price
              </span>

              <div>
                <small>
                  LKR
                </small>

                <input
                  v-model.number="filters.minPrice"
                  type="number"
                  :min="PRICE_MIN"
                  :max="PRICE_MAX"
                  :step="PRICE_STEP"
                  @input="handleMinPrice"
                  @blur="normalizePriceRange"
                />

                <b>M</b>
              </div>

            </label>


            <label class="price-box">

              <span>
                Max price
              </span>

              <div>
                <small>
                  LKR
                </small>

                <input
                  v-model.number="filters.maxPrice"
                  type="number"
                  :min="PRICE_MIN"
                  :max="PRICE_MAX"
                  :step="PRICE_STEP"
                  @input="handleMaxPrice"
                  @blur="normalizePriceRange"
                />

                <b>M</b>
              </div>

            </label>

          </div>

        </div>


        <!-- =================================
             PROPERTY TYPE
        ================================== -->
        <div class="filter-section">

          <h4>
            Property Type
          </h4>

          <div class="type-grid">

            <button
              v-for="type in propertyTypes"
              :key="type"
              type="button"
              :class="{
                selected:
                  filters.propertyType === type
              }"
              @click="
                filters.propertyType =
                  filters.propertyType === type
                    ? ''
                    : type
              "
            >

              <span>
                {{ type }}
              </span>

              <small>
                Browse properties
              </small>

            </button>

          </div>

        </div>


        <!-- =================================
             LOCATION
        ================================== -->
        <div class="filter-section">

          <h4>
            Location
          </h4>

          <div class="location-pills">

            <button
              v-for="location in locations"
              :key="location"
              type="button"
              :class="{
                selected:
                  filters.location === location
              }"
              @click="
                filters.location =
                  filters.location === location
                    ? ''
                    : location
              "
            >
              {{ location }}
            </button>

          </div>

        </div>


        <!-- =================================
             ROOMS
        ================================== -->
        <div class="filter-section">

          <h4>
            Rooms and Beds
          </h4>


          <!-- BEDROOMS -->
          <div class="room-row">

            <span class="room-label">
              Bedrooms
            </span>

            <div class="number-pills">

              <button
                v-for="item in bedroomOptions"
                :key="`bed-${item}`"
                type="button"
                :class="{
                  selected:
                    filters.bedrooms === item
                }"
                @click="filters.bedrooms = item"
              >
                {{ item }}
              </button>

            </div>

          </div>


          <!-- BATHROOMS -->
          <div class="room-row">

            <span class="room-label">
              Bathrooms
            </span>

            <div class="number-pills">

              <button
                v-for="item in bathroomOptions"
                :key="`bath-${item}`"
                type="button"
                :class="{
                  selected:
                    filters.bathrooms === item
                }"
                @click="filters.bathrooms = item"
              >
                {{ item }}
              </button>

            </div>

          </div>

        </div>


        <!-- =================================
             FLOOR AREA
        ================================== -->
        <div class="filter-section">

          <h4>
            Floor Area
          </h4>

          <div class="area-pills">

            <button
              v-for="item in floorAreas"
              :key="item.value"
              type="button"
              :class="{
                selected:
                  filters.floorArea === item.value
              }"
              @click="
                filters.floorArea =
                  filters.floorArea === item.value
                    ? ''
                    : item.value
              "
            >
              {{ item.label }}
            </button>

          </div>

        </div>


        <!-- =================================
             PROJECT STATUS
        ================================== -->
        <div class="filter-section">

          <h4>
            Project Status
          </h4>

          <div class="status-grid">

            <label
              v-for="status in projectStatuses"
              :key="status"
            >

              <input
                v-model="filters.projectStatus"
                type="checkbox"
                :value="status"
              />

              <span class="check-box"></span>

              <span>
                {{ status }}
              </span>

            </label>

          </div>

        </div>


        <!-- =================================
             MORE FILTERS
        ================================== -->
        <div class="more-filter">

          <button
            class="more-button"
            type="button"
            @click="moreOpen = !moreOpen"
          >

            <span>
              More Filters
            </span>

            <span class="more-right">

              <b v-if="advancedFilterCount">
                {{ advancedFilterCount }}
              </b>

              <svg
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                :class="{ rotate: moreOpen }"
              >
                <path d="M6 9l6 6 6-6" />
              </svg>

            </span>

          </button>


          <div
            v-if="moreOpen"
            class="more-content"
          >

            <!-- PARKING -->
            <div class="advanced-block">

              <h5>
                Parking
              </h5>

              <div class="small-pills">

                <button
                  v-for="item in parkingOptions"
                  :key="item"
                  type="button"
                  :class="{
                    selected:
                      filters.parking === item
                  }"
                  @click="
                    filters.parking =
                      filters.parking === item
                        ? ''
                        : item
                  "
                >
                  {{ item }}
                </button>

              </div>

            </div>


            <!-- VIEW -->
            <div class="advanced-block">

              <h5>
                View
              </h5>

              <div class="status-grid">

                <label
                  v-for="view in viewOptions"
                  :key="view"
                >

                  <input
                    v-model="filters.views"
                    type="checkbox"
                    :value="view"
                  />

                  <span class="check-box"></span>

                  <span>
                    {{ view }}
                  </span>

                </label>

              </div>

            </div>


            <!-- DEVELOPER -->
            <div class="advanced-block">

              <h5>
                Developer
              </h5>

              <select v-model="filters.developer">

                <option value="">
                  All developers
                </option>

                <option
                  v-for="developer in developers"
                  :key="developer"
                  :value="developer"
                >
                  {{ developer }}
                </option>

              </select>

            </div>


            <!-- FURNISHING -->
            <div class="advanced-block">

              <h5>
                Furnishing
              </h5>

              <select v-model="filters.furnishing">

                <option value="">
                  Any furnishing
                </option>

                <option
                  v-for="item in furnishingOptions"
                  :key="item"
                  :value="item"
                >
                  {{ item }}
                </option>

              </select>

            </div>


            <!-- AMENITIES -->
            <div class="advanced-block">

              <h5>
                Amenities
              </h5>

              <div class="status-grid">

                <label
                  v-for="amenity in amenities"
                  :key="amenity"
                >

                  <input
                    v-model="filters.amenities"
                    type="checkbox"
                    :value="amenity"
                  />

                  <span class="check-box"></span>

                  <span>
                    {{ amenity }}
                  </span>

                </label>

              </div>

            </div>

          </div>

        </div>

      </div>


      <!-- =====================================
           FILTER FOOTER
      ====================================== -->
      <div class="filter-footer">

        <button
          class="clear-bottom"
          type="button"
          @click="clearAll"
        >
          Clear all
        </button>


        <button
          class="show-button"
          type="button"
          @click="filterOpen = false"
        >
          Show {{ sortedProperties.length }} Properties
        </button>

      </div>

    </aside>


    <!-- MOBILE OVERLAY -->
    <div
      v-if="filterOpen"
      class="mobile-overlay"
      @click="filterOpen = false"
    ></div>


    <!-- =====================================
         RIGHT RESULTS
    ====================================== -->
    <main class="results">

      <!-- TOOLBAR -->
      <div class="results-toolbar">

        <div>

          <span>
            AVAILABLE COLLECTION
          </span>

          <h3>
            {{ sortedProperties.length }}
            Residences
          </h3>

        </div>


        <select v-model="sortBy">

          <option value="featured">
            Featured
          </option>

          <option value="low">
            Price: Low to High
          </option>

          <option value="high">
            Price: High to Low
          </option>

        </select>

      </div>


      <!-- PROPERTY CARDS -->
      <div
        v-if="sortedProperties.length"
        class="property-grid"
      >

        <article
          v-for="property in sortedProperties"
          :key="property.id"
          class="property-card"
        >

          <!-- IMAGE -->
          <div class="image-box">

            <img
              :src="property.image"
              :alt="property.name"
            />

            <!-- SMALL VERTICAL STATUS -->
            <div class="status-side">
              <span>
                {{ property.status }}
              </span>
            </div>

          </div>


          <!-- CARD CONTENT -->
          <div class="card-content">

            <span class="property-type">
              {{ property.type }}
            </span>


            <h3>
              {{ property.name }}
            </h3>


            <!-- LOCATION -->
            <div class="location-row">

              <svg
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="1.7"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path
                  d="M20 10c0 5-8 12-8 12S4 15 4 10a8 8 0 1 1 16 0Z"
                />

                <circle
                  cx="12"
                  cy="10"
                  r="2.5"
                />
              </svg>

              <span>
                {{ property.location }}
              </span>

            </div>


            <!-- BUILDER -->
            <div class="builder">

              <span>
                PRESENTED BY
              </span>

              <i></i>

              <strong>
                {{ property.developer }}
              </strong>

            </div>


            <!-- DESCRIPTION -->
            <p class="featured-description">
              {{ property.description }}
            </p>


            <!-- DETAILS -->
            <div class="details-row">

              <!-- BED -->
              <div class="detail">

                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.6"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M3 18v-7" />
                  <path d="M21 18v-5" />
                  <path d="M3 14h18" />
                  <path d="M6 11V8h5v3" />
                </svg>

                <span>
                  {{ property.bedText }}
                </span>

              </div>


              <!-- SIZE -->
              <div class="detail">

                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.6"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M4 9V4h5" />
                  <path d="M15 4h5v5" />
                  <path d="M20 15v5h-5" />
                  <path d="M9 20H4v-5" />
                </svg>

                <span>
                  {{ property.size }}
                </span>

              </div>


              <!-- BATH -->
              <div class="detail">

                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.6"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M4 13h16" />

                  <path
                    d="M5 13v2a5 5 0 0 0 5 5h4a5 5 0 0 0 5-5v-2"
                  />

                  <path
                    d="M7 13V7a3 3 0 0 1 6 0"
                  />
                </svg>

                <span>
                  {{ property.bathText }}
                </span>

              </div>

            </div>


            <!-- FOOTER -->
            <div class="card-footer">

              <a
                href="#"
                class="explore-link"
              >
                Explore Residence
                <span>↗</span>
              </a>


              <div class="price-right">

                <small>
                  STARTING FROM
                </small>

                <div>
                  <span>
                    LKR
                  </span>

                  <strong>
                    {{ property.price }}M
                  </strong>
                </div>

              </div>

            </div>

          </div>

        </article>

      </div>


      <!-- EMPTY -->
      <div
        v-else
        class="empty"
      >
        <h3>
          No properties found.
        </h3>

        <p>
          Try changing or removing some filters.
        </p>

        <button
          type="button"
          @click="clearAll"
        >
          Clear Filters
        </button>
      </div>

    </main>

  </div>

</div>

  </section>
</template>

<script setup>
import {
  reactive,
  ref,
  computed
} from "vue";


/* =========================
   IMAGES
========================= */

import thalpeImage
  from "../images/1.jpg";

import colomboImage
  from "../images/3.jpg";

import galleImage
  from "../images/11.png";

import weligamaImage
  from "../images/5.png";



/* =========================
   STATE
========================= */

const filterOpen =
  ref(false);

const moreOpen =
  ref(false);

const sortBy =
  ref("featured");


const filters =
  reactive({

    minPrice: 24,

    maxPrice: 100,

    propertyType: "",

    location: "",

    bedrooms: "Any",

    bathrooms: "Any",

    floorArea: "",

    projectStatus: [],

    parking: "",

    views: [],

    developer: "",

    furnishing: "",

    amenities: []

  });


/* =========================
   PRICE GRAPH
========================= */

/*
  One chart bar represents one real price point from
  PRICE_MIN to PRICE_MAX. Because each bar has its own
  `price`, the highlighted chart always matches the
  selected Min and Max values exactly.
*/

const PRICE_MIN = 10;
const PRICE_MAX = 150;
const PRICE_STEP = 1;
const PRICE_GAP = 1;
const BAR_COUNT = 45;


/* Average from the actual property data is declared later,
   so this display uses the collection's intended average. */
const averagePropertyPrice = 48;


/* =========================================================
   ASCENDING PRICE CURVE
   ---------------------------------------------------------
   Bars now climb steadily from PRICE_MIN to PRICE_MAX
   instead of forming a bell curve. This makes the chart
   read literally as "price increasing left to right" —
   dragging the min/max handles right visibly moves the
   highlighted (active) region further up the climb.

   Height formula: a slightly eased curve (power 1.25) so
   the increase feels natural rather than perfectly linear,
   while always strictly increasing bar to bar.
========================================================= */
const histogramHeights = Array.from(
  { length: BAR_COUNT },
  (_, i) => Math.round(4 + 88 * Math.pow(i / (BAR_COUNT - 1), 1.25))
);


const priceBars =
  histogramHeights.map(
    (height, index, bars) => {

      const percent =
        bars.length === 1
          ? 0
          : index / (bars.length - 1);

      const price =
        Math.round(
          PRICE_MIN +
          percent *
          (PRICE_MAX - PRICE_MIN)
        );

      return {
        price,
        height
      };

    }
  );


/* Highlight a bar only when its REAL price lies
   between selected min and max. */
function isPriceBarActive(price) {

  return (
    price >= filters.minPrice &&
    price <= filters.maxPrice
  );

}


/* Exact handle positions on the 10M–150M scale */
const minPricePercent =
  computed(() => {

    return (
      (
        filters.minPrice -
        PRICE_MIN
      ) /
      (
        PRICE_MAX -
        PRICE_MIN
      )
    ) * 100;

  });


const maxPricePercent =
  computed(() => {

    return (
      (
        filters.maxPrice -
        PRICE_MIN
      ) /
      (
        PRICE_MAX -
        PRICE_MIN
      )
    ) * 100;

  });


const priceRangeStyle =
  computed(() => {

    return {
      left:
        `${minPricePercent.value}%`,

      width:
        `${
          maxPricePercent.value -
          minPricePercent.value
        }%`
    };

  });


function handleMinPrice() {

  let value =
    Number(filters.minPrice);

  if (!Number.isFinite(value)) {
    value = PRICE_MIN;
  }

  value =
    Math.max(
      PRICE_MIN,
      Math.min(
        value,
        filters.maxPrice -
        PRICE_GAP
      )
    );

  filters.minPrice =
    Math.round(
      value / PRICE_STEP
    ) * PRICE_STEP;

}


function handleMaxPrice() {

  let value =
    Number(filters.maxPrice);

  if (!Number.isFinite(value)) {
    value = PRICE_MAX;
  }

  value =
    Math.min(
      PRICE_MAX,
      Math.max(
        value,
        filters.minPrice +
        PRICE_GAP
      )
    );

  filters.maxPrice =
    Math.round(
      value / PRICE_STEP
    ) * PRICE_STEP;

}


function normalizePriceRange() {

  let minValue =
    Number(filters.minPrice);

  let maxValue =
    Number(filters.maxPrice);


  if (!Number.isFinite(minValue)) {
    minValue = PRICE_MIN;
  }

  if (!Number.isFinite(maxValue)) {
    maxValue = PRICE_MAX;
  }


  minValue =
    Math.max(
      PRICE_MIN,
      Math.min(
        minValue,
        PRICE_MAX - PRICE_GAP
      )
    );


  maxValue =
    Math.min(
      PRICE_MAX,
      Math.max(
        maxValue,
        PRICE_MIN + PRICE_GAP
      )
    );


  if (
    minValue >
    maxValue - PRICE_GAP
  ) {
    minValue =
      maxValue - PRICE_GAP;
  }


  filters.minPrice =
    Math.round(
      minValue / PRICE_STEP
    ) * PRICE_STEP;

  filters.maxPrice =
    Math.round(
      maxValue / PRICE_STEP
    ) * PRICE_STEP;

}


/* =========================
   FILTER OPTIONS
========================= */

const propertyTypes = [
  "Apartments",
  "Villas",
  "Houses",
  "Penthouses",
  "Beachfront"
];


const locations = [
  "Colombo",
  "Thalawathugoda",
  "Galle",
  "Thalpe",
  "Negombo",
  "Nuwara Eliya"
];


const bedroomOptions = [
  "Any",
  "1",
  "2",
  "3",
  "4",
  "5+"
];


const bathroomOptions = [
  "Any",
  "1",
  "2",
  "3",
  "4+"
];


const floorAreas = [
  {
    label: "<750",
    value: "under750"
  },

  {
    label: "750–1K",
    value: "750-1000"
  },

  {
    label: "1K–1.5K",
    value: "1000-1500"
  },

  {
    label: "1.5K–2.5K",
    value: "1500-2500"
  },

  {
    label: "2.5K+",
    value: "2500+"
  }
];


const projectStatuses = [
  "Newly Launched",
  "Under Construction",
  "Ready to Move",
  "Completed"
];


const parkingOptions = [
  "No Parking",
  "1 Slot",
  "2+ Slots"
];


const viewOptions = [
  "Ocean View",
  "City View",
  "Garden View",
  "Pool View",
  "Mountain View"
];


const developers = [
  "Odiliya Premier",
  "Home Lands Skyline",
  "Prime Residencies"
];


const furnishingOptions = [
  "Unfurnished",
  "Semi-Furnished",
  "Fully Furnished"
];


const amenities = [
  "Pool",
  "Gym",
  "Rooftop",
  "Kids Area",
  "Security",
  "Concierge",
  "EV Charging"
];


/* =========================
   PROPERTIES
========================= */

const properties = [

  {
    id: 1,

    name:
      "Icon V Thalpe",

    type:
      "Beachfront Residence",

    propertyType:
      "Beachfront",

    location:
      "Thalpe, Galle",

    locationFilter:
      "Thalpe",

    developer:
      "Odiliya Premier",

    description:
      "Refined beachfront living with ocean views and contemporary coastal design.",

    price:
      24,

    beds:
      [2, 3],

    bedText:
      "2–3 Bed",

    baths:
      2,

    bathText:
      "2 Bath",

    size:
      "1,150–1,850 sq.ft",

    minSize:
      1150,

    projectStatus:
      "Ready to Move",

    parking:
      "1 Slot",

    view:
      "Ocean View",

    furnishing:
      "Fully Furnished",

    amenities:
      [
        "Pool",
        "Gym",
        "Security"
      ],

    status:
      "FEATURED",

    image:
      thalpeImage
  },


  {
    id: 2,

    name:
      "Oceanista Residences",

    type:
      "Luxury Apartments",

    propertyType:
      "Apartments",

    location:
      "Galle",

    locationFilter:
      "Galle",

    developer:
      "Odiliya Premier",

    description:
      "Contemporary apartments designed around natural light, privacy and coastal living.",

    price:
      25,

    beds:
      [1, 2, 3],

    bedText:
      "1–3 Bed",

    baths:
      2,

    bathText:
      "2 Bath",

    size:
      "800–2,400 sq.ft",

    minSize:
      800,

    projectStatus:
      "Newly Launched",

    parking:
      "1 Slot",

    view:
      "Ocean View",

    furnishing:
      "Semi-Furnished",

    amenities:
      [
        "Pool",
        "Gym",
        "Rooftop"
      ],

    status:
      "NEW",

    image:
      weligamaImage
  },


  {
    id: 3,

    name:
      "Platinum 10",

    type:
      "Private Pool Villas",

    propertyType:
      "Villas",

    location:
      "Colombo",

    locationFilter:
      "Colombo",

    developer:
      "Odiliya Premier",

    description:
      "Generous private villas combining refined architecture, privacy and modern convenience.",

    price:
      84,

    beds:
      [4],

    bedText:
      "4 Bed",

    baths:
      4,

    bathText:
      "4 Bath",

    size:
      "3,500+ sq.ft",

    minSize:
      3500,

    projectStatus:
      "Under Construction",

    parking:
      "2+ Slots",

    view:
      "Garden View",

    furnishing:
      "Fully Furnished",

    amenities:
      [
        "Pool",
        "Gym",
        "Security",
        "Concierge"
      ],

    status:
      "LIMITED",

    image:
      colomboImage
  },


  {
    id: 4,

    name:
      "Ocean House",

    type:
      "Luxury Coastal House",

    propertyType:
      "Houses",

    location:
      "Galle",

    locationFilter:
      "Galle",

    developer:
      "Odiliya Premier",

    description:
      "A private coastal home shaped around elegant interiors, light and relaxed living.",

    price:
      42,

    beds:
      [3],

    bedText:
      "3 Bed",

    baths:
      3,

    bathText:
      "3 Bath",

    size:
      "1,750–2,600 sq.ft",

    minSize:
      1750,

    projectStatus:
      "Completed",

    parking:
      "1 Slot",

    view:
      "Ocean View",

    furnishing:
      "Fully Furnished",

    amenities:
      [
        "Pool",
        "Security",
        "Concierge"
      ],

    status:
      "READY",

    image:
      galleImage
  },


  {
    id: 5,

    name:
      "Colombo Penthouse",

    type:
      "Luxury Penthouse",

    propertyType:
      "Penthouses",

    location:
      "Colombo",

    locationFilter:
      "Colombo",

    developer:
      "Prime Residencies",

    description:
      "An elevated residence with skyline views, sophisticated interiors and private amenities.",

    price:
      68,

    beds:
      [3],

    bedText:
      "3 Bed",

    baths:
      3,

    bathText:
      "3 Bath",

    size:
      "2,450 sq.ft",

    minSize:
      2450,

    projectStatus:
      "Under Construction",

    parking:
      "2+ Slots",

    view:
      "City View",

    furnishing:
      "Fully Furnished",

    amenities:
      [
        "Pool",
        "Gym",
        "Rooftop",
        "Security"
      ],

    status:
      "FEATURED",

    image:
      colomboImage
  }

];


/* =========================
   FILTER HELPERS
========================= */

function matchesBedrooms(property) {

  if (
    filters.bedrooms ===
    "Any"
  ) {
    return true;
  }


  if (
    filters.bedrooms ===
    "5+"
  ) {

    return property.beds.some(
      bed =>
        bed >= 5
    );

  }


  return property.beds.includes(
    Number(filters.bedrooms)
  );

}


function matchesBathrooms(property) {

  if (
    filters.bathrooms ===
    "Any"
  ) {
    return true;
  }


  if (
    filters.bathrooms ===
    "4+"
  ) {

    return property.baths >= 4;

  }


  return (
    property.baths ===
    Number(filters.bathrooms)
  );

}


function matchesArea(property) {

  const size =
    property.minSize;


  switch (
    filters.floorArea
  ) {

    case "under750":
      return size < 750;


    case "750-1000":
      return (
        size >= 750 &&
        size <= 1000
      );


    case "1000-1500":
      return (
        size >= 1000 &&
        size <= 1500
      );


    case "1500-2500":
      return (
        size >= 1500 &&
        size <= 2500
      );


    case "2500+":
      return size >= 2500;


    default:
      return true;
  }

}


/* =========================
   FILTER
========================= */

const filteredProperties =
  computed(() => {

    return properties.filter(
      property => {

        if (
          property.price <
          filters.minPrice ||
          property.price >
          filters.maxPrice
        ) {
          return false;
        }


        if (
          filters.propertyType &&
          property.propertyType !==
          filters.propertyType
        ) {
          return false;
        }


        if (
          filters.location &&
          property.locationFilter !==
          filters.location
        ) {
          return false;
        }


        if (
          !matchesBedrooms(property)
        ) {
          return false;
        }


        if (
          !matchesBathrooms(property)
        ) {
          return false;
        }


        if (
          !matchesArea(property)
        ) {
          return false;
        }


        if (
          filters.projectStatus.length &&
          !filters.projectStatus.includes(
            property.projectStatus
          )
        ) {
          return false;
        }


        if (
          filters.parking &&
          property.parking !==
          filters.parking
        ) {
          return false;
        }


        if (
          filters.views.length &&
          !filters.views.includes(
            property.view
          )
        ) {
          return false;
        }


        if (
          filters.developer &&
          property.developer !==
          filters.developer
        ) {
          return false;
        }


        if (
          filters.furnishing &&
          property.furnishing !==
          filters.furnishing
        ) {
          return false;
        }


        if (
          filters.amenities.length &&
          !filters.amenities.every(
            amenity =>
              property.amenities
                .includes(amenity)
          )
        ) {
          return false;
        }


        return true;

      }
    );

  });


/* =========================
   SORT
========================= */

const sortedProperties =
  computed(() => {

    const results =
      [
        ...filteredProperties.value
      ];


    if (
      sortBy.value ===
      "low"
    ) {

      results.sort(
        (a, b) =>
          a.price -
          b.price
      );

    }


    if (
      sortBy.value ===
      "high"
    ) {

      results.sort(
        (a, b) =>
          b.price -
          a.price
      );

    }


    return results;

  });


/* =========================
   FILTER COUNT
========================= */

const advancedFilterCount =
  computed(() => {

    let count =
      0;


    if (filters.parking)
      count++;


    if (filters.views.length)
      count++;


    if (filters.developer)
      count++;


    if (filters.furnishing)
      count++;


    if (filters.amenities.length)
      count++;


    return count;

  });


const activeFilterCount =
  computed(() => {

    let count =
      advancedFilterCount.value;


    if (
      filters.minPrice !== 24 ||
      filters.maxPrice !== 100
    ) count++;


    if (
      filters.propertyType
    ) count++;


    if (
      filters.location
    ) count++;


    if (
      filters.bedrooms !==
      "Any"
    ) count++;


    if (
      filters.bathrooms !==
      "Any"
    ) count++;


    if (
      filters.floorArea
    ) count++;


    if (
      filters.projectStatus.length
    ) count++;


    return count;

  });


/* =========================
   CLEAR
========================= */

function clearAll() {

  filters.minPrice =
    24;

  filters.maxPrice =
    100;

  filters.propertyType =
    "";

  filters.location =
    "";

  filters.bedrooms =
    "Any";

  filters.bathrooms =
    "Any";

  filters.floorArea =
    "";

  filters.projectStatus =
    [];

  filters.parking =
    "";

  filters.views =
    [];

  filters.developer =
    "";

  filters.furnishing =
    "";

  filters.amenities =
    [];

}

</script>

<style scoped>

/* =========================================================
   GLOBAL
========================================================= */

.property-section,
.property-section *,
.property-section *::before,
.property-section *::after {
  box-sizing: border-box;
  font-family: sans-serif !important;
}


button,
select,
input {
  font: inherit;
}


/* =========================================================
   PAGE
========================================================= */

.property-section {
  width: 100%;
  padding: 70px 0;
  background: #f5f4f1;
  color: #171717;
}


.property-container {
  width: min(94%, 1650px);
  margin: 0 auto;
}


/* =========================================================
   HEADING
========================================================= */

.section-heading {
  display: grid;
  grid-template-columns: 1fr 0.7fr;
  align-items: end;

  gap: 80px;

  margin-bottom: 30px;
  padding-bottom: 24px;

  border-bottom: 1px solid #dedbd6;
}


.eyebrow {
  margin: 0 0 8px;

  color: #987b49;

  font-size: 12px;
  font-weight: 700;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}


.section-heading h2 {
   margin: 0;

  font-size:
    clamp(
      2.1rem,
      2.3vw,
      3.7rem
    );

  font-weight: 400;

  line-height: 1;

  letter-spacing: -0.045em;
}


.heading-copy {
  max-width: 470px;

  margin: 0;

  justify-self: end;

  color: #77716a;

  font-size: 15px;

  line-height: 1.7;
}


/* =========================================================
   LAYOUT
========================================================= */

.property-layout {
  display: grid;

  grid-template-columns:
    310px
    minmax(0, 1fr);

  gap: 28px;

  align-items: start;
}


/* =========================================================
   FILTER
========================================================= */

.filter-panel {
  position: sticky;

  top: 20px;

  max-height:
    calc(100vh - 40px);

  display: flex;

  flex-direction: column;

  overflow: hidden;

  background: #ffffff;

  border: 1px solid #e0dfdc;

  border-radius: 16px;

  box-shadow:
    0 10px 35px
    rgba(0, 0, 0, 0.045);
}


/* =========================================================
   FILTER HEADER
========================================================= */

.filter-header {
  min-height: 70px;

  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 15px;

  padding: 15px 17px;

  border-bottom: 1px solid #eeeeec;
}


.small-label {
  display: block;

  margin-bottom: 3px;

  color: #aa8b53;

  font-size: 10px;

  font-weight: 700;

  letter-spacing: 0.16em;
}


.filter-header h3 {
  margin: 0;

  font-size: 18px;

  font-weight: 650;
}


.filter-header-actions {
  display: flex;
  align-items: center;
  gap: 10px;
}


.clear-top {
  padding: 0;

  border: 0;

  background: transparent;

  color: #967b4d;

  font-size: 12px;

  text-decoration: underline;

  cursor: pointer;
}


.close-filter {
  display: none;

  border: 0;

  background: transparent;

  font-size: 22px;

  cursor: pointer;
}


/* =========================================================
   SCROLL
========================================================= */

.filter-scroll {
  flex: 1;

  overflow-y: auto;

  scrollbar-width: thin;
}


/* =========================================================
   FILTER SECTION
========================================================= */

.filter-section {
  padding: 16px 17px;

  border-bottom: 1px solid #eeeeec;
}


.filter-section h4 {
  margin: 0 0 10px;

  font-size: 14px;

  font-weight: 650;
}


/* =========================================================
   PRICE - ACCURATE DUAL RANGE
========================================================= */

.average-price {
  margin: -5px 0 0;

  color: #96928c;

  font-size: 12px;

  line-height: 1.4;
}


.average-price strong {
  color: #66615c;

  font-weight: 600;
}


/* HISTOGRAM — ASCENDING PRICE CLIMB */

.histogram {
  position: relative;

  height: 96px;

  display: flex;

  align-items: flex-end;

  justify-content: center;

  gap: 3px;

  margin-top: 8px;

  padding:
    0
    10px
    7px;

  overflow: visible;
}


/* subtle baseline under the distribution */
.histogram::after {
  content: "";

  position: absolute;

  left: 8px;
  right: 8px;
  bottom: 0;

  height: 1px;

  background: #e3e2df;
}


.histogram-bar {
  position: relative;

  z-index: 2;

  flex: 1 1 0;

  min-width: 2px;
  max-width: 5px;

  background: #e2e1de;

  border-radius:
    3px
    3px
    0
    0;

  opacity: 1;

  transform-origin: bottom;

  transition:
    background 0.18s ease,
    opacity 0.18s ease,
    transform 0.18s ease;
}


/* Selected Min → Max area */
.histogram-bar.active {
  background: linear-gradient(180deg, #c2a46e, #4e4e4b 85%);
}


/* edge bars stay softer for a premium fade */
.histogram-bar:not(.active) {
  opacity: 0.55;
}


.histogram-bar:hover {
  transform: scaleY(1.04);
}


.histogram-bar.active:hover {
  background: linear-gradient(180deg, #c2a46e, #242424 85%);
}


/* =========================================================
   DUAL SLIDER
========================================================= */

.dual-slider {
  position: relative;

  width: 100%;

  height: 32px;

  margin-top: -7px;
}


.slider-track,
.slider-active {
  position: absolute;

  top: 50%;

  height: 2px;

  transform: translateY(-50%);

  pointer-events: none;
}


.slider-track {
  left: 0;
  right: 0;

  background: #dededc;

  z-index: 1;
}


.slider-active {
  background: #232323;

  z-index: 2;
}


.dual-slider input {
  position: absolute;

  left: 0;
  top: 0;

  width: 100%;
  height: 34px;

  margin: 0;
  padding: 0;

  appearance: none;
  -webkit-appearance: none;

  background: transparent;

  pointer-events: none;

  outline: none;
}


.dual-slider .min-slider {
  z-index: 4;
}


.dual-slider .max-slider {
  z-index: 5;
}


.dual-slider input::-webkit-slider-runnable-track {
  height: 2px;

  background: transparent;

  border: 0;
}


.dual-slider input::-webkit-slider-thumb {
  width: 16px;
  height: 16px;

  margin-top: -7px;

  appearance: none;
  -webkit-appearance: none;

  border: 2px solid #ffffff;

  border-radius: 50%;

  background: #242424;

  box-shadow:
    0 0 0 1px #242424;

  pointer-events: auto;

  cursor: grab;
}


.dual-slider input::-webkit-slider-thumb:active {
  cursor: grabbing;
}


.dual-slider input::-moz-range-track {
  height: 2px;

  background: transparent;

  border: 0;
}


.dual-slider input::-moz-range-thumb {
  width: 14px;
  height: 14px;

  border: 2px solid #ffffff;

  border-radius: 50%;

  background: #242424;

  box-shadow:
    0 0 0 1px #242424;

  pointer-events: auto;

  cursor: grab;
}


/* LIVE MIN/MAX LABELS */

.range-readout {
  display: flex;

  align-items: center;

  justify-content: space-between;

  margin-top: -2px;
  margin-bottom: 8px;

  color: #66615c;

  font-size: 11px;

  font-weight: 700;
}


/* =========================================================
   PRICE INPUTS
========================================================= */

.price-inputs {
  display: grid;

  grid-template-columns:
    1fr 1fr;

  gap: 10px;

  margin-top: 3px;
}


.price-box {
  padding: 9px 10px;

  border: 1px solid #e1e1df;

  border-radius: 6px;

  background: #ffffff;
}


.price-box:focus-within {
  border-color: #77736d;
}


.price-box > span {
  display: block;

  margin-bottom: 5px;

  color: #9b9792;

  font-size: 10px;
}


.price-box > div {
  display: flex;

  align-items: baseline;

  gap: 3px;
}


.price-box small {
  color: #8a7553;

  font-size: 10px;

  font-weight: 700;
}


.price-box input {
  width: 100%;

  min-width: 0;

  padding: 0;

  border: 0;

  outline: 0;

  background: transparent;

  color: #222222;

  font-size: 13px;

  font-weight: 600;
}


.price-box b {
  color: #66615c;

  font-size: 11px;

  font-weight: 600;
}


.price-box
input::-webkit-inner-spin-button,
.price-box
input::-webkit-outer-spin-button {
  margin: 0;

  -webkit-appearance: none;
}


/* =========================================================
   PROPERTY TYPES
========================================================= */

.type-grid {
  display: grid;

  grid-template-columns:
    1fr 1fr;

  gap: 7px;
}


.type-grid button {
  min-height: 58px;

  display: flex;

  flex-direction: column;

  align-items: flex-start;

  justify-content: center;

  padding: 9px 10px;

  border: 1px solid #dfddda;

  border-radius: 8px;

  background: #ffffff;

  color: #303030;

  text-align: left;

  cursor: pointer;
}


.type-grid button > span {
  font-size: 12px;

  font-weight: 700;
}


.type-grid button small {
  margin-top: 3px;

  color: #aaa6a0;

  font-size: 9px;
}


.type-grid button:hover,
.type-grid button.selected {
  border-color: #222222;

  box-shadow:
    inset
    0 0 0
    1px #222222;
}


/* =========================================================
   LOCATIONS
========================================================= */

.location-pills {
  display: flex;

  flex-wrap: wrap;

  gap: 5px;
}


.location-pills button {
  min-height: 30px;

  padding: 0 10px;

  border: 1px solid #dfddda;

  border-radius: 100px;

  background: #ffffff;

  color: #66615c;

  font-size: 11px;

  cursor: pointer;
}


.location-pills button.selected,
.location-pills button:hover {
  border-color: #222222;

  background: #222222;

  color: #ffffff;
}


/* =========================================================
   ROOMS
========================================================= */

.room-row + .room-row {
  margin-top: 12px;
}


.room-label {
  display: block;

  margin-bottom: 6px;

  color: #77716a;

  font-size: 11px;
}


.number-pills {
  display: grid;

  grid-template-columns:
    repeat(6, 1fr);

  gap: 5px;
}


.number-pills button {
  height: 27px;

  padding: 0;

  border: 0;

  border-radius: 100px;

  background: #f2f2f1;

  color: #8a8680;

  font-size: 11px;

  cursor: pointer;
}


.number-pills button.selected,
.number-pills button:hover {
  background: #252525;

  color: #ffffff;
}


/* =========================================================
   FLOOR AREA
========================================================= */

.area-pills,
.small-pills {
  display: flex;

  flex-wrap: wrap;

  gap: 5px;
}


.area-pills button,
.small-pills button {
  min-height: 30px;

  padding: 0 9px;

  border: 1px solid #dfddda;

  border-radius: 100px;

  background: #ffffff;

  color: #68635d;

  font-size: 11px;

  cursor: pointer;
}


.area-pills button.selected,
.small-pills button.selected {
  border-color: #222222;

  background: #222222;

  color: #ffffff;
}


/* =========================================================
   CHECKBOX
========================================================= */

.status-grid {
  display: grid;

  grid-template-columns:
    1fr 1fr;

  gap: 9px;
}


.status-grid label {
  display: flex;

  align-items: center;

  gap: 6px;

  color: #65605a;

  font-size: 11px;

  cursor: pointer;
}


.status-grid input {
  display: none;
}


.check-box {
  width: 15px;

  height: 15px;

  position: relative;

  flex-shrink: 0;

  border: 1px solid #bbb8b3;

  border-radius: 3px;
}


.status-grid
input:checked
+
.check-box {
  border-color: #222222;

  background: #222222;
}


.status-grid
input:checked
+
.check-box::after {
  content: "✓";

  position: absolute;

  top: 50%;

  left: 50%;

  transform:
    translate(-50%, -55%);

  color: #ffffff;

  font-size: 10px;
}


/* =========================================================
   MORE
========================================================= */

.more-button {
  width: 100%;

  min-height: 50px;

  display: flex;

  align-items: center;

  justify-content: space-between;

  padding: 0 17px;

  border: 0;

  background: #fafaf9;

  color: #222222;

  font-size: 13px;

  font-weight: 700;

  cursor: pointer;
}


.more-right {
  display: flex;

  align-items: center;

  gap: 7px;
}


.more-right b {
  width: 19px;

  height: 19px;

  display: grid;

  place-items: center;

  border-radius: 50%;

  background: #a08555;

  color: #ffffff;

  font-size: 10px;
}


.more-right svg {
  width: 13px;

  transition: transform 0.25s ease;
}


.more-right svg.rotate {
  transform: rotate(180deg);
}


.more-content {
  padding: 0 17px 12px;

  background: #fafaf9;
}


.advanced-block {
  padding: 12px 0;

  border-top: 1px solid #eceae7;
}


.advanced-block h5 {
  margin: 0 0 8px;

  font-size: 13px;
}


.advanced-block select {
  width: 100%;

  min-height: 37px;

  padding: 0 9px;

  border: 1px solid #dfddda;

  border-radius: 5px;

  outline: none;

  background: #ffffff;

  color: #59544e;

  font-size: 12px;
}


/* =========================================================
   FILTER FOOTER
========================================================= */

.filter-footer {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 10px;

  padding: 11px 13px;

  border-top: 1px solid #eeeeec;

  background: #ffffff;
}


.clear-bottom {
  border: 0;

  background: transparent;

  color: #6e6963;

  font-size: 12px;

  text-decoration: underline;

  cursor: pointer;
}


.show-button {
  min-height: 42px;

  flex: 1;

  padding: 0 13px;

  border: 0;

  border-radius: 5px;

  background: #222222;

  color: #ffffff;

  font-size: 12px;

  font-weight: 700;

  cursor: pointer;
}


/* =========================================================
   RESULTS
========================================================= */

.results {
  min-width: 0;
}


.results-toolbar {
  min-height: 54px;

  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 20px;

  margin-bottom: 14px;

  padding-bottom: 12px;

  border-bottom: 1px solid #dedbd6;
}


.results-toolbar span {
  display: block;

  margin-bottom: 4px;

  color: #9a7d49;

  font-size: 10px;

  font-weight: 700;

  letter-spacing: 0.12em;
}


.results-toolbar h3 {
  margin: 0;

  font-size: 20px;

  font-weight: 600;
}


.results-toolbar select {
  min-height: 37px;

  padding: 0 10px;

  border: 1px solid #d9d6d1;

  background: #ffffff;

  font-size: 12px;
}


/* =========================================================
   FEATURED RESIDENCE CARDS
========================================================= */

.property-grid {
  display: grid;

  grid-template-columns:
    repeat(
      3,
      minmax(0, 1fr)
    );

  gap:
    clamp(
      0.8rem,
      1vw,
      1.1rem
    );
}


/* CARD */

.property-card {
  min-width: 0;

  overflow: hidden;

  background: #ffffff;

  border:
    1px solid #e1ded8;

  transition:
    transform 0.4s ease,
    box-shadow 0.4s ease;
}


.property-card:hover {
  transform:
    translateY(-5px);

  box-shadow:
    0 18px 45px
    rgba(0, 0, 0, 0.07);
}


/* IMAGE */

.image-box {
  position: relative;

  width: 100%;

  height:
    clamp(
      230px,
      21vw,
      340px
    );

  overflow: hidden;

  background: #dddddd;
}


.image-box img {
  width: 100%;
  height: 100%;

  display: block;

  object-fit: cover;

  transition:
    transform 0.7s ease;
}


.property-card:hover
.image-box img {
  transform:
    scale(1.04);
}


/* STATUS */

.status-side {
  position: absolute;

  z-index: 6;

  top: 0;
  left: 0;

  width:
    clamp(
      30px,
      2.2vw,
      36px
    );

  height:
    clamp(
      105px,
      9vw,
      135px
    );

  display: flex;

  align-items: center;

  justify-content: center;

  background:
    rgba(15, 15, 15, 0.95);

  color: #ffffff;

  overflow: hidden;
}


.status-side span {
  display: block;

  color: #ffffff;

  font-size:
    clamp(9px, 0.55vw, 10px);

  font-weight: 500;

  letter-spacing: 0.17em;

  line-height: 1;

  text-transform: uppercase;

  white-space: nowrap;

  writing-mode: vertical-rl;

  text-orientation: mixed;
}


/* CONTENT */

.card-content {
  padding:
    clamp(
      1rem,
      1.25vw,
      1.3rem
    );
}


.property-type {
  display: block;

  margin-bottom: 0.35rem;

  color: #96918a;

  font-size:
    clamp(11px, 0.68vw, 13px);

  font-weight: 500;
}


.card-content h3 {
  margin: 0;

  color: #111111;

  font-size:
    clamp(20px, 1.35vw, 25px);

  font-weight: 400;

  line-height: 1.15;

  letter-spacing: -0.025em;
}


/* LOCATION */

.location-row {
  display: flex;

  align-items: center;

  gap: 0.38rem;

  margin-top: 0.55rem;

  color: #35312d;
}


.location-row svg {
  width: 13px;
  height: 13px;

  flex-shrink: 0;

  color: #a4864d;
}


.location-row span {
  font-size:
    clamp(11px, 0.68vw, 13px);

  font-weight: 600;
}


/* BUILDER */

.builder {
  display: flex;

  align-items: center;

  gap: 0.4rem;

  margin-top: 0.5rem;
}


.builder span {
  color: #aaa49c;

  font-size: clamp(8px, 0.48vw, 9px);

  font-weight: 700;

  letter-spacing: 0.12em;

  white-space: nowrap;
}


.builder i {
  width: 15px;
  height: 1px;

  display: block;

  background: #a4864d;
}


.builder strong {
  color: #96773e;

  font-size:
    clamp(10px, 0.62vw, 12px);

  font-weight: 700;

  white-space: nowrap;
}


/* DESCRIPTION */

.featured-description {

  overflow: hidden;

  margin:
    0.65rem
    0
    0;

  color: #817c75;

  font-size:
    clamp(12px, 0.72vw, 14px);

  font-weight: 400;

  line-height: 1.5;

  white-space: nowrap;
  text-overflow: ellipsis;
}


/* DETAILS */

.details-row {
  display: grid;

  grid-template-columns:
    0.8fr
    1.35fr
    0.8fr;

  align-items: center;

  gap: 0.5rem;

  margin-top: 0.9rem;

  padding:
    0.85rem
    0;

  border-top:
    1px solid #ece9e4;

  border-bottom:
    1px solid #ece9e4;
}


.detail {
  min-width: 0;

  display: flex;

  align-items: center;

  gap: 0.32rem;
}


.detail svg {
  width: 15px;
  height: 15px;

  flex-shrink: 0;

  color: #767069;
}


.detail span {
  overflow: hidden;

  color: #5c5751;

  font-size:
    clamp(10px, 0.65vw, 12px);

  font-weight: 500;

  text-overflow: ellipsis;

  white-space: nowrap;
}


/* FOOTER */

.card-footer {
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap: 1rem;

  margin-top: 1rem;
}


/* EXPLORE */

.explore-link {
  display: inline-flex;

  align-items: center;

  gap: 0.65rem;

  padding-bottom: 0.22rem;

  border-bottom:
    1px solid #111111;

  color: #111111;

  font-size:
    clamp(9px, 0.58vw, 11px);

  font-weight: 650;

  letter-spacing: 0.05em;

  text-decoration: none;

  text-transform: uppercase;
}


.explore-link span {
  transition:
    transform 0.3s ease;
}


.explore-link:hover span {
  transform:
    translate(
      3px,
      -3px
    );
}


/* PRICE */

.price-right {
  display: flex;

  flex-direction: column;

  align-items: flex-end;

  text-align: right;
}


.price-right > small {
  margin-bottom: 0.14rem;

  color: #aaa49d;

  font-size: clamp(8px, 0.46vw, 9px);

  font-weight: 700;

  letter-spacing: 0.1em;

  text-transform: uppercase;
}


.price-right > div {
  display: flex;

  align-items: baseline;

  gap: 0.23rem;
}


.price-right > div span {
  color: #a4864d;

  font-size: clamp(11px, 0.6vw, 12px);

  font-weight: 700;
}


.price-right > div strong {
  color: #111111;

  font-size:
    clamp(28px, 1.55vw, 34px);

  font-weight: 500;

  line-height: 1;
}


/* =========================================================
   EMPTY
========================================================= */

.empty {
  padding: 80px 20px;

  border: 1px solid #e0ddd7;

  background: #ffffff;

  text-align: center;
}


.empty h3 {
  margin: 0;

  font-size: 22px;

  font-weight: 600;
}


.empty p {
  margin: 8px 0 15px;

  color: #77716a;

  font-size: 13px;
}


.empty button {
  min-height: 42px;

  padding: 0 16px;

  border: 0;

  border-radius: 6px;

  background: #222222;

  color: #ffffff;

  font-size: 12px;

  font-weight: 700;

  cursor: pointer;
}


/* =========================================================
   MOBILE FILTER BUTTON
========================================================= */

.mobile-filter-button {
  display: none;
}


.mobile-overlay {
  display: none;
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 1250px) {

  .property-layout {
    grid-template-columns:
      290px
      minmax(0, 1fr);
  }


  .property-grid {
    grid-template-columns:
      repeat(2, minmax(0, 1fr));
  }

}


/* =========================================================
   MOBILE / DRAWER
========================================================= */

@media (max-width: 900px) {

  .section-heading {
    grid-template-columns: 1fr;

    gap: 15px;
  }


  .heading-copy {
    justify-self: start;
  }


  .property-layout {
    grid-template-columns: 1fr;
  }


  .mobile-filter-button {
    display: inline-flex;

    align-items: center;

    gap: 8px;

    min-height: 44px;

    margin-bottom: 15px;

    padding: 0 16px;

    border: 1px solid #d8d5d0;

    background: #ffffff;

    font-size: 13px;

    font-weight: 700;
  }


  .filter-count {
    width: 20px;

    height: 20px;

    display: grid;

    place-items: center;

    border-radius: 50%;

    background: #222222;

    color: #ffffff;

    font-size: 10px;

    font-weight: 700;
  }


  .filter-panel {
    position: fixed;

    z-index: 101;

    top: 0;

    left: -100%;

    width: min(92vw, 380px);

    height: 100vh;

    max-height: 100vh;

    border-radius: 0 15px 15px 0;

    transition: left 0.3s ease;
  }


  .filter-panel.open {
    left: 0;
  }


  .close-filter {
    display: block;
  }


  .mobile-overlay {
    position: fixed;

    z-index: 100;

    inset: 0;

    display: block;

    background: rgba(0,0,0,0.45);
  }

}


/* =========================================================
   SMALL MOBILE
========================================================= */

@media (max-width: 600px) {

  .property-section {
    padding: 45px 0;
  }


  .property-container {
    width: 91%;
  }


  .property-grid {
    grid-template-columns: 1fr;
  }


  .image-box {
    height: 72vw;
  }


  .results-toolbar {
    align-items: flex-start;

    flex-direction: column;
  }

}


/* =========================================================
   FEATURED CARD RESPONSIVE
========================================================= */

@media (max-width: 1100px) {

  .property-grid {
    grid-template-columns:
      repeat(
        2,
        minmax(0, 1fr)
      );
  }


  .image-box {
    height:
      clamp(
        280px,
        38vw,
        400px
      );
  }

}


@media (max-width: 600px) {

  .property-grid {
    grid-template-columns: 1fr;
  }


  .image-box {
    height:
      clamp(
        270px,
        75vw,
        370px
      );
  }


  .status-side {
    width: 30px;

    height: 105px;
  }


  .status-side span {
    font-size: 0.36rem;
  }


  .details-row {
    grid-template-columns:
      repeat(
        3,
        minmax(0, 1fr)
      );
  }

}

</style>