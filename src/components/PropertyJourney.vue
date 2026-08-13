<template>
  <section class="journey">

    <div class="shell">

      <div class="head">

        <div>

          <p class="kicker">
            YOUR PROPERTY JOURNEY
          </p>

          <h2 class="title">
            What would you
           
            like to do?
          </h2>

        </div>


        <p>
          Find the right path for your property journey.
          Explore residences, investment opportunities,
          private viewings and tailored guidance.
        </p>

      </div>


      <div class="cards">

        <article
          v-for="(x, i) in items"
          :key="x.name"
        >

          <div class="num">

            <span>
              0{{ i + 1 }}
            </span>

            <i></i>

          </div>


          <small>
            {{ x.cat }}
          </small>


          <h3>
            {{ x.name }}
          </h3>


          <p>
            {{ x.text }}
          </p>


          <a href="#">

            {{ x.cta }}

            <span>
              →
            </span>

          </a>

        </article>

      </div>

    </div>

  </section>
</template>

<script setup>
const items = [
  {
    cat: "LUXURY RESIDENCES",
    name: "Explore Residences",
    text:
      "Discover exceptional apartments in Sri Lanka’s most desirable residential locations.",
    cta: "View residences"
  },
  {
    cat: "PERSONALISED SEARCH",
    name: "Find Your Ideal Home",
    text:
      "Browse residences by location, lifestyle, size and preferred property type.",
    cta: "Start exploring"
  },
  {
    cat: "SMART INVESTMENT",
    name: "Investment Opportunities",
    text:
      "Explore selected residences with long-term value and investment potential.",
    cta: "Discover more"
  },
  {
    cat: "PRIVATE EXPERIENCE",
    name: "Book a Private Viewing",
    text:
      "Arrange a personal tour and experience your preferred residence in person.",
    cta: "Book viewing"
  },
  {
    cat: "PRIME LOCATIONS",
    name: "Explore Prime Locations",
    text:
      "Discover Colombo, Galle, Thalpe and other prestigious residential destinations.",
    cta: "View locations"
  }
];
</script>

<style scoped>
.journey {
  padding:
    clamp(4rem, 7vh, 6rem)
    0;

  background: #000000;
}

.shell {
  width: min(
    91vw,
    1550px
  );

  margin: 0 auto;
}

.head {
  display: grid;

  grid-template-columns:
    1.1fr
    0.9fr;

  align-items: flex-end;

  gap:
    clamp(
      3rem,
      6vw,
      7rem
    );

  margin-bottom: 2rem;
}

.kicker {
  margin: 0;

  color: #777777;

  font-size: clamp(
    0.52rem,
    0.58vw,
    0.68rem
  );

  letter-spacing: 0.18em;
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
      2.1vw,
      4.8rem
    );

  font-weight: 400;

  line-height: 0.96;

  letter-spacing: 0.01em;
  color: #ffffff;
}

.head > p {
  max-width: 500px;

  color: #777777;

  font-size: clamp(
    0.66rem,
    0.72vw,
    0.82rem
  );

  line-height: 1.7;
}

.cards {
  display: grid;

  grid-template-columns:
    repeat(
      5,
      1fr
    );

  gap:
    clamp(
      0.7rem,
      1vw,
      1rem
    );
}

.cards article {
  min-height:
    clamp(
      270px,
      32vh,
      310px
    );

  padding:
    clamp(
      1.1rem,
      1.3vw,
      1.35rem
    );

  display: flex;

  flex-direction: column;

  background: #ffffff;

  border:
    1px solid
    #dddddd;

  transition:
    transform 0.3s ease,
    border-color 0.3s ease;
}

.cards article:hover {
  transform:
    translateY(-5px);

  border-color: #111111;
}

.num {
  display: flex;

  align-items: center;

  gap: 0.7rem;
}

.num span {
  font-size: 1.1rem;
}

.num i {
  flex: 1;

  height: 1px;

  background: #dddddd;
}

.cards small {
  margin-top: 1.4rem;

  color: #777777;

  font-size: 0.5rem;

  letter-spacing: 0.12em;
}

.cards h3 {
  margin:
    0.4rem
    0;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size: clamp(
    1.3rem,
    1.45vw,
    1.6rem
  );

  font-weight: 400;

  line-height: 1.05;
}

.cards p {
  color: #777777;

  font-size: clamp(
    0.58rem,
    0.62vw,
    0.68rem
  );

  line-height: 1.55;
}

.cards a {
  margin-top: auto;

  padding-top: 0.8rem;

  display: flex;

  justify-content: space-between;

  border-top:
    1px solid
    #eeeeee;

  color: #111111;

  font-size: 0.52rem;

  letter-spacing: 0.08em;

  text-decoration: none;

  text-transform: uppercase;
}

@media (max-width: 900px) {
  .head {
    grid-template-columns: 1fr;
  }

  .cards {
    grid-template-columns:
      repeat(
        2,
        1fr
      );
  }
}

@media (max-width: 520px) {
  .cards {
    grid-template-columns: 1fr;
  }
}
</style>