<template>
  <section class="story-section">

    <div class="story-container">

      <!-- =========================
           LEFT CONTENT
      ========================== -->
      <div class="story-content">

        <p class="story-kicker">
          AWARD-WINNING INTERIORS
        </p>

        <h2 class="story-title">
          Interior design
          <br />
          with a lasting
          <br />
          identity.
        </h2>

        <p class="story-description">
          Carefully balanced materials, natural light and refined proportions
          create residences that feel calm, functional and distinctive.
          Every detail is considered for everyday comfort and
          long-term relevance.
        </p>

        <a href="#" class="story-button">
          <span>Read the design story</span>
          <span class="button-arrow">→</span>
        </a>

      </div>


      <!-- =========================
           RIGHT IMAGE
      ========================== -->
      <div class="story-visual">

        <div class="story-image-wrap">

         <img
  :src="interiorImage"
  alt="Luxury residence"
  class="story-image"
/>

        </div>


        <!-- OVERLAPPING QUOTE -->
        <div class="story-quote">

          <p>
            “Quiet materials, generous light and considered
            details shape the experience of home.”
          </p>

          <span>
            Luxury Estate Design Studio
          </span>

        </div>

      </div>

    </div>

  </section>
</template>


<script setup>
import interiorImage from "../images/5.png";
</script>


<style scoped>

/* =========================================================
   RESET
========================================================= */

.story-section,
.story-section *,
.story-section *::before,
.story-section *::after {
  box-sizing: border-box;
  font-family: sans-serif;
}


/* =========================================================
   MAIN SECTION
========================================================= */

.story-section {
  width: 100%;

  padding:
    clamp(4.5rem, 8vh, 7rem)
    0
    clamp(5.5rem, 10vh, 8rem);

  background: #ffffff;

  color: #111111;

  overflow: hidden;
}


/* =========================================================
   CONTAINER
========================================================= */

.story-container {
  width: min(82vw, 1460px);

  margin: 0 auto;

  display: grid;

  grid-template-columns:
    0.82fr
    1.18fr;

  align-items: center;

  gap:
    clamp(
      4rem,
      8vw,
      9rem
    );
}


/* =========================================================
   LEFT CONTENT
========================================================= */

.story-content {
  width: 100%;

  max-width: 570px;
}


/* =========================================================
   KICKER
========================================================= */

.story-kicker {
  margin:
    0
    0
    12px;

  color: #9d7e46;

  font-size:
    clamp(
      13px,
      0.82vw,
      15px
    );

  font-weight: 700;

  letter-spacing: 0.18em;

  line-height: 1.4;

  text-transform: uppercase;
}

/* =========================================================
   TITLE
========================================================= */

