<template>
  <main class="opportunities">

    <!-- =====================================================
         HOT DEAL PROPERTIES
    ====================================================== -->
    <section class="property-section hot-section">

      <div class="shell">

        <!-- HEADER -->
        <div class="section-head">

          <div>

            <p class="eyebrow">
              SELECTED OPPORTUNITIES
            </p>

            <h2>
              Hot Deal Properties
            </h2>

            <p class="section-description">
              Selected residences offering exceptional value
              across sought-after Sri Lankan locations.
            </p>

          </div>


          <a href="#" class="view-all">
            View all
            <span>→</span>
          </a>

        </div>


        <!-- CARDS -->
        <div class="property-grid">

          <article
            v-for="property in hotProperties"
            :key="property.name"
            class="property-card"
          >

            <!-- IMAGE -->
            <div class="image-box">

              <img
                :src="property.image"
                :alt="property.name"
              />


              <!-- SMALL VERTICAL STATUS -->
              <div class="status-side hot-status">

                <span>
                  {{ property.status }}
                </span>

              </div>

            </div>


            <!-- CARD CONTENT -->
            <div class="card-content">

              <!-- TYPE + LOCATION -->
              <div class="meta-row">

                <span class="property-type">
                  {{ property.type }}
                </span>


                <div class="location">

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

              </div>


              <!-- TITLE -->
              <h3>
                {{ property.name }}
              </h3>


              <!-- SHORT DESCRIPTION -->
              <p class="description">
                {{ property.description }}
              </p>


              <!-- FOOTER -->
              <div class="card-footer">

                <a
                  href="#"
                  class="explore-link"
                >
                  View Residence
                  <span>↗</span>
                </a>


                <div class="price-right">

                  <small>
                    FROM
                  </small>

                  <div>

                    <span>
                      {{ property.currency }}
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



    <!-- =====================================================
         TRENDING PROPERTIES
    ====================================================== -->
    <section class="property-section trending-section">

      <div class="shell">

        <!-- HEADER -->
        <div class="section-head">

          <div>

            <p class="eyebrow">
              MOST VIEWED
            </p>

            <h2>
              Trending Properties
            </h2>

            <p class="section-description">
              Residences currently attracting strong attention
              from homebuyers and property investors.
            </p>

          </div>


          <a href="#" class="view-all">
            View all
            <span>→</span>
          </a>

        </div>


        <!-- CARDS -->
        <div class="property-grid">

          <article
            v-for="property in trendingProperties"
            :key="property.name"
            class="property-card"
          >

            <!-- IMAGE -->
            <div class="image-box">

              <img
                :src="property.image"
                :alt="property.name"
              />


              <!-- SMALL VERTICAL STATUS -->
              <div class="status-side trending-status">

                <span>
                  {{ property.status }}
                </span>

              </div>

            </div>


            <!-- CARD CONTENT -->
            <div class="card-content">

              <!-- TYPE + LOCATION -->
              <div class="meta-row">

                <span class="property-type">
                  {{ property.type }}
                </span>


                <div class="location">

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

              </div>


              <!-- TITLE -->
              <h3>
                {{ property.name }}
              </h3>


              <!-- SHORT DESCRIPTION -->
              <p class="description">
                {{ property.description }}
              </p>


              <!-- FOOTER -->
              <div class="card-footer">

                <a
                  href="#"
                  class="explore-link"
                >
                  View Residence
                  <span>↗</span>
                </a>


                <div class="price-right">

                  <small>
                    FROM
                  </small>

                  <div>

                    <span>
                      {{ property.currency }}
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

  </main>
</template>


<script setup>
import image2 from "../images/2.jpg";

/* =========================================================
   HOT DEALS
========================================================= */

