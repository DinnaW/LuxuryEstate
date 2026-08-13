<template>
  <section class="deals">

    <div class="shell">

      <!-- =========================
           HEADER
      ========================== -->
      <div class="head">

        <div>
          <p class="kicker">
            SELECTED OPPORTUNITIES
          </p>

          <h2 class="title">
            Hot Deal Residences
          </h2>
        </div>

        <a
          href="#"
          class="view-more"
        >
          View more →
        </a>

      </div>


      <!-- =========================
           DEAL CAROUSEL
      ========================== -->
      <div class="track">

        <article
          v-for="d in deals"
          :key="d.name"
          class="deal-card"
        >

          <!-- IMAGE -->
          <div class="pic">

            <img
              :src="d.img"
              :alt="d.name"
            />

            <span>
              {{ d.tag }}
            </span>

          </div>


          <!-- CONTENT -->
          <div class="copy">

            <small>
              {{ d.location }}
            </small>

            <h3>
              {{ d.name }}
            </h3>

            <p>
              {{ d.meta }}
            </p>

            <div class="card-bottom">

              <b>
                {{ d.price }}
              </b>

              <a href="#">
                View →
              </a>

            </div>

          </div>

        </article>

      </div>

    </div>

  </section>
</template>


<script setup>

const deals = [

  {
    tag: "FEATURED",

    location: "Colombo 03",

    name: "Ocean Avenue Residence",

    meta: "3 Bed · 2,150 sq.ft",

    price: "USD 520K",

    img:
      "https://images.unsplash.com/photo-1600585154340-be6161a56a0c?auto=format&fit=crop&w=800&q=90"
  },


  {
    tag: "NEW",

    location: "Colombo 07",

    name: "Parkside Penthouse",

    meta: "4 Bed · 3,400 sq.ft",

    price: "USD 780K",

    img:
      "https://images.unsplash.com/photo-1600607687920-4e2a09cf159d?auto=format&fit=crop&w=800&q=90"
  },


  {
    tag: "READY",

    location: "Galle",

    name: "South Coast Residence",

    meta: "3 Bed · 2,480 sq.ft",

    price: "USD 465K",

    img:
      "https://images.unsplash.com/photo-1600566753190-17f0baa2a6c3?auto=format&fit=crop&w=800&q=90"
  },


  {
    tag: "LIMITED",

    location: "Thalpe",

    name: "Garden Courtyard Home",

    meta: "2 Bed · 1,890 sq.ft",

    price: "USD 355K",

    img:
      "https://images.unsplash.com/photo-1600210492486-724fe5c67fb0?auto=format&fit=crop&w=800&q=90"
  },


  {
    tag: "VIEW",

    location: "Colombo",

    name: "Skyline Apartment",

    meta: "2 Bed · 1,600 sq.ft",

    price: "USD 295K",

    img:
      "https://images.unsplash.com/photo-1545324418-cc1a3fa10c00?auto=format&fit=crop&w=800&q=90"
  }

];

</script>


<style scoped>

/* =========================
   SECTION
========================= */

.deals {
  width: 100%;

  padding:
    clamp(4rem, 7vh, 6rem)
    0;

  background: #efefef;

  color: #111111;

  overflow: hidden;
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

  justify-content: space-between;

  align-items: flex-end;

  gap:
    clamp(1.5rem, 3vw, 3rem);

  margin-bottom:
    clamp(1.4rem, 2.5vh, 2rem);
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
      0.66rem
    );

  font-weight: 400;

  letter-spacing: 0.18em;

  text-transform: uppercase;

  color: #666666;
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


.view-more {
  color: #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.56rem,
      0.62vw,
      0.68rem
    );

  text-transform: uppercase;

  letter-spacing: 0.08em;

  text-decoration: none;

  padding-bottom: 0.25rem;

  border-bottom:
    1px solid
    rgba(0, 0, 0, 0.2);
}


/* =========================
   TRACK
========================= */

