<template>
  <section class="story">

    <div class="shell grid">

      <div class="copy">

        <p class="kicker">
          AWARD-WINNING INTERIORS
        </p>

        <h2 class="title">
          Interior design
          <br />
          with a lasting
          <br />
          identity.
        </h2>

        <p>
          Carefully balanced materials, natural light and refined proportions
          create residences that feel calm, functional and distinctive.
          Every detail is considered for everyday comfort and long-term relevance.
        </p>

        <a href="#">
          Read the design story →
        </a>

      </div>


      <div class="image">

        <img
          src="/Users/naduniameesha/LuxuryEstate/src/images/Colombo.jpeg"
          alt="Luxury apartment interior"
        />

        <div class="quote">
          <p>
            “Quiet materials, generous light and considered details shape
            the experience of home.”
          </p>

          <span>
            Luxury Estate Design Studio
          </span>
        </div>

      </div>

    </div>

  </section>
</template>

<style scoped>
.story {
  width: 100%;

  padding:
    clamp(5rem, 9vh, 8rem)
    0;

  background: #ffffff;
  color: #111111;
}

.shell {
  width: min(
    91vw,
    1550px
  );

  margin: 0 auto;
}

.grid {
  display: grid;

  grid-template-columns:
    0.85fr
    1.15fr;

  gap:
    clamp(
      3rem,
      7vw,
      8rem
    );

  align-items: center;
}

.kicker {
  margin: 0;

  font-family:
    sans-serif;

  font-size: clamp(
    0.52rem,
    0.58vw,
    0.68rem
  );

  letter-spacing: 0.18em;

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
    sans-serif;

  font-size:
    clamp(
      1.7rem,
      3.1vw,
      4.8rem
    );

  font-weight: 400;

  line-height: 1.26;

  letter-spacing: 0.01em;
}
.copy > p:last-of-type {
  max-width: 560px;

  color: #777777;

  font-family:
    sans-serif;

  font-size: clamp(
    0.7rem,
    0.78vw,
    0.88rem
  );

  line-height: 1.85;
}

.copy a {
  display: inline-block;

  margin-top:
    clamp(
      1.2rem,
      2vh,
      1.5rem
    );

  padding:
    0.9rem
    1.2rem;

  background: #111111;
  color: #ffffff;

  font-family:
    sans-serif;

  font-size: clamp(
    0.52rem,
    0.58vw,
    0.64rem
  );

  letter-spacing: 0.08em;

  text-decoration: none;
  text-transform: uppercase;

  transition:
    background 0.3s ease,
    color 0.3s ease;
}

.copy a:hover {
  background: #eeeeee;
  color: #111111;
}

.image {
  min-height:
    clamp(
      430px,
      55vh,
      640px
    );

  position: relative;
}

.image > img {
  width: 100%;
  height: 100%;

  object-fit: cover;
}

.quote {
  position: absolute;

  left: -7%;
  bottom: -6%;

  width: min(
    420px,
    72%
  );

  padding:
    clamp(
      1.1rem,
      2vw,
      1.6rem
    );

  background: #f4f0e9;

  border:
    1px solid
    #eeeeee;

  box-shadow:
    0 16px 35px
    rgba(0, 0, 0, 0.08);
}

.quote p {
  margin:
    0
    0
    0.8rem;

 font-family:
    sans-serif;

  font-size: clamp(
    0.78rem,
    0.86vw,
    0.95rem
  );

  line-height: 1.6;
}

.quote span {
  color: #777777;

  font-size: clamp(
    0.54rem,
    0.58vw,
    0.64rem
  );
}

@media (max-width: 800px) {
  .grid {
    grid-template-columns: 1fr;
  }

  .quote {
    left: 4%;
    bottom: 4%;
  }
}
</style>