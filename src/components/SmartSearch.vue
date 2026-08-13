<template>
  <section class="smart">

    <div class="shell grid">

      <!-- =========================
           LEFT IMAGE
      ========================== -->
      <div class="visual">

        <img
          src="https://images.unsplash.com/photo-1600210492486-724fe5c67fb0?auto=format&fit=crop&w=1400&q=90"
          alt="Luxury apartment interior"
        />

        <div class="visual-overlay"></div>

        <div class="visual-content">

          <p class="kicker">
            TAILORED SEARCH
          </p>

          <h2 class="title">
            Find the place
           
            that feels right.
          </h2>

          <p class="visual-text">
            Explore residences shaped around your location,
            lifestyle and preferred way of living.
          </p>

        </div>

      </div>


      <!-- =========================
           SEARCH FORM
      ========================== -->
      <form
        class="search-form"
        @submit.prevent="searchResidences"
      >

        <p class="kicker form-kicker">
          START YOUR SEARCH
        </p>

        <h3>
          Choose your preferences
        </h3>

        <p class="form-intro">
          Tell us what you are looking for and discover
          residences that match your requirements.
        </p>


        <!-- PROPERTY TYPE -->
        <div class="tabs">

          <button
            v-for="t in types"
            :key="t"
            type="button"
            :class="{ on: type === t }"
            @click="type = t"
          >
            {{ t }}
          </button>

        </div>


        <!-- LOCATION -->
        <label>

          <span>
            Location
          </span>

          <select v-model="filters.location">

            <option value="">
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


        <!-- BEDROOMS -->
        <label>

          <span>
            Bedrooms
          </span>

          <select v-model="filters.bedrooms">

            <option value="">
              Any bedrooms
            </option>

            <option>
              1 Bedroom
            </option>

            <option>
              2 Bedrooms
            </option>

            <option>
              3 Bedrooms
            </option>

            <option>
              4+ Bedrooms
            </option>

          </select>

        </label>


        <!-- PRICE -->
        <label>

          <span>
            Price Range
          </span>

          <select v-model="filters.price">

            <option value="">
              Any price
            </option>

            <option>
              USD 150K – 250K
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


        <!-- BUTTON -->
        <button
          class="submit"
          type="submit"
        >

          <span>
            Search residences
          </span>

          <span class="submit-arrow">
            →
          </span>

        </button>

      </form>

    </div>

  </section>
</template>


<script setup>
import {
  reactive,
  ref
} from "vue";


const types = [
  "Apartment",
  "Penthouse",
  "Villa"
];


const type = ref(
  "Apartment"
);


const filters = reactive({

  location: "",

  bedrooms: "",

  price: ""

});


const searchResidences = () => {

  console.log({

    type:
      type.value,

    location:
      filters.location,

    bedrooms:
      filters.bedrooms,

    price:
      filters.price

  });

};

</script>


<style scoped>

/* =========================================
   SECTION
========================================= */

.smart {
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
      91vw,
      1550px
    );

  margin:
    0
    auto;
}


/* =========================================
   GRID
========================================= */

.grid {
  display: grid;

  grid-template-columns:
    1.25fr
    0.75fr;

  gap:
    clamp(
      1rem,
      1.5vw,
      1.5rem
    );
}


/* =========================================
   LEFT IMAGE
========================================= */

.visual {
  min-height:
    clamp(
      500px,
      64vh,
      720px
    );

  position: relative;

  overflow: hidden;

  background: #111111;
}


.visual > img {
  width: 100%;
  height: 100%;

  position: absolute;

  inset: 0;

  object-fit: cover;

  transition:
    transform
    0.8s
    ease;
}


.visual:hover > img {
  transform:
    scale(1.035);
}


/* =========================================
   IMAGE OVERLAY
========================================= */

.visual-overlay {
  position: absolute;

  inset: 0;

  z-index: 1;

  background:
    linear-gradient(
      180deg,
      rgba(
        0,
        0,
        0,
        0.03
      )
      30%,

      rgba(
        0,
        0,
        0,
        0.18
      )
      58%,

      rgba(
        0,
        0,
        0,
        0.76
      )
      100%
    );
}


/* =========================================
   IMAGE CONTENT
========================================= */

.visual-content {
  position: absolute;

  z-index: 2;

  left:
    clamp(
      1.4rem,
      2.2vw,
      2.4rem
    );

  right:
    clamp(
      1.4rem,
      2.2vw,
      2.4rem
    );

  bottom:
    clamp(
      1.5rem,
      3vw,
      3rem
    );

  max-width:
    650px;

  color:
    #ffffff;
}


/* =========================================
   KICKER
========================================= */

.kicker {
  margin: 0;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.52rem,
      0.58vw,
      0.68rem
    );

  font-weight:
    400;

  line-height:
    1.2;

  letter-spacing:
    0.18em;

  text-transform:
    uppercase;
}


/* =========================================
   LEFT TITLE
========================================= */

.visual-content .title {
  margin:
    clamp(
      0.55rem,
      1vh,
      0.8rem
    )
    0;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      rem,
      0.4vw,
      5.4rem
    );

  font-weight:
    400;

  line-height:
    0.94;

  letter-spacing:
    0.012em;

  color:
    #ffffff;
}


/* =========================================
   LEFT DESCRIPTION
========================================= */

.visual-text {
  width:
    min(
      90%,
      500px
    );

  margin:
    clamp(
      0.8rem,
      1.5vh,
      1rem
    )
    0
    0;

  color:
    rgba(
      255,
      255,
      255,
      0.74
    );

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.66rem,
      0.72vw,
      0.82rem
    );

  line-height:
    1.65;
}


/* =========================================
   FORM
========================================= */