.story-title {
  margin: 0;

  color: #111111;

  font-size:
    clamp(
      48px,
      4vw,
      68px
    );

  font-weight: 400;

  line-height: 1.12;

  letter-spacing: -0.035em;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.story-description {
  margin:
    clamp(1.35rem, 2.2vh, 1.8rem)
    0
    0;

  color:
    rgba(0, 0, 0, 0.52);

  font-size:
    clamp(
      16px,
      1.02vw,
      18px
    );

  line-height: 1.7;
}


/* =========================================================
   BUTTON
========================================================= */

.story-button {
  width: fit-content;

  min-width:
    clamp(
      205px,
      15vw,
      240px
    );

  height:
    clamp(
      48px,
      3.8vw,
      56px
    );

  margin-top:
    clamp(
      1.9rem,
      3vh,
      2.5rem
    );

  padding:
    0
    clamp(
      1.15rem,
      1.4vw,
      1.6rem
    );

  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 1rem;

  background: #111111;

  color: #ffffff;

  text-decoration: none;

  text-transform: uppercase;

  font-size:
    clamp(
      12px,
      0.74vw,
      14px
    );

  font-weight: 600;

  letter-spacing: 0.07em;

  transition:
    background 0.3s ease,
    transform 0.3s ease;
}


.story-button:hover {
  background: #343434;

  transform: translateY(-2px);
}


.button-arrow {
  font-size: 18px;

  transition:
    transform 0.3s ease;
}


.story-button:hover .button-arrow {
  transform: translateX(4px);
}


/* =========================================================
   RIGHT VISUAL
========================================================= */

.story-visual {
  width: 100%;

  position: relative;

  padding-bottom:
    clamp(
      3rem,
      5vw,
      4.5rem
    );
}


/* =========================================================
   IMAGE
========================================================= */

.story-image-wrap {
  width: 100%;

  height:
    clamp(
      380px,
      47vh,
      540px
    );

  position: relative;

  overflow: hidden;

  background: #eeeeee;
}


.story-image {
  width: 100%;
  height: 100%;

  display: block;

  object-fit: cover;

  object-position: center;

  transition:
    transform
    1s
    cubic-bezier(
      0.22,
      1,
      0.36,
      1
    );
}


.story-image-wrap:hover .story-image {
  transform: scale(1.02);
}


/* =========================================================
   QUOTE CARD
========================================================= */

.story-quote {
  position: absolute;

  left:
    clamp(
      -3.5rem,
      -3vw,
      -1.5rem
    );

  bottom: 0;

  width:
    min(
      390px,
      55%
    );

  min-height:
    clamp(
      125px,
      10vw,
      155px
    );

  padding:
    clamp(
      1.35rem,
      1.8vw,
      1.9rem
    );

  display: flex;

  flex-direction: column;

  justify-content: center;

  background: #f2eee8;

  border:
    1px solid
    rgba(0, 0, 0, 0.025);

  box-shadow:
    0
    20px
    45px
    rgba(0, 0, 0, 0.07);

  z-index: 3;
}


.story-quote p {
  max-width: 330px;

  margin: 0;

  color: #181818;

  font-size:
    clamp(
      16px,
      1vw,
      18px
    );

  font-weight: 400;

  line-height: 1.55;
}


.story-quote span {
  display: block;

  margin-top:
    clamp(
      0.9rem,
      1.2vh,
      1.1rem
    );

  color: #8e8a84;

  font-family: sans-serif;

  font-size:
    clamp(
      12px,
      0.72vw,
      14px
    );
}


/* =========================================================
   LARGE DESKTOP
========================================================= */

@media (min-width: 1700px) {

  .story-container {
    width: min(82vw, 1500px);
  }

}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 1050px) {

  .story-container {
    width: 88vw;

    grid-template-columns:
      0.9fr
      1.1fr;

    gap: 4rem;
  }


  .story-image-wrap {
    height: 430px;
  }


  .story-quote {
    left: -2rem;

    width: 65%;
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 800px) {

  .story-section {
    padding:
      4rem
      0;
  }


  .story-container {
    width: 88vw;

    grid-template-columns: 1fr;

    gap: 3rem;
  }


  .story-content {
    max-width: 600px;
  }


  .story-kicker {
    font-size: 12px;
  }


  .story-title {
    font-size:
      clamp(
        44px,
        10vw,
        60px
      );
  }


  .story-description {
    font-size: 16px;

    line-height: 1.7;
  }


  .story-visual {
    padding-bottom: 0;
  }


  .story-image-wrap {
    height:
      clamp(
        360px,
        75vw,
        500px
      );
  }


  .story-quote {
    position: relative;

    left: auto;

    bottom: auto;

    width: 86%;

    margin:
      -3rem
      0
      0
      auto;
  }


  .story-quote p {
    font-size: 15px;
  }


  .story-quote span {
    font-size: 12px;
  }

}


/* =========================================================
   SMALL MOBILE
========================================================= */

@media (max-width: 520px) {

  .story-section {
    padding:
      3.5rem
      0;
  }


  .story-container {
    width: 90vw;

    gap: 2.5rem;
  }


  .story-title {
    font-size:
      clamp(
        40px,
        11vw,
        52px
      );

    line-height: 1.12;
  }


  .story-description {
    font-size: 15px;

    line-height: 1.72;
  }


  .story-image-wrap {
    height: 340px;
  }


  .story-quote {
    width: 92%;

    margin-top: -2.2rem;

    padding: 1.3rem;
  }


  .story-button {
    min-width: 215px;

    height: 50px;

    font-size: 11px;
  }

}

</style>