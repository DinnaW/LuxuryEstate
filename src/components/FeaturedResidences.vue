

<template>
  <section class="sec">

<div class="shell">

  <!-- =====================================
       HEADER
  ====================================== -->
  <div class="head">

    <div>
      <p class="kicker">
        CURATED COLLECTION
      </p>

      <h2 class="title">
        Featured Residences
      </h2>

      <p class="section-desc">
        Discover a curated selection of distinctive residences
        across Sri Lanka's most desirable locations.
      </p>
    </div>

    <a href="#" class="view-all">
      View all →
    </a>

  </div>


  <!-- =====================================
       FILTERS
  ====================================== -->
  <div class="filters">

    <button
      v-for="f in filters"
      :key="f"
      type="button"
      :class="{ on: active === f }"
      @click="active = f"
    >
      {{ f }}
    </button>

  </div>


  <!-- =====================================
       PROPERTY GRID
  ====================================== -->
  <div class="grid">

    <article
      v-for="p in shown"
      :key="p.name"
      class="project-card"
    >

      <!-- =================================
           PROPERTY IMAGE
      ================================== -->
      <div class="image-wrap">

        <img
          :src="p.img"
          :alt="p.name"
        />

        <div class="image-shade"></div>


        <!-- TAGS -->
        <div class="badges">

          <span
            v-for="tag in p.tags"
            :key="tag"
            class="badge"
            :class="getTagClass(tag)"
          >
            {{ tag }}
          </span>

        </div>

      </div>


      <!-- =================================
           PROPERTY CONTENT
      ================================== -->
      <div class="content">

        <p class="property-type">
          {{ p.type }}
        </p>


        <h3 class="property-title">
          {{ p.name }}
        </h3>


        <div class="location">

          <svg
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path
              d="M12 21s6-5.3 6-11a6 6 0 1 0-12 0c0 5.7 6 11 6 11Z"
            />
            <circle
              cx="12"
              cy="10"
              r="2"
            />
          </svg>

          <span>
            {{ p.area }}
          </span>

        </div>


        <p class="description">
          {{ p.description }}
        </p>


        <!-- =================================
             PROPERTY FEATURES
        ================================== -->
        <div class="features">

          <!-- BEDROOMS -->
          <div class="feature">

            <div class="feature-icon">
              <svg viewBox="0 0 24 24">
                <path d="M3 18v-8h2v2h14V9h2v9" />
                <path d="M5 12h14v5H5z" />
                <path d="M7 9h4v3H7z" />
              </svg>
            </div>

            <span>
              {{ p.bedrooms }}
            </span>

          </div>


          <!-- AREA -->
          <div class="feature">

            <div class="feature-icon">
              <svg viewBox="0 0 24 24">
                <path d="M5 9V5h4" />
                <path d="M15 5h4v4" />
                <path d="M19 15v4h-4" />
                <path d="M9 19H5v-4" />
              </svg>
            </div>

            <span>
              {{ p.size }}
            </span>

          </div>


          <!-- BATHROOMS -->
          <div class="feature">

            <div class="feature-icon">
              <svg viewBox="0 0 24 24">
                <path d="M4 13h16" />
                <path d="M5 13v2a5 5 0 0 0 5 5h4a5 5 0 0 0 5-5v-2" />
                <path d="M7 13V7a3 3 0 0 1 6 0" />
              </svg>
            </div>

            <span>
              {{ p.bathrooms }}
            </span>

          </div>


          <!-- PARKING -->
          <div class="feature">

            <div class="feature-icon parking-icon">
              P
            </div>

            <span>
              {{ p.parking }}
            </span>

          </div>

        </div>


        <!-- =================================
             CARD FOOTER
        ================================== -->
        <div class="card-footer">

          <div class="price">

            <small>
              STARTING FROM
            </small>

            <span class="currency">
              {{ p.currency }}
            </span>

            <strong>
              {{ p.price }}
            </strong>

          </div>


          <a
            href="#"
            class="explore"
          >
            <span>
              Explore
            </span>

            <span class="arrow">
              →
            </span>
          </a>

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


