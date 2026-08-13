<template>
  <div class="property-sections">

    <!-- =====================================================
         HOT DEAL PROPERTIES
    ====================================================== -->
    <section class="property-section hot-deals">

      <div class="shell">

        <!-- HEADER -->
        <div class="section-head">

          <div class="section-heading">

            <p class="kicker">
              SELECTED OPPORTUNITIES
            </p>

            <h2>
              Hot Deal Properties
            </h2>

            <p class="section-description">
              Selected residences offering attractive value
              in sought-after locations across Sri Lanka.
            </p>

          </div>


          <a
            href="#"
            class="view-all"
          >
            View all
            <span>→</span>
          </a>

        </div>


        <!-- GOLD HIGHLIGHT LINE -->
        <div class="section-line">
          <span></span>
        </div>


        <!-- CARDS -->
        <div class="property-grid">

          <article
            v-for="property in hotDeals"
            :key="property.name"
            class="property-card"
          >

            <!-- IMAGE -->
            <div class="image-wrap">

              <img
                :src="property.img"
                :alt="property.name"
              />


              <div class="image-shade"></div>


              <span class="status hot-status">
                {{ property.status }}
              </span>

            </div>


            <!-- CARD BODY -->
            <div class="card-content">

              <p class="property-type">
                {{ property.type }}
              </p>


              <h3>
                {{ property.name }}
              </h3>


              <div class="location">

                <span class="location-dot"></span>

                <span>
                  {{ property.location }}
                </span>

              </div>


              <div class="card-bottom">

                <div class="price">

                  <small>
                    STARTING FROM
                  </small>

                  <strong>
                    {{ property.price }}
                  </strong>

                </div>


                <a
                  href="#"
                  class="view-property"
                >
                  View residence
                  <span>→</span>
                </a>

              </div>

            </div>

          </article>

        </div>

      </div>

    </section>



    <!-- =====================================================
         TRENDING PROPERTIES
    ====================================================== -->
    <section class="property-section trending">

      <div class="shell">

        <!-- HEADER -->
        <div class="section-head">

          <div class="section-heading">

            <p class="kicker">
              MOST VIEWED RESIDENCES
            </p>

            <h2>
              Trending Properties
            </h2>

            <p class="section-description">
              Residences currently attracting strong interest
              from buyers and investors.
            </p>

          </div>


          <a
            href="#"
            class="view-all light-link"
          >
            Explore all
            <span>→</span>
          </a>

        </div>


        <!-- GOLD HIGHLIGHT LINE -->
        <div class="section-line dark-line">
          <span></span>
        </div>


        <!-- CARDS -->
        <div class="property-grid">

          <article
            v-for="property in trendingProperties"
            :key="property.name"
            class="property-card trending-card"
          >

            <!-- IMAGE -->
            <div class="image-wrap">

              <img
                :src="property.img"
                :alt="property.name"
              />


              <div class="image-shade trending-shade"></div>


              <span class="status trending-status">
                {{ property.status }}
              </span>

            </div>


            <!-- CARD BODY -->
            <div class="card-content">

              <p class="property-type">
                {{ property.type }}
              </p>


              <h3>
                {{ property.name }}
              </h3>


              <div class="location">

                <span class="location-dot"></span>

                <span>
                  {{ property.location }}
                </span>

              </div>


              <div class="card-bottom">

                <div class="price">

                  <small>
                    FROM
                  </small>

                  <strong>
                    {{ property.price }}
                  </strong>

                </div>


                <a
                  href="#"
                  class="view-property"
                >
                  View residence
                  <span>→</span>
                </a>

              </div>

            </div>

          </article>

        </div>

      </div>

    </section>

  </div>
</template>



<script setup>

/* =========================================================
   HOT DEALS
========================================================= */