.search-form {
  min-height:
    clamp(
      500px,
      64vh,
      720px
    );

  padding:
    clamp(
      1.6rem,
      2.5vw,
      2.7rem
    );

  display:
    flex;

  flex-direction:
    column;

  justify-content:
    center;

  background:
    #f3efe8;

  border:
    1px
    solid
    rgba(
      0,
      0,
      0,
      0.08
    );
}


/* =========================================
   FORM SMALL TITLE
========================================= */

.form-kicker {
  color:
    #777777;
}


/* =========================================
   FORM TITLE
========================================= */

.search-form h3 {
  margin:
    clamp(
      0.45rem,
      0.8vh,
      0.7rem
    )
    0
    0;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      1.7rem,
      2.1vw,
      4.8rem
    );

  font-weight: 400;

  line-height: 1.71;

  letter-spacing: 0.01em;
}


/* =========================================
   FORM DESCRIPTION
========================================= */

.form-intro {
  margin:
    0
    0
    clamp(
      1rem,
      2vh,
      1.5rem
    );

  color:
    #777777;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.64rem,
      0.7vw,
      0.8rem
    );

  line-height:
    1.6;
}


/* =========================================
   PROPERTY TYPE TABS
========================================= */

.tabs {
  width: 100%;

  display:
    flex;

  margin-bottom:
    clamp(
      0.5rem,
      1vh,
      0.8rem
    );
}


.tabs button {
  flex:
    1;

  min-height:
    clamp(
      2.7rem,
      3vw,
      3.1rem
    );

  padding:
    0
    clamp(
      0.5rem,
      0.8vw,
      0.8rem
    );

  border:
    1px
    solid
    #111111;

  border-right:
    0;

  background:
    transparent;

  color:
    #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.58rem,
      0.64vw,
      0.72rem
    );

  cursor:
    pointer;

  transition:
    background
    0.3s
    ease,
    color
    0.3s
    ease;
}


.tabs button:last-child {
  border-right:
    1px
    solid
    #111111;
}


.tabs button:hover,
.tabs .on {
  background:
    #111111;

  color:
    #ffffff;
}


/* =========================================
   LABEL
========================================= */

.search-form label {
  display:
    block;

  margin-top:
    clamp(
      0.7rem,
      1.2vh,
      0.95rem
    );

  font-family:
    Georgia,
    "Times New Roman",
    serif;
}


.search-form label > span {
  display:
    block;

  margin-bottom:
    clamp(
      0.3rem,
      0.5vh,
      0.4rem
    );

  font-size:
    clamp(
      0.54rem,
      0.6vw,
      0.68rem
    );

  font-weight:
    400;

  letter-spacing:
    0.08em;

  text-transform:
    uppercase;
}


/* =========================================
   SELECT
========================================= */

.search-form select {
  width:
    100%;

  min-height:
    clamp(
      2.8rem,
      3.2vw,
      3.2rem
    );

  padding:
    0
    clamp(
      0.8rem,
      1vw,
      1rem
    );

  border:
    1px
    solid
    #cccccc;

  outline:
    none;

  background:
    #ffffff;

  color:
    #555555;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.62rem,
      0.68vw,
      0.76rem
    );

  cursor:
    pointer;

  transition:
    border-color
    0.25s
    ease;
}


.search-form select:focus {
  border-color:
    #111111;
}


/* =========================================
   SEARCH BUTTON
========================================= */

.submit {
  width:
    100%;

  min-height:
    clamp(
      3.1rem,
      3.5vw,
      3.6rem
    );

  margin-top:
    clamp(
      1.2rem,
      2vh,
      1.6rem
    );

  padding:
    0
    clamp(
      1rem,
      1.4vw,
      1.4rem
    );

  display:
    flex;

  align-items:
    center;

  justify-content:
    space-between;

  border:
    1px
    solid
    #111111;

  background:
    #111111;

  color:
    #ffffff;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.56rem,
      0.62vw,
      0.7rem
    );

  font-weight:
    400;

  letter-spacing:
    0.08em;

  text-transform:
    uppercase;

  cursor:
    pointer;

  transition:
    background
    0.3s
    ease,
    color
    0.3s
    ease;
}


.submit-arrow {
  font-size:
    clamp(
      0.9rem,
      1vw,
      1.1rem
    );

  transition:
    transform
    0.3s
    ease;
}


.submit:hover {
  background:
    #ffffff;

  color:
    #111111;
}


.submit:hover
.submit-arrow {
  transform:
    translateX(
      5px
    );
}


/* =========================================
   TABLET
========================================= */

@media
(max-width: 900px) {

  .grid {
    grid-template-columns:
      1fr;
  }


  .visual {
    min-height:
      clamp(
        480px,
        62vh,
        650px
      );
  }


  .search-form {
    min-height:
      auto;

    padding:
      clamp(
        2rem,
        5vw,
        3rem
      );
  }

}


/* =========================================
   MOBILE
========================================= */

@media
(max-width: 600px) {

  .smart {
    padding:
      clamp(
        3.5rem,
        7vh,
        5rem
      )
      0;
  }


  .shell {
    width:
      92vw;
  }


  .visual {
    min-height:
      clamp(
        440px,
        65vh,
        580px
      );
  }


  .visual-content .title {
    font-size:
      clamp(
        2.7rem,
        12vw,
        4rem
      );
  }


  .tabs {
    flex-direction:
      column;
  }


  .tabs button {
    border-right:
      1px
      solid
      #111111;

    border-bottom:
      0;
  }


  .tabs button:last-child {
    border-bottom:
      1px
      solid
      #111111;
  }


  .search-form {
    padding:
      clamp(
        1.4rem,
        5vw,
        2rem
      );
  }

}

</style>