.track {
  display: flex;

  gap:
    clamp(
      0.8rem,
      1vw,
      1rem
    );

  overflow-x: auto;

  overflow-y: hidden;

  scroll-snap-type: x mandatory;

  scroll-behavior: smooth;

  scrollbar-width: none;

  -webkit-overflow-scrolling: touch;
}


.track::-webkit-scrollbar {
  display: none;
}


/* =========================
   CARD
========================= */

.deal-card {
  flex:
    0
    0
    clamp(
      230px,
      21vw,
      310px
    );

  background: #ffffff;

  border:
    1px solid
    rgba(0, 0, 0, 0.1);

  overflow: hidden;

  scroll-snap-align: start;

  transition:
    transform 0.35s ease,
    box-shadow 0.35s ease;
}


.deal-card:hover {
  transform:
    translateY(-5px);

  box-shadow:
    0
    clamp(
      0.8rem,
      2vh,
      1.5rem
    )
    clamp(
      1.8rem,
      3vw,
      3rem
    )
    rgba(0, 0, 0, 0.07);
}


/* =========================
   IMAGE
========================= */

.pic {
  width: 100%;

  height:
    clamp(
      180px,
      18vw,
      250px
    );

  position: relative;

  overflow: hidden;

  background: #111111;
}


.pic img {
  width: 100%;
  height: 100%;

  object-fit: cover;

  transition:
    transform 0.7s ease;
}


.deal-card:hover .pic img {
  transform:
    scale(1.04);
}


/* STATUS */

.pic span {
  position: absolute;

  top:
    clamp(
      0.65rem,
      0.8vw,
      0.8rem
    );

  left:
    clamp(
      0.65rem,
      0.8vw,
      0.8rem
    );

  padding:
    0.32rem
    0.5rem;

  background: #111111;

  color: #ffffff;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.46rem,
      0.5vw,
      0.56rem
    );

  font-weight: 400;

  letter-spacing: 0.1em;
}


/* =========================
   CONTENT
========================= */

.copy {
  padding:
    clamp(
      0.85rem,
      1.1vw,
      1.1rem
    );
}


.copy small {
  display: block;

  color: #777777;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.56rem,
      0.62vw,
      0.68rem
    );
}


.copy h3 {
  margin:
    clamp(
      0.32rem,
      0.6vh,
      0.45rem
    )
    0;

  color: #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      1.25rem,
      1.45vw,
      1.6rem
    );

  font-weight: 400;

  line-height: 1.08;
}


.copy > p {
  margin:
    0
    0
    clamp(
      0.7rem,
      1.1vh,
      0.9rem
    );

  color: #777777;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.6rem,
      0.65vw,
      0.72rem
    );

  line-height: 1.5;
}


/* =========================
   BOTTOM
========================= */

.card-bottom {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 1rem;

  padding-top:
    clamp(
      0.7rem,
      1vh,
      0.85rem
    );

  border-top:
    1px solid
    #eeeeee;
}


.card-bottom b {
  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.7rem,
      0.76vw,
      0.85rem
    );

  font-weight: 400;

  color: #111111;
}


.card-bottom a {
  color: #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.5rem,
      0.55vw,
      0.62rem
    );

  text-transform: uppercase;

  letter-spacing: 0.08em;

  text-decoration: none;
}


/* =========================
   TABLET
========================= */

@media (max-width: 900px) {

  .deal-card {
    flex-basis:
      clamp(
        230px,
        34vw,
        300px
      );
  }

}


/* =========================
   MOBILE
========================= */

@media (max-width: 600px) {

  .deals {
    padding:
      clamp(
        3.5rem,
        7vh,
        5rem
      )
      0;
  }


  .head {
    flex-direction: column;

    align-items: flex-start;
  }


  .title {
    font-size:
      clamp(
        2.5rem,
        11vw,
        3.8rem
      );
  }


  .deal-card {
    flex-basis:
      clamp(
        240px,
        78vw,
        310px
      );
  }


  .pic {
    height:
      clamp(
        200px,
        60vw,
        280px
      );
  }

}

</style>