const hotDeals = [

  {
    name: "Ocean Avenue Residence",

    location: "Colombo 03",

    type: "Luxury Apartment",

    price: "USD 520K",

    status: "HOT DEAL",

    img:
      "src/images/hf_20260724_043544_62932b82-e384-492f-aa3c-8ca7dc82d080.webp"
  },


  {
    name: "Parkside Penthouse",

    location: "Colombo 07",

    type: "Penthouse Residence",

    price: "USD 780K",

    status: "SPECIAL",

    img:
      "src/images/weligama.webp"
  },


  {
    name: "South Coast Residence",

    location: "Galle",

    type: "Coastal Residence",

    price: "USD 465K",

    status: "READY",

    img:
      "src/images/Galle.webp"
  },


  {
    name: "Garden Courtyard Home",

    location: "Thalpe",

    type: "Private Residence",

    price: "USD 355K",

    status: "LIMITED",

    img:
      "src/images/Thalpe.webp"
  }

];



/* =========================================================
   TRENDING
========================================================= */

const trendingProperties = [

  {
    name: "Icon V Talpe",

    location: "Thalpe",

    type: "Luxury Apartment",

    price: "USD 420K",

    status: "TRENDING",

    img:
      "src/images/Thalpe.webp"
  },


  {
    name: "City Central Residence",

    location: "Colombo",

    type: "City Residence",

    price: "USD 340K",

    status: "POPULAR",

    img:
      "src/images/Colombo.jpeg"
  },


  {
    name: "Galle Ocean Residence",

    location: "Galle",

    type: "Ocean View Apartment",

    price: "USD 490K",

    status: "MOST VIEWED",

    img:
      "src/images/Galle.webp"
  },


  {
    name: "Thalpe Private Collection",

    location: "Thalpe",

    type: "Boutique Residence",

    price: "USD 375K",

    status: "TRENDING",

    img:
      "src/images/mirissa.webp"
  }

];

</script>



<style scoped>

/* =========================================================
   GLOBAL
========================================================= */

.property-sections,
.property-sections * {
  box-sizing: border-box;

  font-family:
    sans-serif;
}


.property-sections {
  width: 100%;
}


/* =========================================================
   SHARED SECTION
========================================================= */

.property-section {
  width: 100%;

  padding:
    clamp(3.5rem, 6vh, 5rem)
    0;

  overflow: hidden;
}


.shell {
  width:
    min(
      94vw,
      1650px
    );

  margin:
    0 auto;
}


/* =========================================================
   HOT DEAL BACKGROUND
========================================================= */

.hot-deals {
  background:
    #f3f2ef;

  color:
    #111111;
}


/* =========================================================
   TRENDING BACKGROUND
========================================================= */

.trending {
  background:
    #0a0a0a;

  color:
    #ffffff;
}


/* =========================================================
   HEADER
========================================================= */

.section-head {
  display: flex;

  justify-content: space-between;

  align-items: flex-end;

  gap:
    clamp(
      2rem,
      5vw,
      6rem
    );
}


.section-heading {
  max-width:
    700px;
}


.kicker {
  margin:
    0;

  color:
    #a4864d;

  font-size:
    clamp(
      0.48rem,
      0.54vw,
      0.62rem
    );

  font-weight:
    600;

  letter-spacing:
    0.2em;

  text-transform:
    uppercase;
}


.section-heading h2 {
  margin:
    clamp(
      0.45rem,
      0.8vh,
      0.7rem
    )
    0
    0;

  font-size:
    clamp(
      2rem,
      2.5vw,
      3.2rem
    );

  font-weight:
    400;

  line-height:
    1;

  letter-spacing:
    -0.035em;
}


.section-description {
  max-width:
    520px;

  margin:
    clamp(
      0.7rem,
      1.3vh,
      1rem
    )
    0
    0;

  color:
    #77736c;

  font-size:
    clamp(
      0.62rem,
      0.7vw,
      0.8rem
    );

  line-height:
    1.6;
}


.trending .section-description {
  color:
    rgba(
      255,
      255,
      255,
      0.48
    );
}


/* =========================================================
   VIEW ALL
========================================================= */

