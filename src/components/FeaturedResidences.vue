<template>
  <section class="featured">

    <div class="shell">

      <!-- =========================
           HEADER
      ========================== -->
      <div class="section-head">

        <div>

          <p class="eyebrow">
            CURATED COLLECTION
          </p>

          <h2>
            Featured Residences
          </h2>

          <p class="section-description">
            A selected collection of premium residences
            across Sri Lanka’s most desirable addresses.
          </p>

        </div>


        <a href="#" class="view-all">
          View all
          <span>→</span>
        </a>

      </div>


 


      <!-- =========================
           PROPERTY GRID
      ========================== -->
      <div class="property-grid">

            <article
        v-for="property in properties"
        :key="property.name"
        class="property-card"
      >

          <!-- =========================
               IMAGE
          ========================== -->
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


          <!-- =========================
               CARD CONTENT
          ========================== -->
          <div class="card-content">

            <span class="property-type">
              {{ property.type }}
            </span>


            <!-- PROPERTY NAME -->
            <h3>
              {{ property.name }}
            </h3>


            <!-- =========================
                 LOCATION BELOW TITLE
            ========================== -->
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


            <!-- =========================
                 BUILDER
            ========================== -->
            <div class="builder">

              <span>
                PRESENTED BY
              </span>

              <i></i>

              <strong>
                {{ property.builder }}
              </strong>

            </div>


            <!-- =========================
                 DESCRIPTION
            ========================== -->
            <p class="description">
              {{ property.description }}
            </p>


            <!-- =========================
                 DETAILS
            ========================== -->
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
                  {{ property.bedrooms }}
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
                  {{ property.bathrooms }}
                </span>

              </div>

            </div>


            <!-- =========================
                 FOOTER
            ========================== -->
            <div class="card-footer">

              <a
                href="#"
                class="explore-link"
              >
                Explore Residence
                <span>↗</span>
              </a>


              <!-- PRICE -->
              <div class="price-right">

                <small>
                  STARTING FROM
                </small>

                <div>

                  <span>
                    LKR
                  </span>

                  <strong>
                    {{ property.price }}
                  </strong>

                </div>

              </div>

            </div>

          </div>

        </article>

      </div>

    </div>

  </section>
</template>


<script setup>
import {
  ref,
  computed
} from "vue";

const properties = [

  {
    name: "Icon V Thalpe",
    type: "Beachfront Residence",

    location: "Thalpe, Galle",
    filterLocation: "Thalpe",

    builder: "Odiliya Premier",

    description:
      "Refined beachfront living with ocean views, privacy and contemporary coastal design.",

    bedrooms: "2–3 Bed",

    size: "1,150–1,850 sq.ft",

    bathrooms: "2 Bath",

    price: "24M",

    status: "FEATURED",

    image:
      "src/images/Thalpe.webp"
  },


  {
    name: "Oceanista Residences",
    type: "Beachfront Apartments",

    location: "Panadura",
    filterLocation: "Colombo",

    builder: "Odiliya Premier",

    description:
      "Contemporary coastal apartments designed around light, comfort and long-term value.",

    bedrooms: "1–3 Bed",

    size: "800–2,400 sq.ft",

    bathrooms: "2 Bath",

    price: "25M",

    status: "NEW",

    image:
      "src/images/weligama.webp"
  },


  {
    name: "Platinum 10",
    type: "Private Pool Villas",

    location: "Colombo",
    filterLocation: "Colombo",

    builder: "Odiliya Premier",

    description:
      "Private residences combining generous spaces, refined architecture and city convenience.",

    bedrooms: "4 Bed",

    size: "3,500+ sq.ft",

    bathrooms: "4 Bath",

    price: "84M",

    status: "LIMITED",

    image:
      "src/images/Colombo.jpeg"
  },


  {
    name: "Ocean House",
    type: "Luxury Coastal Residence",

    location: "Galle",
    filterLocation: "Galle",

    builder: "Odiliya Premier",

    description:
      "A peaceful coastal residence shaped around natural light, privacy and elegant living.",

    bedrooms: "3 Bed",

    size: "1,750–2,600 sq.ft",

    bathrooms: "3 Bath",

    price: "42M",

    status: "READY",

    image:
      "src/images/nuwaraeliya.webp"
  }

];

</script>


<style scoped>

/* =========================================================
   GLOBAL
========================================================= */

.featured,
.featured *,
.featured *::before,
.featured *::after {
  box-sizing: border-box;

  font-family: sans-serif;
}


/* =========================================================
   SECTION
========================================================= */

.featured {
  width: 100%;

  padding:
    clamp(3.8rem, 7vh, 6rem)
    0;

  background: #f5f4f1;

  color: #111111;
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
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap: 3rem;

  padding-bottom: 1.5rem;

  border-bottom:
    1px solid #dedbd5;
}


