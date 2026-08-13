<template>
  <section class="sec">

    <div class="shell">

      <!-- =========================
           HEADER
      ========================== -->
      <div class="head">

        <div>
          <p class="kicker">
            CURATED COLLECTION
          </p>

          <h2 class="title">
            Featured Residences
          </h2>
        </div>

        <a href="#" class="view-all">
          View all →
        </a>

      </div>


      <!-- =========================
           FILTERS
      ========================== -->
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


      <!-- =========================
           PROJECT GRID
      ========================== -->
      <div class="grid">

        <article
          v-for="p in shown"
          :key="p.name"
          class="project-card"
        >

          <!-- IMAGE -->
          <div class="img">

            <img
              :src="p.img"
              :alt="p.name"
            />

            <span>
              {{ p.status }}
            </span>

          </div>


          <!-- INFO -->
          <div class="info">

            <h3>
              {{ p.name }}
            </h3>

            <p>
              {{ p.area }} · {{ p.beds }} Bedrooms
            </p>

            <div class="bottom-row">

              <div class="price">
  <small>PRICE</small>
  <b>{{ p.price }}</b>
</div>

              <a href="#">
                View residence →
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
    beds: 3,
    price: "From USD 420K",
    status: "READY",

    img:
      "src/images/Thalpe.webp"
  },
  


  {
    name: "Sotheby's International Realty",
    area: "Colombo",
    beds: 2,
    price: "From USD 310K",
    status: "ONGOING",

    img:
      "src/images/weligama.webp"
  },


  {
    name: "Philippe Philippe ",
    area: "Colombo",
    beds: 4,
    price: "From USD 680K",
    status: "ONGOING",

    img:
      "src/images/Galle.webp"
  },


  {
    name: "Ocean House",
    area: "Galle",
    beds: 3,
    price: "From USD 465K",
    status: "READY",

    img:
      "src/images/nuwaraeliya.webp"
  },


  {
    name: "Thalpe Courtyard",
    area: "Thalpe",
    beds: 2,
    price: "From USD 355K",
    status: "NEW",

    img:
      "src/images/hf_20260724_043544_62932b82-e384-492f-aa3c-8ca7dc82d080.webp"
  }

];


const shown = computed(() => {

  if (active.value === "All") {
    return projects.slice(0, 4);
  }

  return projects.filter(
    (x) => x.area === active.value
  );

});
</script>


<style scoped>

/* =========================
   SECTION
========================= */

.sec {
  width: 100%;

  padding:
    clamp(4.5rem, 8vh, 7rem)
    0;

  background: #ffffff;

  color: #111111;
}


.shell {
  width: min(91vw, 1550px);

  margin: 0 auto;
}


/* =========================
   HEADER
========================= */

.head {
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap:
    clamp(1.5rem, 3vw, 3rem);
}


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

  font-weight: 400;

  letter-spacing: 0.18em;

  text-transform: uppercase;

  color: #6f6f6f;
}


.title {
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

  line-height: 0.96;

  letter-spacing: 0.01em;
}


.view-all {
  padding-bottom: 0.25rem;

  color: #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.58rem,
      0.65vw,
      0.72rem
    );

  text-transform: uppercase;

  letter-spacing: 0.08em;

  text-decoration: none;

  border-bottom:
    1px solid
    rgba(0, 0, 0, 0.25);
}


/* =========================
   FILTERS
========================= */

.filters {
  display: flex;

  flex-wrap: wrap;

  gap:
    clamp(
      0.4rem,
      0.6vw,
      0.6rem
    );

  margin:
    clamp(
      1.2rem,
      2vh,
      1.7rem
    )
    0
    clamp(
      1.5rem,
      2.5vh,
      2rem
    );
}


.filters button {
  border:
    1px solid
    #111111;

  border-radius: 100px;

  background: transparent;

  color: #111111;

  padding:
    clamp(
      0.4rem,
      0.5vw,
      0.5rem
    )
    clamp(
      0.75rem,
      0.9vw,
      0.95rem
    );

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.58rem,
      0.64vw,
      0.7rem
    );

  cursor: pointer;

  transition:
    background 0.3s ease,
    color 0.3s ease;
}


.filters button:hover,
.filters .on {
  background: #111111;

  color: #ffffff;
}