const hotProperties = [

  {
    name: "Ocean Residence",

    type: "Luxury Apartment",

    location: "Colombo 03",

    description:
      "Prime city living offered through a limited-value release.",

    currency: "LKR",

    price: "52M",

    status: "HOT DEAL",

   image: image2
  },


  {
    name: "Parkside Pehouse",

    type: "Penthouse Residence",

    location: "Colombo 07",

    description:
      "Refined elevated living in one of Colombo’s most desirable addresses.",

    currency: "LKR",

    price: "78M",

    status: "SPECIAL",

    image:
      "https://i.pinimg.com/1200x/cd/cf/e7/cdcfe74e7bdba70e13080c05a833318e.jpg"
  },


  {
    name: "South Residence",

    type: "Coastal Residence",

    location: "Galle",

    description:
      "Private coastal living positioned close to the southern shoreline.",

    currency: "LKR",

    price: "46M",

    status: "READY",

    image:
      "https://i.pinimg.com/1200x/07/82/ae/0782ae978947f00bf0c6ac8808170822.jpg"
  },


  {
    name: "Garden Home",

    type: "Private Residence",

    location: "Thalpe",

    description:
      "A quiet tropical home created around privacy and natural surroundings.",

    currency: "LKR",

    price: "35M",

    status: "LIMITED",

    image:
      "https://i.pinimg.com/736x/87/49/51/874951812f5ee89e54c6c100c1d4cf81.jpg"
  }

];



/* =========================================================
   TRENDING
========================================================= */

const trendingProperties = [

  {
    name: "Icon V Thalpe",

    type: "Beachfront Residence",

    location: "Thalpe, Galle",

    description:
      "A distinctive beachfront address attracting strong buyer interest.",

    currency: "LKR",

    price: "24M",

    status: "TRENDING",

    image:
      "https://i.pinimg.com/736x/7a/37/6f/7a376f13c7fe11bde817fcd70ddb7425.jpg"
  },


  {
    name: "City Residence",

    type: "City Residence",

    location: "Colombo",

    description:
      "Contemporary urban living in one of Colombo’s connected locations.",

    currency: "USD",

    price: "34K",

    status: "POPULAR",

    image:
      "https://i.pinimg.com/1200x/58/27/02/58270273632a4295a47748abb7160e5e.jpg"
  },


  {
    name: "Galle Residence",

    type: "Ocean View Apartment",

    location: "Galle",

    description:
      "Modern coastal living framed by open views towards the Indian Ocean.",

    currency: "USD",

    price: "49K",

    status: "TRENDING",

    image:
      "https://i.pinimg.com/736x/f9/26/92/f926926fbbd48ff445cf642985355705.jpg"
  },


  {
    name: "Thalpe Collection",

    type: "Boutique Residence",

    location: "Thalpe",

    description:
      "An intimate residential collection designed for relaxed coastal living.",

    currency: "USD",

    price: "37K",

    status: "LIMITED",

    image:
      "https://i.pinimg.com/736x/d3/59/f3/d359f321a1a7b4ae01b67286afc47c3a.jpg"
  }

];
</script>


<style scoped>

/* =========================================================
   GLOBAL
========================================================= */

.opportunities,
.opportunities *,
.opportunities *::before,
.opportunities *::after {
  box-sizing: border-box;

  font-family: sans-serif;
}


.opportunities {
  width: 100%;

  color: #111111;
}


/* =========================================================
   SECTIONS
========================================================= */

.property-section {
  width: 100%;

  padding:
    clamp(4rem, 7vh, 6rem)
    0;
}


.hot-section {
  background: #f5f4f1;
}


.trending-section {
  background: #ffffff;
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

  margin-bottom: 1.5rem;

  border-bottom:
    1px solid #dedbd5;
}


.eyebrow {
  margin:
    0
    0
    0.6rem;

  color: #9d7e46;
  font-size: clamp(16px, 1.02vw, 18px);

  font-weight: 700;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}


.section-head h2 {
 margin: 0;
  
 font-size:
    clamp(
      48px,
      3.4vw,
      64px
    );

  font-weight: 400;
  line-height: 1.15;
  letter-spacing: -0.035em;
}


.section-description {
  max-width: 470px;

  margin:
    0.75rem
    0
    0;

  color: #858079;
  font-size: clamp(16px, 1.02vw, 18px);
  line-height: 1.7;
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
  font-size: clamp(13px, 0.82vw, 15px);

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
      220px,
      19vw,
      315px
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
    transform
    0.7s ease;
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

  z-index: 5;

  top: 0;

  left: 0;

  width:
    clamp(
      29px,
      2vw,
      34px
    );

  height:
    clamp(
      95px,
      8vw,
      125px
    );

  display: flex;

  align-items: center;

  justify-content: center;

  color: #ffffff;

  background: #111111;
}


.status-side span {
  display: block;

  color: #ffffff;
  font-size: clamp(9px, 0.55vw, 10px);

  font-weight: 500;

  letter-spacing: 0.17em;

  line-height: 1;

  text-transform: uppercase;

  white-space: nowrap;

  writing-mode: vertical-rl;

  text-orientation: mixed;
}


