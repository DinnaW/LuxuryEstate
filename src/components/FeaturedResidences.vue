<template>
  <section class="featured">
    <div class="shell">

      <!-- HEADER -->
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


      <!-- PROPERTY GRID -->
      <div class="property-grid">

        <article
          v-for="property in properties"
          :key="property.name"
          class="property-card"
        >

          <!-- IMAGE -->
          <div class="image-box">

            <img
              :src="property.image"
              :alt="property.name"
            />

            <!-- STATUS -->
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
                {{ property.builder }}
              </strong>

            </div>


            <!-- DESCRIPTION -->
            <p class="description">
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
                  <span>LKR</span>

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

/* =========================================================
   LOCAL IMAGES
========================================================= */

import image1 from "../images/1.jpg";
import image3 from "../images/3.jpg";


/* =========================================================
   PROPERTY DATA
========================================================= */

const properties = [

  {
    name: "Icon V Thalpe",

    type: "Beachfront Residence",

    location: "Thalpe, Galle",

    builder: "Odiliya Premier",

    description:
      "Refined beachfront living with ocean views, privacy and contemporary design.",

    bedrooms: "2–3 Bed",

    size: "1,150–1,850 sq.ft",

    bathrooms: "2 Bath",

    price: "24M",

    status: "FEATURED",

    image: image1
  },


  {
    name: "Oceanista Residences",

    type: "Beachfront Apartments",

    location: "Panadura",

    builder: "Odiliya Premier",

    description:
      "Contemporary coastal living shaped by light, comfort and lasting value.",

    bedrooms: "1–3 Bed",

    size: "800–2,400 sq.ft",

    bathrooms: "2 Bath",

    price: "25M",

    status: "NEW",

    image: image3
  },


  {
    name: "Platinum 10",

    type: "Private Pool Villas",

    location: "Colombo",

    builder: "Odiliya Premier",

    description:
      "Private city residences combining generous space, refined design and convenience.",

    bedrooms: "4 Bed",

    size: "3,500+ sq.ft",

    bathrooms: "4 Bath",

    price: "84M",

    status: "LIMITED",

    image:
      "https://images.unsplash.com/photo-1596178067639-5c6e68aea6dc?q=80&w=2070&auto=format&fit=crop"
  },


  {
    name: "Ocean House",

    type: "Luxury Coastal Residence",

    location: "Galle",

    builder: "Odiliya Premier",

    description:
      "Elegant coastal living shaped around natural light, privacy and calm.",

    bedrooms: "3 Bed",

    size: "1,750–2,600 sq.ft",

    bathrooms: "3 Bath",

    price: "42M",

    status: "READY",

    image:
      "https://i.pinimg.com/1200x/9c/9c/24/9c9c246228431e0d4af293d4603da044.jpg"
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
    clamp(70px, 7vh, 105px)
    0;

  background: #f5f4f1;

  color: #111111;
}


.shell {
  width: min(94vw, 1650px);

  margin: 0 auto;
}


/* =========================================================
   HEADER
========================================================= */

.section-head {
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap: 3rem;

  padding-bottom: 28px;

  margin-bottom: 34px;

  border-bottom:
    1px solid #dedbd5;
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


.section-head h2 {
  margin: 0;

  color: #111111;

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


.section-description {
  max-width: 500px;

  margin:
    13px
    0
    0;

  color: #77736d;

  font-size:
    clamp(
      13px,
      0.82vw,
      15px
    );

  font-weight: 400;

  line-height: 1.7;
}


/* =========================================================
   VIEW ALL
========================================================= */

.view-all {
  display: inline-flex;

  align-items: center;

  gap: 9px;

  padding-bottom: 5px;

  border-bottom:
    1px solid #111111;

  color: #111111;

  font-size:
    clamp(
      10px,
      0.65vw,
      12px
    );

  font-weight: 700;

  letter-spacing: 0.08em;

  line-height: 1.3;

  text-decoration: none;

  text-transform: uppercase;

  white-space: nowrap;
}


.view-all span {
  font-size: 15px;

  transition:
    transform 0.3s ease;
}


.view-all:hover span {
  transform:
    translateX(4px);
}


/* =========================================================
   PROPERTY GRID
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
      16px,
      1.2vw,
      22px
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
    box-shadow 0.4s ease,
    border-color 0.4s ease;
}


.property-card:hover {
  transform:
    translateY(-5px);

  border-color:
    #d3cec6;

  box-shadow:
    0 20px 50px
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
      240px,
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

  object-position: center;

  transition:
    transform 0.8s ease;
}


.property-card:hover
.image-box img {
  transform:
    scale(1.035);
}


/* =========================================================
   STATUS LABEL
========================================================= */

.status-side {
  position: absolute;

  z-index: 5;

  top: 0;

  left: 0;

  width:
    clamp(
      30px,
      2vw,
      36px
    );

  height: 130px;

  display: flex;

  align-items: center;

  justify-content: center;

  overflow: hidden;

  background:
    rgba(12, 12, 12, 0.94);

  color: #ffffff;
}


.status-side span {
  display: block;

  color: #ffffff;

  font-size:
    clamp(
      9px,
      0.55vw,
      10px
    );

  font-weight: 600;

  letter-spacing: 0.16em;

  line-height: 1;

  text-transform: uppercase;

  white-space: nowrap;

  writing-mode: vertical-rl;

  text-orientation: mixed;
}


/* =========================================================
   CARD CONTENT
========================================================= */

.card-content {
  padding:
    clamp(
      18px,
      1.35vw,
      24px
    );
}


.property-type {
  display: block;

  margin-bottom: 7px;

  color: #8d8881;

  font-size:
    clamp(
      11px,
      0.68vw,
      13px
    );

  font-weight: 500;

  line-height: 1.4;
}


.card-content h3 {
  margin: 0;

  color: #111111;

  font-size:
    clamp(
      20px,
      1.35vw,
      25px
    );

  font-weight: 400;

  line-height: 1.2;

  letter-spacing:
    -0.025em;
}


/* =========================================================
   LOCATION
========================================================= */

.location-row {
  display: flex;

  align-items: center;

  gap: 6px;

  margin-top: 10px;

  color: #393531;
}


.location-row svg {
  width: 14px;

  height: 14px;

  flex-shrink: 0;

  color: #a4864d;
}


.location-row span {
  font-size:
    clamp(
      11px,
      0.68vw,
      13px
    );

  font-weight: 600;

  line-height: 1.4;
}


/* =========================================================
   BUILDER
========================================================= */

.builder {
  display: flex;

  align-items: center;

  gap: 7px;

  margin-top: 9px;
}


.builder span {
  color: #99938b;

  font-size:
    clamp(
      8px,
      0.48vw,
      9px
    );

  font-weight: 700;

  letter-spacing: 0.11em;

  line-height: 1.3;

  white-space: nowrap;
}


.builder i {
  width: 15px;

  height: 1px;

  flex-shrink: 0;

  display: block;

  background: #a4864d;
}


.builder strong {
  overflow: hidden;

  color: #96773e;

  font-size:
    clamp(
      10px,
      0.62vw,
      12px
    );

  font-weight: 700;

  line-height: 1.3;

  text-overflow: ellipsis;

  white-space: nowrap;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.description {
  overflow: hidden;

  margin:
    13px
    0
    0;

  color: #716d67;

  font-size:
    clamp(
      12px,
      0.72vw,
      14px
    );

  font-weight: 400;

  line-height: 1.6;

  white-space: nowrap;

  text-overflow: ellipsis;
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

  gap: 8px;

  margin-top: 16px;

  padding:
    14px
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

  gap: 6px;
}


.detail svg {
  width: 15px;

  height: 15px;

  flex-shrink: 0;

  color: #706a64;
}


.detail span {
  overflow: hidden;

  color: #514c47;

  font-size:
    clamp(
      10px,
      0.65vw,
      12px
    );

  font-weight: 500;

  line-height: 1.4;

  text-overflow: ellipsis;

  white-space: nowrap;
}


/* =========================================================
   CARD FOOTER
========================================================= */

.card-footer {
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap: 16px;

  margin-top: 18px;
}


/* =========================================================
   EXPLORE LINK
========================================================= */

.explore-link {
  display: inline-flex;

  align-items: center;

  gap: 8px;

  padding-bottom: 4px;

  border-bottom:
    1px solid #111111;

  color: #111111;

  font-size:
    clamp(
      9px,
      0.58vw,
      11px
    );

  font-weight: 700;

  letter-spacing: 0.05em;

  line-height: 1.3;

  text-decoration: none;

  text-transform: uppercase;

  white-space: nowrap;
}


.explore-link span {
  font-size: 13px;

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
   PRICE
========================================================= */

.price-right {
  display: flex;

  flex-direction: column;

  align-items: flex-end;

  text-align: right;

  white-space: nowrap;
}


.price-right > small {
  margin-bottom: 4px;

  color: #969089;

  font-size:
    clamp(
      8px,
      0.46vw,
      10px
    );

  font-weight: 700;

  letter-spacing: 0.09em;

  line-height: 1.3;

  text-transform: uppercase;
}


.price-right > div {
  display: flex;

  align-items: baseline;

  gap: 5px;
}


.price-right > div span {
  color: #a4864d;

  font-size:
    clamp(
      10px,
      0.6vw,
      12px
    );

  font-weight: 900;
}


.price-right > div strong {
  color: #111111;

  font-size:
    clamp(
      30px,
      1.55vw,
      42px
    );

  font-weight: 500;

  line-height: 1;
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

    gap: 22px;
  }


  .image-box {
    height:
      clamp(
        280px,
        38vw,
        400px
      );
  }


  .card-content h3 {
    font-size: 23px;
  }


  .description {
    font-size: 13px;
  }


  .detail span {
    font-size: 11px;
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 600px) {

  .featured {
    padding:
      55px
      0;
  }


  .shell {
    width: 91vw;
  }


  .section-head {
    flex-direction: column;

    align-items: flex-start;

    gap: 18px;

    margin-bottom: 25px;

    padding-bottom: 22px;
  }


  .eyebrow {
    font-size: 10px;
  }


  .section-head h2 {
    font-size: 30px;

    line-height: 1.15;
  }


  .section-description {
    max-width: 100%;

    font-size: 13px;

    line-height: 1.65;
  }


  .view-all {
    font-size: 10px;
  }


  .property-grid {
    grid-template-columns: 1fr;

    gap: 24px;
  }


  .image-box {
    height:
      clamp(
        270px,
        75vw,
        380px
      );
  }


  .status-side {
    width: 31px;

    height: 110px;
  }


  .status-side span {
    font-size: 8px;
  }


  .card-content {
    padding: 20px;
  }


  .property-type {
    font-size: 11px;
  }


  .card-content h3 {
    font-size: 22px;
  }


  .location-row span {
    font-size: 12px;
  }


  .builder span {
    font-size: 8px;
  }


  .builder strong {
    font-size: 10px;
  }


  .description {
    font-size: 13px;

    line-height: 1.6;
  }


  .details-row {
    grid-template-columns:
      repeat(
        3,
        minmax(0, 1fr)
      );

    gap: 5px;
  }


  .detail span {
    font-size: 10px;
  }


  .explore-link {
    font-size: 9px;
  }


  .price-right > small {
    font-size: 8px;
  }


  .price-right > div span {
    font-size: 10px;
  }


  .price-right > div strong {
    font-size: 25px;
  }

}


/* =========================================================
   VERY SMALL MOBILE
========================================================= */

@media (max-width: 390px) {

  .card-footer {
    align-items: flex-start;

    flex-direction: column;
  }


  .price-right {
    align-items: flex-start;

    text-align: left;
  }


  .details-row {
    grid-template-columns: 1fr;
  }


  .detail {
    min-height: 25px;
  }

}

</style>