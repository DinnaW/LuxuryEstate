<template>
  <section class="places">

    <div class="shell intro">

      <div>

        <p class="kicker">
          EXPLORE SRI LANKA
        </p>

        <h2 class="title">
          Places worth
      
          calling home.
        </h2>

      </div>


      <p>
        Discover distinctive neighbourhoods, coastal escapes
        and connected city addresses selected for modern living.
      </p>

    </div>


    <div class="row">

      <a
        v-for="a in areas"
        :key="a.name"
        href="#"
      >

        <img
          :src="a.img"
          :alt="a.name"
        />

        <div class="shade"></div>


        <div class="copy">

          <h3>
            {{ a.name }}
          </h3>

          <p>
            View residences →
          </p>

        </div>

      </a>

    </div>

  </section>
</template>

<script setup>
const areas = [
  {
    name: "Colombo",
    img:
      "src/images/Colombo.jpeg"
  },
  {
    name: "Galle",
    img:
      "src/images/Galle.webp"
  },
  {
    name: "Thalpe",
    img:
      "src/images/mirissa.webp"
  },
  {
    name: "Mirissa",
    img:
      "src/images/Thalpe.webp"
  },
  {
    name: "Nuwaraeliya",
    img:
      "src/images/weligama.webp"
  }
];
</script>

<style scoped>
.places {
  padding:
    clamp(4rem, 7vh, 6rem)
    0;

  background: #0b0b0b;

  color: #ffffff;
}

.shell {
  width: min(
    91vw,
    1550px
  );

  margin: 0 auto;
}

.intro {
  display: grid;

  grid-template-columns:
    1fr
    0.8fr;

  gap:
    clamp(
      3rem,
      7vw,
      8rem
    );

  align-items: flex-end;

  margin-bottom: 2rem;
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

.intro h2 {
  margin: 0.45rem 0;

  font-family: Georgia, "Times New Roman", serif;

  font-weight: 400;
}

/* KEEP THIS AFTER ALL OTHER HEADING CSS */
.places .intro h2.title {
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
.intro > p {
  max-width: 520px;

  color:
    rgba(
      255,
      255,
      255,
      0.48
    );

  font-size: clamp(
    0.68rem,
    0.95vw,
    0.84rem
  );

  line-height: 1.7;
}

.row {
  display: flex;

  width: 100%;

  overflow: hidden;
}


/* DEFAULT PANEL */

.row > a {
  flex: 1 1 20%;

  height:
    clamp(
      470px,
      58vh,
      660px
    );

  position: relative;

  overflow: hidden;

  color: #ffffff;

  text-decoration: none;

  border-right:
    1px solid
    rgba(255, 255, 255, 0.35);

  transition:
    flex 0.7s cubic-bezier(0.22, 1, 0.36, 1),
    filter 0.5s ease;
}


/* REMOVE BORDER LAST */

.row > a:last-child {
  border-right: 0;
}
.row > a:hover .copy {
  transform:
    translateY(-8px);
}
.row > a:hover .copy p {
  padding-right: 0.35rem;
}
/* IMAGE */

.row img {
  width: 100%;
  height: 100%;

  object-fit: cover;

  filter:
    saturate(0.72)
    brightness(0.88);

  transform:
    scale(1.02);

  transition:
    transform 0.9s cubic-bezier(0.22, 1, 0.36, 1),
    filter 0.6s ease;
}


/* =========================
   BIG HOVER EFFECT
========================= */

.row:hover > a {
  flex: 0.82 1 16%;
}


/* HOVERED PANEL BECOMES BIG */

.row > a:hover {
  flex: 1.9 1 26%;
}


/* IMAGE ZOOM */

.row > a:hover img {
  transform:
    scale(1.07);

  filter:
    saturate(0.9)
    brightness(0.98);
}


.shade {
  position: absolute;

  inset: 0;

  background:
    linear-gradient(
      0deg,
      rgba(0, 0, 0, 0.82) 0%,
      rgba(0, 0, 0, 0.42) 30%,
      rgba(0, 0, 0, 0.04) 68%
    );

  transition:
    background 0.6s ease;
}


.row > a:hover .shade {
  background:
    linear-gradient(
      0deg,
      rgba(0, 0, 0, 0.72) 0%,
      rgba(0, 0, 0, 0.25) 32%,
      rgba(0, 0, 0, 0.02) 68%
    );
}

.copy {
  position: absolute;

  z-index: 2;

  left:
    clamp(
      1rem,
      1.4vw,
      1.5rem
    );

  right:
    clamp(
      1rem,
      1.4vw,
      1.5rem
    );

  bottom:
    clamp(
      1.1rem,
      1.7vw,
      1.7rem
    );

  transition:
    transform 0.55s cubic-bezier(0.22, 1, 0.36, 1);
}


.copy h3 {
  margin:
    0
    0
    0.6rem;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      1.5rem,
      0.2vw,
      1.4rem
    );

  font-weight: 400;

  line-height: 1;

  color: #ffffff;

  white-space: nowrap;
}


.copy p {
  width: fit-content;

  margin: 0;

  padding-bottom: 0.2rem;

  border-bottom:
    1px solid
    rgba(255, 255, 255, 0.8);

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

  color: #ffffff;
}


@media (max-width: 900px) {

  .row {
    display: grid;

    grid-template-columns:
      1fr
      1fr;
  }


  .row > a,
  .row:hover > a,
  .row > a:hover {
    flex: none;
  }


  .row > a {
    height:
      clamp(
        420px,
        55vh,
        560px
      );
  }

}


/* =========================
   MOBILE
========================= */

@media (max-width: 560px) {

  .row {
    grid-template-columns: 1fr;
  }


  .row > a {
    height:
      clamp(
        420px,
        68vh,
        560px
      );
  }


  .row > a:hover img {
    transform:
      scale(1.04);
  }

}
</style>