.view-all {
  display: flex;

  align-items: center;

  gap:
    0.55rem;

  padding-bottom:
    0.3rem;

  color:
    #111111;

  border-bottom:
    1px solid
    rgba(
      17,
      17,
      17,
      0.35
    );

  font-size:
    clamp(
      0.5rem,
      0.56vw,
      0.64rem
    );

  font-weight:
    500;

  letter-spacing:
    0.08em;

  text-transform:
    uppercase;

  text-decoration:
    none;
}


.light-link {
  color:
    #ffffff;

  border-color:
    rgba(
      255,
      255,
      255,
      0.35
    );
}


/* =========================================================
   HIGHLIGHT LINE
========================================================= */

.section-line {
  width:
    100%;

  height:
    1px;

  margin:
    clamp(
      1.4rem,
      2.5vh,
      2rem
    )
    0
    clamp(
      1.5rem,
      2.8vh,
      2.2rem
    );

  position:
    relative;

  background:
    #dcd8d1;
}


.section-line span {
  position:
    absolute;

  top:
    0;

  left:
    0;

  width:
    clamp(
      80px,
      9vw,
      150px
    );

  height:
    2px;

  background:
    #a4864d;
}


.dark-line {
  background:
    rgba(
      255,
      255,
      255,
      0.12
    );
}


/* =========================================================
   GRID
========================================================= */

.property-grid {
  display: grid;

  grid-template-columns:
    repeat(
      4,
      minmax(
        0,
        1fr
      )
    );

  gap:
    clamp(
      0.8rem,
      1vw,
      1rem
    );
}


/* =========================================================
   CARD
========================================================= */

.property-card {
  min-width:
    0;

  overflow:
    hidden;

  background:
    #ffffff;

  border:
    1px solid
    rgba(
      17,
      17,
      17,
      0.08
    );

  transition:
    transform 0.4s ease,
    box-shadow 0.4s ease;
}


.property-card:hover {
  transform:
    translateY(-6px);

  box-shadow:
    0
    18px
    45px
    rgba(
      0,
      0,
      0,
      0.1
    );
}


.trending-card {
  background:
    #111111;

  border-color:
    rgba(
      255,
      255,
      255,
      0.12
    );
}


/* =========================================================
   IMAGE
========================================================= */

.image-wrap {
  width:
    100%;

  height:
    clamp(
      200px,
      18vw,
      300px
    );

  position:
    relative;

  overflow:
    hidden;

  background:
    #111111;
}


.image-wrap img {
  width:
    100%;

  height:
    100%;

  object-fit:
    cover;

  transition:
    transform
    0.8s
    cubic-bezier(
      0.22,
      1,
      0.36,
      1
    );
}


.property-card:hover .image-wrap img {
  transform:
    scale(
      1.045
    );
}


/* =========================================================
   IMAGE SHADE
========================================================= */

.image-shade {
  position:
    absolute;

  inset:
    0;

  background:
    linear-gradient(
      180deg,
      rgba(0,0,0,0)
      55%,
      rgba(0,0,0,0.26)
      100%
    );
}


.trending-shade {
  background:
    linear-gradient(
      180deg,
      rgba(0,0,0,0.05)
      35%,
      rgba(0,0,0,0.42)
      100%
    );
}


/* =========================================================
   STATUS
========================================================= */

.status {
  position:
    absolute;

  z-index:
    3;

  top:
    0.75rem;

  left:
    0.75rem;

  padding:
    0.32rem
    0.55rem;

  font-size:
    clamp(
      0.42rem,
      0.47vw,
      0.53rem
    );

  font-weight:
    600;

  letter-spacing:
    0.07em;

  text-transform:
    uppercase;
}


.hot-status {
  background:
    #111111;

  color:
    #ffffff;
}


.trending-status {
  background:
    #a4864d;

  color:
    #ffffff;
}


/* =========================================================
   CONTENT
========================================================= */

.card-content {
  padding:
    clamp(
      0.95rem,
      1.2vw,
      1.25rem
    );
}


.property-type {
  margin:
    0
    0
    0.3rem;

  color:
    #8f8a83;

  font-size:
    clamp(
      0.52rem,
      0.58vw,
      0.66rem
    );
}