const filters = [
  "All",
  "Colombo",
  "Galle",
  "Thalpe"
];


const active = ref("All");


const projects = [

  {
    name: "Icon V Talpe",

    area: "Thalpe",

    type: "Luxury Apartment Development",

    description:
      "Contemporary coastal residences shaped around refined interiors, natural light and relaxed South Coast living.",

    bedrooms: "2 & 3 Bedrooms",

    size: "1,150–1,850 sq.ft",

    bathrooms: "2 Bathrooms",

    parking: "Dedicated Parking",

    currency: "USD",

    price: "420K",

    tags: [
      "BEST SELLING",
      "READY"
    ],

    img:
      "src/images/Thalpe.webp"
  },


  {
    name: "Sotheby's International",

    area: "Colombo",

    type: "Premium City Residence",

    description:
      "A sophisticated urban address combining architectural character, private amenities and effortless city access.",

    bedrooms: "2 & 3 Bedrooms",

    size: "1,250–2,100 sq.ft",

    bathrooms: "2 Bathrooms",

    parking: "Private Parking",

    currency: "USD",

    price: "310K",

    tags: [
      "NEWLY LAUNCHED",
      "ONGOING"
    ],

    img:
      "src/images/weligama.webp"
  },


  {
    name: "Philippe Philippe",

    area: "Colombo",

    type: "Signature Luxury Residence",

    description:
      "Generous residences designed for contemporary living with elegant proportions, premium materials and city views.",

    bedrooms: "3 & 4 Bedrooms",

    size: "1,900–3,200 sq.ft",

    bathrooms: "3 Bathrooms",

    parking: "2 Parking Slots",

    currency: "USD",

    price: "680K",

    tags: [
      "FEATURED",
      "ONGOING"
    ],

    img:
      "src/images/Galle.webp"
  },


  {
    name: "Ocean House",

    area: "Galle",

    type: "Coastal Residence",

    description:
      "A refined coastal home offering generous interiors, tropical surroundings and effortless access to the southern coastline.",

    bedrooms: "3 Bedrooms",

    size: "1,750–2,600 sq.ft",

    bathrooms: "3 Bathrooms",

    parking: "Dedicated Parking",

    currency: "USD",

    price: "465K",

    tags: [
      "BEST SELLING",
      "READY"
    ],

    img:
      "src/images/nuwaraeliya.webp"
  },


  {
    name: "Thalpe Courtyard",

    area: "Thalpe",

    type: "Private Courtyard Residence",

    description:
      "A limited collection of residences balancing privacy, landscaped outdoor spaces and modern tropical architecture.",

    bedrooms: "2 Bedrooms",

    size: "1,450–1,900 sq.ft",

    bathrooms: "2 Bathrooms",

    parking: "Private Parking",

    currency: "USD",

    price: "355K",

    tags: [
      "NEW",
      "LIMITED"
    ],

    img:
      "src/images/hf_20260724_043544_62932b82-e384-492f-aa3c-8ca7dc82d080.webp"
  }

];


const shown = computed(() => {

  if (active.value === "All") {
    return projects.slice(0, 4);
  }

  return projects.filter(
    (project) =>
      project.area === active.value
  );

});


const getTagClass = (tag) => {

  const normalized =
    tag
      .toLowerCase()
      .replaceAll(" ", "-");

  return `badge-${normalized}`;

};
</script>

<style scoped>

/* =========================================================
   SECTION
========================================================= */

.sec {
  width: 100%;

  padding:
    clamp(4.5rem, 8vh, 7rem)
    0;

  background: #ffffff;

  color: #111111;
}


.shell {
  width:
    min(
      94vw,
      1650px
    );

  margin: 0 auto;
}