.trending-status {
  background: #8e713e;
}


/* =========================================================
   CONTENT
========================================================= */

.card-content {
  padding:
    clamp(
      1rem,
      1.15vw,
      1.2rem
    );
}


/* =========================================================
   META
========================================================= */

.meta-row {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 0.8rem;

  margin-bottom: 0.4rem;
}


.property-type {
  overflow: hidden;

  color: #96918a;
  font-size: clamp(14px, 0.86vw, 16px);

  font-weight: 500;

  white-space: nowrap;

  text-overflow: ellipsis;
}


/* =========================================================
   LOCATION
========================================================= */

.location {
  display: flex;

  align-items: center;

  justify-content: flex-end;

  gap: 0.3rem;

  color: #8a6e3b;

  white-space: nowrap;
}


.location svg {
  width: 12px;

  height: 12px;

  flex-shrink: 0;
}


.location span {
  font-size: clamp(14px, 0.86vw, 16px);

  font-weight: 650;
}


/* =========================================================
   TITLE
========================================================= */

.card-content h3 {
  margin: 0;

  color: #111111;
  font-size:
    clamp(
      27px,
      1.7vw,
      30px
    );
  font-weight: 400;
  line-height: 1.2;

  letter-spacing: -0.025em;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.description {
  display: -webkit-box;

  min-height: 2.8em;

  overflow: hidden;

  margin:
    0.6rem
    0
    0;

  color: #858079;
  font-size: clamp(15px, 0.92vw, 17px);
  line-height: 1.6;

  -webkit-line-clamp: 2;

  -webkit-box-orient: vertical;
}


/* =========================================================
   FOOTER
========================================================= */

.card-footer {
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap: 1rem;

  margin-top: 0.9rem;

  padding-top: 0.85rem;

  border-top:
    1px solid #ebe8e2;
}


/* =========================================================
   VIEW RESIDENCE
========================================================= */

.explore-link {
  display: inline-flex;

  align-items: center;

  gap: 0.55rem;

  padding-bottom: 0.2rem;

  border-bottom:
    1px solid #111111;

  color: #111111;
  font-size: clamp(12px, 0.74vw, 14px);

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

  color: #aaa49c;
  font-size: clamp(10px, 0.60vw, 12px);

  font-weight: 700;

  letter-spacing: 0.12em;

  text-transform: uppercase;
}


.price-right > div {
  display: flex;

  align-items: baseline;

  justify-content: flex-end;

  gap: 0.24rem;
}


.price-right > div span {
  color: #9b7a42;
  font-size: clamp(13px, 0.78vw, 15px);

  font-weight: 700;
}


.price-right > div strong {
  color: #111111;
  font-size: clamp(34px, 2vw, 48px);

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
  }


  .image-box {
    height:
      clamp(
        250px,
        34vw,
        380px
      );
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 600px) {

  /* Featured Residences typography scale */
  .eyebrow {
    font-size: 14px;
  }

  .section-head h2 {
    font-size: 40px;
    line-height: 1.15;
  }

  .section-description {
    font-size: 16px;
    line-height: 1.65;
  }

  .view-all {
    font-size: 14px;
  }

  .status-side span {
    font-size: 8px;
  }

  .property-type {
    font-size: 14px;
  }

  .location span {
    font-size: 14px;
  }

  .card-content h3 {
    font-size: 27px;
  }

  .description {
    font-size: 16px;
    line-height: 1.6;
  }

  .explore-link {
    font-size: 11px;
  }

  .price-right > small {
    font-size: 8px;
  }

  .price-right > div span {
    font-size: 14px;
  }

  .price-right > div strong {
    font-size: 30px;
  }


  .property-section {
    padding:
      3.2rem
      0;
  }


  .shell {
    width: 91vw;
  }


  .section-head {
    flex-direction: column;

    align-items: flex-start;

    gap: 1rem;
  }


  .property-grid {
    grid-template-columns: 1fr;
  }


  .image-box {
    height:
      clamp(
        250px,
        70vw,
        350px
      );
  }


  .meta-row {
    align-items: flex-start;
  }


  .location {
    max-width: 48%;

    white-space: normal;

    text-align: right;
  }

}
</style>