.trending-card .property-type {
  color:
    rgba(
      255,
      255,
      255,
      0.48
    );
}


.card-content h3 {
  margin:
    0;

  color:
    #111111;

  font-size:
    clamp(
      1rem,
      1.2vw,
      1.4rem
    );

  font-weight:
    500;

  line-height:
    1.16;

  letter-spacing:
    -0.02em;
}


.trending-card h3 {
  color:
    #ffffff;
}


/* =========================================================
   LOCATION
========================================================= */

.location {
  display:
    flex;

  align-items:
    center;

  gap:
    0.4rem;

  margin-top:
    0.55rem;

  color:
    #6f6a64;

  font-size:
    clamp(
      0.55rem,
      0.62vw,
      0.7rem
    );
}


.trending-card .location {
  color:
    rgba(
      255,
      255,
      255,
      0.58
    );
}


.location-dot {
  width:
    5px;

  height:
    5px;

  flex-shrink:
    0;

  border-radius:
    50%;

  background:
    #a4864d;
}


/* =========================================================
   CARD BOTTOM
========================================================= */

.card-bottom {
  display:
    flex;

  justify-content:
    space-between;

  align-items:
    flex-end;

  gap:
    0.8rem;

  margin-top:
    clamp(
      0.85rem,
      1.4vh,
      1rem
    );

  padding-top:
    clamp(
      0.75rem,
      1.2vh,
      0.9rem
    );

  border-top:
    1px solid
    #eceae6;
}


.trending-card .card-bottom {
  border-color:
    rgba(
      255,
      255,
      255,
      0.12
    );
}


/* =========================================================
   PRICE
========================================================= */

.price small {
  display:
    block;

  margin-bottom:
    0.18rem;

  color:
    #99958e;

  font-size:
    0.42rem;

  font-weight:
    500;

  letter-spacing:
    0.11em;
}


.price strong {
  color:
    #111111;

  font-size:
    clamp(
      0.76rem,
      0.86vw,
      0.98rem
    );

  font-weight:
    600;
}


.trending-card .price strong {
  color:
    #ffffff;
}


/* =========================================================
   VIEW PROPERTY
========================================================= */

.view-property {
  display:
    flex;

  align-items:
    center;

  gap:
    0.4rem;

  padding-bottom:
    0.2rem;

  color:
    #111111;

  border-bottom:
    1px solid
    rgba(
      17,
      17,
      17,
      0.3
    );

  font-size:
    clamp(
      0.45rem,
      0.51vw,
      0.58rem
    );

  font-weight:
    500;

  letter-spacing:
    0.06em;

  text-decoration:
    none;

  text-transform:
    uppercase;

  white-space:
    nowrap;

  transition:
    opacity 0.3s ease;
}


.trending-card .view-property {
  color:
    #ffffff;

  border-color:
    rgba(
      255,
      255,
      255,
      0.32
    );
}


.view-property:hover {
  opacity:
    0.55;
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 1100px) {

  .property-grid {
    grid-template-columns:
      repeat(
        2,
        minmax(
          0,
          1fr
        )
      );
  }


  .image-wrap {
    height:
      clamp(
        240px,
        31vw,
        360px
      );
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 600px) {

  .property-section {
    padding:
      3rem
      0;
  }


  .shell {
    width:
      91vw;
  }


  .section-head {
    flex-direction:
      column;

    align-items:
      flex-start;

    gap:
      1rem;
  }


  .section-heading h2 {
    font-size:
      clamp(
        1.9rem,
        9vw,
        2.7rem
      );
  }


  .property-grid {
    grid-template-columns:
      1fr;
  }


  .image-wrap {
    height:
      clamp(
        240px,
        68vw,
        350px
      );
  }

}


/* =========================================================
   SMALL MOBILE
========================================================= */

@media (max-width: 390px) {

  .card-bottom {
    flex-direction:
      column;

    align-items:
      flex-start;
  }

}

</style>