/* =========================
   GRID
========================= */

.grid {
  display: grid;

  grid-template-columns:
    repeat(4, minmax(0, 1fr));

  gap:
    clamp(
      0.7rem,
      0.9vw,
      1rem
    );
}


/* =========================
   CARD
========================= */

.project-card {
  background: #ffffff;

  border:
    1px solid
    rgba(0, 0, 0, 0.12);

  overflow: hidden;

  transition:
    transform 0.35s ease,
    box-shadow 0.35s ease;
}


.project-card:hover {
  transform:
    translateY(-5px);

  box-shadow:
    0
    clamp(
      1rem,
      2vh,
      1.8rem
    )
    clamp(
      2rem,
      3vw,
      3rem
    )
    rgba(0, 0, 0, 0.06);
}


/* =========================
   IMAGE
========================= */

.img {
  height:
    clamp(
      220px,
      23vw,
      340px
    );

  position: relative;
  overflow: hidden;
  background: #111111;
}
.price {
  display: flex;
  flex-direction: column;
  gap: 0.18rem;
}

.price small {
  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size: 0.48rem;
  letter-spacing: 0.14em;
  color: #999999;
}

.price b {
  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size: clamp(0.78rem, 0.85vw, 0.95rem);

  font-weight: 600;
  color: #111111;
}


.img img {
  width: 100%;
  height: 100%;

  object-fit: cover;

  transition:
    transform 0.7s ease;
}


.project-card:hover .img img {
  transform:
    scale(1.04);
}


.img span {
  position: absolute;

  top:
    clamp(
      0.7rem,
      1vw,
      0.9rem
    );

  left:
    clamp(
      0.7rem,
      1vw,
      0.9rem
    );

  background: #111111;

  color: #ffffff;

  padding:
    0.35rem
    0.55rem;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.48rem,
      0.52vw,
      0.58rem
    );

  font-weight: 400;

  letter-spacing: 0.1em;
}


/* =========================
   INFO
========================= */

.info {
  padding:
    clamp(
      0.9rem,
      1.2vw,
      1.2rem
    );
}


.info h3 {
  margin: 0;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size: clamp(1.25rem, 0.45vw, 1.65rem);

  font-weight: 400;
  line-height: 1.08;
}


.info > p {
  margin:
    clamp(
      0.35rem,
      0.7vh,
      0.5rem
    )
    0
    clamp(
      0.75rem,
      1.3vh,
      1rem
    );

  color: #777777;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.6rem,
      0.66vw,
      0.74rem
    );

  line-height: 1.5;
}


/* =========================
   BOTTOM ROW
========================= */

.bottom-row {
  display: flex;
  align-items: center;
  justify-content: space-between;

  gap: 1rem;

  border-top: 1px solid #eeeeee;

  padding-top: 0.9rem;
}


.bottom-row b {
  display: inline-flex;
  align-items: center;

  padding: 0.48rem 0.75rem;

  background: #111111;
  color: #ffffff;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size: clamp(0.68rem, 0.72vw, 0.82rem);

  font-weight: 400;

  letter-spacing: 0.02em;

  white-space: nowrap;
}


.bottom-row a {
  position: relative;

  color: #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size: clamp(0.56rem, 0.6vw, 0.68rem);

  text-transform: uppercase;
  letter-spacing: 0.08em;

  text-decoration: none;
  white-space: nowrap;

  transition: opacity 0.3s ease;
}

.bottom-row a:hover {
  opacity: 0.5;
}


/* =========================
   TABLET
========================= */

/* LARGE TABLET */
@media (max-width: 1100px) {

  .grid {
    grid-template-columns:
      repeat(2, minmax(0, 1fr));
  }

}


/* MOBILE */
@media (max-width: 560px) {

  .sec {
    padding:
      clamp(
        3.5rem,
        7vh,
        5rem
      )
      0;
  }

  .head {
    align-items: flex-start;
    flex-direction: column;
    gap: 1rem;
  }

  .title {
    font-size:
      clamp(
        2.6rem,
        11vw,
        3.8rem
      );
  }

  .grid {
    grid-template-columns: 1fr;
  }

  .img {
    height:
      clamp(
        250px,
        68vw,
        390px
      );
  }

}

</style>