/* =========================================================
   HEADER
========================================================= */

.head {
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap:
    clamp(
      2rem,
      5vw,
      6rem
    );
}


.kicker {
  margin: 0;

  color: #987b49;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.52rem,
      0.58vw,
      0.68rem
    );

  font-weight: 400;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}


.title {
  margin:
    clamp(
      0.5rem,
      0.9vh,
      0.8rem
    )
    0
    0;

  font-family:
    sans-serif;

  font-size:
    clamp(
      2rem,
      2.5vw,
      3.5rem
    );

  font-weight: 400;

  line-height: 1;

  letter-spacing: 0.005em;
}


.section-desc {
  max-width: 540px;

  margin:
    clamp(
      0.8rem,
      1.5vh,
      1.2rem
    )
    0
    0;

  color: #77736d;

font-family:
    sans-serif;

  font-size:
    clamp(
      0.65rem,
      0.72vw,
      0.82rem
    );

  line-height: 1.7;
}


.view-all {
  flex-shrink: 0;

  padding-bottom: 0.3rem;

  border-bottom:
    1px solid
    rgba(17, 17, 17, 0.35);

  color: #111111;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.55rem,
      0.61vw,
      0.68rem
    );

  letter-spacing: 0.08em;

  text-decoration: none;

  text-transform: uppercase;
}


/* =========================================================
   FILTERS
========================================================= */

.filters {
  display: flex;

  flex-wrap: wrap;

  gap: 0.5rem;

  margin:
    clamp(
      1.4rem,
      2.5vh,
      2rem
    )
    0
    clamp(
      1.7rem,
      3vh,
      2.4rem
    );
}


.filters button {
  min-width:
    clamp(
      58px,
      4.5vw,
      80px
    );

  padding:
    clamp(
      0.45rem,
      0.55vw,
      0.55rem
    )
    clamp(
      0.8rem,
      1vw,
      1.05rem
    );

  border:
    1px solid
    rgba(17, 17, 17, 0.8);

  border-radius: 100px;

  background: transparent;

  color: #111111;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.58rem,
      1.44vw,
      0.72rem
    );

  cursor: pointer;

  transition:
    background 0.3s ease,
    color 0.3s ease;
}


.filters button:hover,
.filters button.on {
  background: #111111;

  color: #ffffff;
}


/* =========================================================
   GRID
========================================================= */

.grid {
  display: grid;

  grid-template-columns:
    repeat(
      4,
      minmax(0, 1fr)
    );

  gap:
    clamp(
      0.9rem,
      1.2vw,
      1.25rem
    );
}


/* =========================================================
   PROPERTY CARD
========================================================= */

.project-card {
  display: flex;

  flex-direction: column;

  overflow: hidden;

  background: #ffffff;

  border:
    1px solid
    rgba(17, 17, 17, 0.1);



  box-shadow:
    0
    6px
    24px
    rgba(0, 0, 0, 0.04);

  transition:
    transform 0.4s ease,
    box-shadow 0.4s ease;
}


.project-card:hover {
  transform:
    translateY(-6px);

  box-shadow:
    0
    20px
    50px
    rgba(0, 0, 0, 0.09);
}


/* =========================================================
   IMAGE
========================================================= */

.image-wrap {
  width: 100%;

  height:
    clamp(
      220px,
      21vw,
      355px
    );

  position: relative;

  overflow: hidden;

  background: #111111;
}


.image-wrap img {
  width: 100%;
  height: 100%;

  object-fit: cover;

  transition:
    transform 0.8s
    cubic-bezier(
      0.22,
      1,
      0.36,
      1
    );
}


.project-card:hover .image-wrap img {
  transform:
    scale(1.045);
}


.image-shade {
  position: absolute;

  inset: 0;

  background:
    linear-gradient(
      180deg,
      rgba(0, 0, 0, 0) 45%,
      rgba(0, 0, 0, 0.5) 100%
    );

  pointer-events: none;
}


