<template>
  <section class="popular">

    <div class="shell">

      <div class="head">

        <p class="kicker">
          DISCOVER MORE
        </p>

        <h2 class="title">
          Popular searches
        </h2>

      </div>


      <div class="cols">

        <div
          v-for="g in groups"
          :key="g.title"
        >

          <h3>
            {{ g.title }}
          </h3>


          <a
            v-for="x in g.items"
            :key="x"
            href="#"
          >
            {{ x }}
          </a>


          <a
            class="more"
            href="#"
          >
            View more →
          </a>

        </div>

      </div>

    </div>

  </section>
</template>

<script setup>
const groups = [
  {
    title: "Apartments",
    items: [
      "Luxury apartments in Colombo",
      "Apartments in Colombo 03",
      "Apartments in Colombo 07",
      "Ocean-view apartments",
      "Ready residences"
    ]
  },
  {
    title: "Investment",
    items: [
      "High-yield residences",
      "Rental-ready apartments",
      "Long-term investment homes",
      "New launch opportunities",
      "Prime-location property"
    ]
  },
  {
    title: "Locations",
    items: [
      "Colombo residences",
      "Colombo 03 residences",
      "Colombo 07 residences",
      "Galle residences",
      "Thalpe residences"
    ]
  },
  {
    title: "Lifestyle",
    items: [
      "Ocean-view living",
      "City-centre living",
      "Private amenity residences",
      "Family apartments",
      "Penthouse living"
    ]
  }
];
</script>

<style scoped>
.popular {
  padding:
    clamp(4.5rem, 8vh, 7rem)
    0;

  background: #ffffff;
}

.shell {
  width: min(
    91vw,
    1550px
  );

  margin: 0 auto;
}

.head {
  text-align: center;

  margin-bottom:
    clamp(
      2.5rem,
      5vh,
      3.5rem
    );
}

.kicker {
  margin: 0;

  font-size: clamp(
    0.52rem,
    0.58vw,
    0.68rem
  );

  letter-spacing: 0.18em;

  color: #777777;
}

.head h2 {
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
      2.3vw,
      4.8rem
    );

  font-weight: 400;

  line-height: 0.96;

  letter-spacing: 0.01em;
}

.head h2::before,
.head h2::after {
  content: "";

  position: absolute;

  top: 50%;

  width: 18vw;
  height: 1px;

  background: #dddddd;
}

.head h2::before {
  right: 100%;
}

.head h2::after {
  left: 100%;
}

.cols {
  display: grid;

  grid-template-columns:
    repeat(
      4,
      1fr
    );

  gap:
    clamp(
      2rem,
      4vw,
      4rem
    );
}

.cols h3 {
  margin:
    0
    0
    1rem;

  padding-bottom: 0.6rem;

  color: #666666;

  border-bottom:
    1px solid
    #cccccc;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size: clamp(
    1.15rem,
    1.3vw,
    1.4rem
  );

  font-weight: 400;
}

.cols a {
  display: block;

  margin:
    0.75rem
    0;

  color: #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size: clamp(
    0.64rem,
    0.7vw,
    0.78rem
  );

  text-decoration: none;
}

.cols a:hover {
  text-decoration: underline;
}

.cols .more {
  margin-top: 1.4rem;

  font-size: clamp(
    0.5rem,
    0.56vw,
    0.62rem
  );

  font-weight: 400;

  text-transform: uppercase;

  letter-spacing: 0.08em;
}

@media (max-width: 800px) {
  .cols {
    grid-template-columns:
      1fr
      1fr;
  }
}

@media (max-width: 480px) {
  .cols {
    grid-template-columns:
      1fr;
  }

  .head h2::before,
  .head h2::after {
    display: none;
  }
}
</style>