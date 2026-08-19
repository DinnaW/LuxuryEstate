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
    9px;

  color: #9d7e46;

  font-size:
    clamp(
      10px,
      0.68vw,
      12px
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
      2.3rem,
      3.35vw,
      4.35rem
    );

  font-weight: 400;

  line-height: 1.18;

  letter-spacing: -0.035em;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.story-description {
    margin: 0;

  color:
    rgba(0, 0, 0, 0.52);

   font-size:
    clamp(
      13px,
      0.82vw,
      15px
    );



  line-height: 1.65;
}


/* =========================================================
   BUTTON
========================================================= */

.story-button {
  width: fit-content;

  min-width:
    clamp(
      175px,
      14vw,
      215px
    );

  height:
    clamp(
      42px,
      3.5vw,
      50px
    );

  margin-top:
    clamp(
      1.7rem,
      3vh,
      2.3rem
    );

  padding:
    0
    clamp(
      1rem,
      1.3vw,
      1.4rem
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
      0.65rem,
      0.5vw,
      0.57rem
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
  font-size: 0.85rem;

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
      115px,
      9vw,
      145px
    );

  padding:
    clamp(
      1.2rem,
      1.7vw,
      1.7rem
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
      13px,
      0.82vw,
      15px
    );

  font-weight: 400;

  line-height: 1.55;
}


.story-quote span {
  display: block;

  margin-top:
    clamp(
      0.8rem,
      1.2vh,
      1rem
    );

  color: #8e8a84;

  font-family: sans-serif;

  font-size:
    clamp(
      0.8rem,
      0.5vw,
      0.57rem
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


  .story-title {
    font-size:
      clamp(
        2.4rem,
        10vw,
        4rem
      );
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
        2.1rem,
        11vw,
        3rem
      );

    line-height: 1.15;
  }


  .story-description {
    font-size: 0.72rem;

    line-height: 1.75;
  }


  .story-image-wrap {
    height: 340px;
  }


  .story-quote {
    width: 92%;

    margin-top: -2.2rem;

    padding: 1.2rem;
  }


  .story-button {
    min-width: 190px;

    height: 46px;
  }

}

</style>