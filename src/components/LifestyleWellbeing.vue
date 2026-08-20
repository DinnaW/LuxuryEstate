<template>
  <section class="design-story">

    <div class="design-shell">

      <!-- =================================
           LEFT IMAGE
      ================================== -->
      <div class="design-visual">

        <div class="image-frame">
          <img
            :src="colomboImage"
            alt="Luxury residential architecture"
          />

          <div class="image-overlay"></div>
        </div>


        <!-- QUOTE CARD -->
        <div class="quote-card">

          <p>
            “Quiet materials, generous light and considered details
            shape the experience of home.”
          </p>

          <span>
            Odiliya Premier Design Studio
          </span>

        </div>

      </div>


      <!-- =================================
           RIGHT CONTENT
      ================================== -->
      <div class="design-content">

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


        <p class="description">
          Carefully balanced materials, natural light and refined proportions
          create residences that feel calm, functional and distinctive.
          Every detail is considered for everyday comfort and long-term relevance.
        </p>


        <!-- DETAILS -->
        <div class="design-points">

          <div class="design-point">
            <span>01</span>

            <div>
              <h3>Natural Light</h3>

              <p>
                Spaces planned to make the most of daylight.
              </p>
            </div>
          </div>


          <div class="design-point">
            <span>02</span>

            <div>
              <h3>Refined Materials</h3>

              <p>
                A considered material palette selected for lasting character.
              </p>
            </div>
          </div>


          <div class="design-point">
            <span>03</span>

            <div>
              <h3>Everyday Comfort</h3>

              <p>
                Thoughtful details shaped around modern residential living.
              </p>
            </div>
          </div>

        </div>


        <!-- CTA -->
        <a href="#" class="design-button">

          <span>
            Read the design 
          </span>

          <span class="arrow">
            →
          </span>

        </a>

      </div>

    </div>

  </section>
</template>


<script setup>
import colomboImage from "../images/new.png";
</script>


<style scoped>

/* =========================================================
   RESET
========================================================= */

.design-story,
.design-story *,
.design-story *::before,
.design-story *::after {
  box-sizing: border-box;
  font-family: sans-serif;
}


/* =========================================================
   SECTION
========================================================= */

.design-story {
  width: 100%;

  background: #101010;

  color: #ffffff;

  padding:
    clamp(4rem, 7vh, 6rem)
    0;

  overflow: hidden;
}


/* =========================================================
   MAIN LAYOUT
========================================================= */

.design-shell {
  width: min(88vw, 1500px);

  margin: 0 auto;

  display: grid;

  /*
    Balanced layout:
    image slightly larger than text
  */
  grid-template-columns:
    1.08fr
    0.92fr;

  align-items: center;

  /*
    MAIN GAP
    reduce/increase this if needed
  */
  column-gap: clamp(10rem, 5vw, 6.5rem);
}


/* =========================================================
   LEFT VISUAL
========================================================= */

.design-visual {
  position: relative;

  width: 100%;

  padding-bottom: 65px;
}


/* =========================================================
   IMAGE FRAME
========================================================= */

.image-frame {
  width: 100%;

  height:
    clamp(
      360px,
      43vh,
      500px
    );

  position: relative;

  overflow: hidden;

  background: #1a1a1a;
}


.image-frame img {
  width: 100%;
  height: 100%;

  display: block;

  object-fit: cover;

  object-position: center;

  transition:
    transform
    0.9s ease;
}


.image-frame:hover img {
  transform: scale(1.02);
}


/* =========================================================
   IMAGE OVERLAY
========================================================= */

.image-overlay {
  position: absolute;

  inset: 0;

  pointer-events: none;

  background:
    linear-gradient(
      180deg,
      rgba(0, 0, 0, 0.02) 55%,
      rgba(0, 0, 0, 0.18) 100%
    );
}


/* =========================================================
   QUOTE CARD
========================================================= */

.quote-card {
  position: absolute;

  /* CENTER CARD */
  left: 50%;
  right: auto;
  bottom: 0;

  transform: translateX(-50%);

  width: min(
    360px,
    52%
  );

  padding:
    clamp(
      1.2rem,
      1.6vw,
      1.6rem
    );

  background: #f0ece5;

  color: #171717;

  box-shadow:
    0 18px 40px
    rgba(0, 0, 0, 0.28);

  z-index: 4;
}


.quote-card p {
  margin: 0;

  color: #181818;

  font-size:
    clamp(16px, 1vw, 18px);

  line-height: 1.6;
}


.quote-card span {
  display: block;

  margin-top: 0.8rem;

  color: #77716b;

  font-family: Georgia, serif;

  font-size:
    clamp(12px, 0.72vw, 14px);
}