/* =========================================================
   BADGES
========================================================= */

.badges {
  position: absolute;

  z-index: 4;

  left:
    clamp(
      0.65rem,
      0.9vw,
      0.85rem
    );

  bottom:
    clamp(
      0.7rem,
      1vw,
      0.9rem
    );

  display: flex;

  flex-wrap: wrap;

  gap:
    clamp(
      0.35rem,
      0.45vw,
      0.45rem
    );
}


.badge {
  padding:
    0.38rem
    0.65rem;

  border-radius:
    0.35rem;

  background:
    rgba(
      255,
      255,
      255,
      0.93
    );

  color: #111111;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.46rem,
      0.5vw,
      0.58rem
    );

  font-weight: 500;

  letter-spacing: 0.03em;
}


.badge-ready {
  background: #f3f3ef;

  color: #111111;
}


.badge-ongoing {
  background: #4c8cb8;

  color: #ffffff;
}


.badge-newly-launched,
.badge-new {
  background: #43a995;

  color: #ffffff;
}


.badge-best-selling,
.badge-featured {
  background:
    rgba(
      255,
      255,
      255,
      0.94
    );

  color: #333333;
}


.badge-limited {
  background: #a8864b;

  color: #ffffff;
}


/* =========================================================
   CONTENT
========================================================= */

.content {
  flex: 1;

  display: flex;

  flex-direction: column;

  padding:
    clamp(
      1.1rem,
      1.5vw,
      1.5rem
    );
}


.property-type {
  margin: 0 0 0.45rem;

  color: #8c8881;

 font-family:
    sans-serif;

  font-size:
    clamp(
      0.58rem,
      1.66vw,
      0.74rem
    );
}


.property-title {
  margin: 0;

  color: #111111;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.02rem,
      3.15vw,
      1.5rem
    );

  font-weight: 400;

  line-height: 1.28;

  letter-spacing: -0.001em;
}


/* =========================================================
   LOCATION
========================================================= */

.location {
  display: flex;

  align-items: center;

  gap: 0.4rem;

  margin-top: 0.6rem;

  color: #252525;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.62rem,
      0.68vw,
      0.76rem
    );

  font-weight: 600;
}


.location svg {
  width:
    clamp(
      14px,
      1vw,
      17px
    );

  height:
    clamp(
      14px,
      1vw,
      17px
    );

  fill: none;

  stroke: #a6864d;

  stroke-width: 1.7;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.description {
  margin:
    clamp(
      0.9rem,
      1.4vh,
      1.2rem
    )
    0;

  color: #77736d;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.61rem,
      0.67vw,
      0.76rem
    );

  line-height: 1.65;
}


/* =========================================================
   FEATURES
========================================================= */

.features {
  display: grid;

  grid-template-columns:
    repeat(
      2,
      minmax(0, 1fr)
    );

  gap:
    clamp(
      0.7rem,
      1vw,
      1rem
    )
    clamp(
      0.8rem,
      1.2vw,
      1.3rem
    );

  margin:
    clamp(
      0.6rem,
      1vh,
      0.8rem
    )
    0
    clamp(
      1.2rem,
      2vh,
      1.6rem
    );
}


.feature {
  display: flex;

  align-items: center;

  gap:
    clamp(
      0.5rem,
      0.65vw,
      0.7rem
    );

  min-width: 0;
}


.feature-icon {
  width:
    clamp(
      24px,
      1.7vw,
      30px
    );

  height:
    clamp(
      24px,
      1.7vw,
      30px
    );

  flex-shrink: 0;

  display: grid;

  place-items: center;

  color: #444444;
}


.feature-icon svg {
  width: 100%;
  height: 100%;

  fill: none;

  stroke: currentColor;

  stroke-width: 1.5;

  stroke-linecap: round;

  stroke-linejoin: round;
}