.eyebrow {
  margin:
    0
    0
    0.6rem;

  color: #9d7e46;

  font-size: 0.62rem;

  font-weight: 700;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}


.section-head h2 {
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


.section-description {
  max-width: 470px;

  margin:
    0.75rem
    0
    0;

  color: #858079;

  font-size:
    clamp(
      0.48rem,
      0.72vw,
      0.82rem
    );

  line-height: 1.6;
}


/* =========================================================
   VIEW ALL
========================================================= */

.view-all {
  display: inline-flex;

  align-items: center;

  gap: 0.7rem;

  padding-bottom: 0.3rem;

  border-bottom:
    1px solid #111111;

  color: #111111;

  font-size: 0.58rem;

  font-weight: 700;

  letter-spacing: 0.08em;

  text-decoration: none;

  text-transform: uppercase;
}


.view-all span {
  transition:
    transform 0.3s ease;
}


.view-all:hover span {
  transform:
    translateX(4px);
}
/* =========================================================
   GRID
========================================================= */

.property-grid {
  display: grid;

  grid-template-columns:
    repeat(
      4,
      minmax(0, 1fr)
    );

  gap:
    clamp(
      0.8rem,
      1vw,
      1.1rem
    );
}


/* =========================================================
   CARD
========================================================= */

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
    0
    18px
    45px
    rgba(0, 0, 0, 0.07);
}


/* =========================================================
   IMAGE
========================================================= */

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


/* =========================================================
   SMALL VERTICAL STATUS
========================================================= */

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
      155px,
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

  transition:
    background 0.3s ease;
}


.status-side span {
  display: block;

  color: #ffffff;

  font-size:
    clamp(
      0.66rem,
      0.4vw,
      0.46rem
    );

  font-weight: 500;

  letter-spacing: 0.17em;

  line-height: 1;

  text-transform: uppercase;

  white-space: nowrap;

  writing-mode: vertical-rl;

  text-orientation: mixed;
}


.property-card:hover
.status-side {
  background: #000000;
}


/* =========================================================
   CONTENT
========================================================= */

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
    clamp(
      0.53rem,
      0.57vw,
      0.62rem
    );

  font-weight: 500;
}


.card-content h3 {
  margin: 0;

  color: #111111;

  font-size:
    clamp(
      1.1rem,
      1.35vw,
      1.6rem
    );

  font-weight: 400;

  line-height: 1.15;

  letter-spacing: -0.025em;
}


/* =========================================================
   LOCATION BELOW TITLE
========================================================= */

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
    clamp(
      0.56rem,
      0.6vw,
      0.67rem
    );

  font-weight: 600;
}


/* =========================================================
   BUILDER
========================================================= */

.builder {
  display: flex;

  align-items: center;

  gap: 0.4rem;

  margin-top: 0.5rem;
}


.builder span {
  color: #aaa49c;

  font-size: 0.42rem;

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
    clamp(
      0.56rem,
      0.6vw,
      0.67rem
    );

  font-weight: 700;

  white-space: nowrap;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.description {
  display: -webkit-box;

  min-height: 2.8em;

  overflow: hidden;

  margin:
    0.65rem
    0
    0;

  color: #817c75;

  font-size:
    clamp(
      0.58rem,
      0.62vw,
      0.68rem
    );

  font-weight: 400;

  line-height: 1.5;

  -webkit-line-clamp: 2;

  -webkit-box-orient: vertical;
}


/* =========================================================
   DETAILS
========================================================= */

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
    clamp(
      0.52rem,
      0.57vw,
      0.65rem
    );

  font-weight: 500;

  text-overflow: ellipsis;

  white-space: nowrap;
}


/* =========================================================
   FOOTER
========================================================= */

.card-footer {
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap: 1rem;

  margin-top: 1rem;
}


/* =========================================================
   EXPLORE
========================================================= */

.explore-link {
  display: inline-flex;

  align-items: center;

  gap: 0.65rem;

  padding-bottom: 0.22rem;

  border-bottom:
    1px solid #111111;

  color: #111111;

  font-size:
    clamp(
      0.5rem,
      0.54vw,
      0.6rem
    );

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


/* =========================================================
   PRICE RIGHT
========================================================= */

.price-right {
  display: flex;

  flex-direction: column;

  align-items: flex-end;

  text-align: right;
}


.price-right > small {
  margin-bottom: 0.14rem;

  color: #aaa49d;

  font-size: 0.38rem;

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

  font-size: 0.5rem;

  font-weight: 700;
}


.price-right > div strong {
  font-size:
    clamp(
      1.4rem,
      1.7vw,
      1.9rem
    );
}


/* =========================================================
   TABLET
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


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 600px) {

  .featured {
    padding:
      3rem
      0;
  }


  .shell {
    width:
      91vw;
  }


  .section-head {
    flex-direction: column;

    align-items: flex-start;

    gap: 1rem;
  }


  .property-grid {
    grid-template-columns:
      1fr;
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