/* =========================================================
   RIGHT CONTENT
========================================================= */

.design-content {
  width: 100%;

  max-width: 520px;
}


/* =========================================================
   KICKER
========================================================= */

.kicker {
  margin:
    0
    0
    9px;

  color: #9d7e46;

  font-size:
    clamp(13px, 0.82vw, 15px);

  font-weight: 700;

  letter-spacing: 0.18em;

  line-height: 1.4;

  text-transform: uppercase;
}


/* =========================================================
   TITLE
========================================================= */

.title {
    margin: 0;

  color: #ffffff;

  font-size:
    clamp(48px, 4vw, 68px);

  font-weight: 400;

  line-height: 1.18;

  letter-spacing: -0.035em;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.description {
   margin:
     clamp(1.35rem, 2.2vh, 1.8rem)
     0
     0;

  color:
    rgba(255, 255, 255, 0.35);

   font-size:
    clamp(16px, 1vw, 18px);



  line-height: 1.65;
}


/* =========================================================
   DETAILS LIST
========================================================= */

.design-points {
  margin-top:
    clamp(
      1.7rem,
      2.4vh,
      1.9rem
    );

  border-top:
    1px solid
    rgba(255, 255, 255, 0.12);
}


.design-point {
  display: grid;

  grid-template-columns:
    38px
    1fr;

  gap: 12px;

  padding:
    clamp(
      0.75rem,
      0.95vw,
      0.95rem
    )
    0;

  border-bottom:
    1px solid
    rgba(255, 255, 255, 0.12);
}


.design-point > span {
  padding-top: 2px;

  color:
    rgba(255, 255, 255, 0.35);

  font-size:
    clamp(14px, 0.86vw, 16px);

  font-weight: 600;
}


.design-point h3 {
  margin: 0;

  color: #ffffff;

  font-size:
    clamp(16px, 1vw, 18px);

  font-weight: 500;
}


.design-point p {
  margin:
    0.25rem
    0
    0;

  color:
    rgba(255, 255, 255, 0.4);

  font-size:
    clamp(14px, 0.86vw, 16px);

  line-height: 1.55;
}


/* =========================================================
   BUTTON
========================================================= */

.design-button {
  width:
    clamp(205px, 15vw, 240px);

  min-height: 54px;

  margin-top:
    clamp(
      1.5rem,
      2.5vh,
      2rem
    );

  padding:
    0
    1.1rem;

  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 1rem;

  background: #ffffff;

  color: #111111;

  text-decoration: none;

  text-transform: uppercase;

  border:
    1px solid #ffffff;

  font-size:
    clamp(12px, 0.74vw, 14px);

  font-weight: 600;

  letter-spacing: 0.08em;

  transition:
    background 0.3s ease,
    color 0.3s ease,
    transform 0.3s ease;
}


.design-button:hover {
  background: transparent;

  color: #ffffff;

  transform: translateY(-2px);
}


.arrow {
  font-size: 18px;

  transition:
    transform 0.3s ease;
}


.design-button:hover .arrow {
  transform: translateX(5px);
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 1100px) {

  .design-shell {
    width: 90vw;

    grid-template-columns:
      1fr
      0.9fr;

    column-gap: 3.5rem;
  }


  .image-frame {
    height: 420px;
  }


  .quote-card {
    width: 58%;

    right: 1.5rem;
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 800px) {

  .design-story {
    padding:
      3.5rem
      0;
  }


  .design-shell {
    width: 88vw;

    grid-template-columns: 1fr;

    row-gap: 3.5rem;
  }


  .design-visual {
    padding-bottom: 0;
  }


  .design-content {
    max-width: none;
  }


  .image-frame {
    height:
      clamp(
        350px,
        82vw,
        480px
      );
  }


  .quote-card {
    position: relative;

    right: auto;
    bottom: auto;

    width: 84%;

    margin:
      -2.5rem
      0
      0
      auto;
  }

}


/* =========================================================
   SMALL MOBILE
========================================================= */

@media (max-width: 520px) {

  .design-story {
    padding:
      3rem
      0;
  }


  .design-shell {
    width: 90vw;

    row-gap: 2.8rem;
  }


  .image-frame {
    height: 330px;
  }


  .quote-card {
    width: 90%;

    margin-top: -2rem;

    padding: 1.1rem;
  }


  .title {
    font-size:
      clamp(
        40px,
        11vw,
        52px
      );
  }


  .design-point {
    grid-template-columns:
      30px
      1fr;
  }


  .design-button {
    width: 100%;

    max-width: 230px;
  }

}

</style>