.parking-icon {
  border:
    1.5px solid
    #555555;

  border-radius: 0.2rem;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.8rem,
      1vw,
      1rem
    );

  font-weight: 600;
}


.feature span {
  color: #55514c;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.57rem,
      0.64vw,
      0.72rem
    );

  line-height: 1.35;
}


/* =========================================================
   CARD FOOTER
========================================================= */

.card-footer {
  margin-top: auto;

  padding-top:
    clamp(
      1rem,
      1.6vh,
      1.3rem
    );

  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap: 1rem;

  border-top:
    1px solid
    #eceae6;
}


/* =========================================================
   PRICE
========================================================= */

.price {
  display: grid;

  grid-template-columns:
    auto
    auto;

  align-items: baseline;

  column-gap: 0.35rem;
}


.price small {
  grid-column:
    1 / -1;

  margin-bottom: 0.2rem;

  color: #8d8982;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.43rem,
      0.48vw,
      0.54rem
    );

  letter-spacing: 0.1em;
}


.currency {
  color: #77736d;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.58rem,
      0.64vw,
      0.72rem
    );
}


.price strong {
  color: #111111;

  font-family:
    sans-serif;
  font-size:
    clamp(
      1.55rem,
      1.8vw,
      2rem
    );

  font-weight: 600;

  line-height: 1;
}


/* =========================================================
   EXPLORE BUTTON
========================================================= */

.explore {
  min-width:
    clamp(
      110px,
      8vw,
      135px
    );

  min-height:
    clamp(
      40px,
      3.1vw,
      48px
    );

  padding:
    0
    clamp(
      0.8rem,
      1vw,
      1rem
    );

  display: flex;

  align-items: center;

  justify-content: center;

  gap:
    clamp(
      0.65rem,
      0.9vw,
      1rem
    );

  border:
    1px solid
    #b49657;

  border-radius: 100px;

  background: #ffffff;

  color: #111111;

  font-family:
    sans-serif;

  font-size:
    clamp(
      0.55rem,
      0.62vw,
      0.7rem
    );

  font-weight: 600;

  letter-spacing: 0.04em;

  text-decoration: none;

  text-transform: uppercase;

  transition:
    background 0.3s ease,
    color 0.3s ease,
    transform 0.3s ease;
}


.explore:hover {
  background: #111111;

  color: #ffffff;

  transform:
    translateX(2px);
}


.arrow {
  font-size:
    clamp(
      0.9rem,
      1.1vw,
      1.2rem
    );

  line-height: 1;
}


/* =========================================================
   LARGE TABLET
========================================================= */

@media (max-width: 1200px) {

  .grid {
    grid-template-columns:
      repeat(
        2,
        minmax(0, 1fr)
      );
  }


  .image-wrap {
    height:
      clamp(
        260px,
        32vw,
        400px
      );
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 620px) {

  .sec {
    padding:
      clamp(
        3.5rem,
        7vh,
        5rem
      )
      0;
  }


  .shell {
    width: 91vw;
  }


  .head {
    align-items: flex-start;

    flex-direction: column;

    gap: 1rem;
  }


  .title {
    font-size:
      clamp(
        2.3rem,
        10vw,
        3.2rem
      );
  }


  .grid {
    grid-template-columns: 1fr;
  }


  .image-wrap {
    height:
      clamp(
        260px,
        70vw,
        380px
      );
  }


  .content {
    padding:
      clamp(
        1.1rem,
        5vw,
        1.5rem
      );
  }


  .features {
    grid-template-columns:
      1fr
      1fr;
  }


  .card-footer {
    align-items: center;
  }


  .explore {
    min-width: 120px;
  }

}


/* =========================================================
   VERY SMALL MOBILE
========================================================= */

@media (max-width: 390px) {

  .features {
    grid-template-columns: 1fr;
  }


  .card-footer {
    align-items: flex-start;

    flex-direction: column;
  }


  .explore {
    width: 100%;
  }

}

</style>