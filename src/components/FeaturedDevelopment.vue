<template>
  <section class="dev">

    <!-- Background Image -->
    <img
      class="dev-bg"
      :src="thalpeImage"
      alt="Featured luxury apartment development"
    />

    <!-- Dark Gradient -->
    <div class="shade"></div>

    <!-- Content -->
    <div class="copy">

      <p class="kicker">
        FEATURED DEVELOPMENT
      </p>

      <h2 class="title">
        Architecture made<br />
        for a lasting<br />
        impression.
      </h2>

      <p class="description">
        A contemporary residence combining intelligent layouts,
        panoramic views, private amenities and effortless access
        to the city.
      </p>

      <div class="facts">
        <span>3–4 Bedrooms</span>
        <span>2,200–3,600 sq.ft</span>
        <span>Private amenities</span>
      </div>

      <a href="#" class="discover-btn">
        <span>Discover the development</span>
        <span class="arrow">→</span>
      </a>

    </div>

  </section>
</template>


<script setup>
import thalpeImage from "../images/Thalpe.webp";
</script>


<style scoped>
.dev {
  width: 100%;
  height: clamp(100px, 62vh, 940px);
  position: relative;
  overflow: hidden;
  background: #0a0a0a;
  color: #ffffff;
}


/* =========================
   BACKGROUND IMAGE
========================= */

.dev-bg {
  position: absolute;
  inset: 0;

  width: 100%;
  height: 100%;

  object-fit: cover;
  object-position: center;

  transition: transform 1.2s ease;
}

.dev:hover .dev-bg {
  transform: scale(1.025);
}


/* =========================
   DARK OVERLAY
========================= */

.shade {
  position: absolute;
  inset: 0;

  background:
    linear-gradient(
      90deg,
      rgba(0, 0, 0, 0.88) 0%,
      rgba(0, 0, 0, 0.76) 25%,
      rgba(0, 0, 0, 0.46) 53%,
      rgba(0, 0, 0, 0.12) 78%,
      rgba(0, 0, 0, 0.04) 100%
    );

  z-index: 1;
}


/* =========================
   CONTENT
========================= */

.copy {
  position: absolute;

  left: clamp(30px, 5.5vw, 110px);
  top: 50%;

  transform: translateY(-50%);

  width: min(720px, 50vw);

  z-index: 2;
}


/* =========================
   SMALL LABEL
========================= */

.kicker {
  margin: 0 0 clamp(18px, 2vh, 28px);

  font-family: sans-serif;

  font-size: clamp(4px, 0.5vw, 13px);

  font-weight: 400;

  letter-spacing: 0.22em;

  line-height: 1.3;

  color: rgba(255, 255, 255, 0.78);
}


/* =========================
   MAIN HEADING
========================= */

.title {
  margin: 0;

  font-family: sans-serif;

  font-size: clamp(1.5rem, 2.9vw, 4rem);

  font-weight: 200;

  line-height: 1.29;

  letter-spacing: -0.015em;

  color: #ffffff;
}


/* =========================
   DESCRIPTION
========================= */

.description {
  max-width: 610px;

  margin:
    clamp(25px, 3vh, 38px)
    0
    0;

  font-family: sans-serif;

  font-size: clamp(13px, 0.82vw, 16px);

  font-weight: 400;

  line-height: 1.75;

  color: rgba(255, 255, 255, 0.72);
}


/* =========================
   PROPERTY FACTS
========================= */

.facts {
  display: flex;
  align-items: center;
  flex-wrap: wrap;

  gap: clamp(20px, 2.5vw, 42px);

  margin:
    clamp(25px, 3vh, 38px)
    0;
}

.facts span {
  position: relative;

  font-family: sans-serif;

  font-size: clamp(11px, 0.7vw, 14px);

  font-weight: 400;

  color: rgba(255, 255, 255, 0.9);

  white-space: nowrap;
}

.facts span:not(:last-child)::after {
  content: "";

  position: absolute;

  right: calc(clamp(10px, 1.25vw, 21px) * -1);
  top: 50%;

  width: 1px;
  height: 13px;

  transform: translateY(-50%);

  background: rgba(255, 255, 255, 0.25);
}


/* =========================
   BUTTON
========================= */

.discover-btn {
  width: clamp(230px, 20vw, 310px);

  min-height: 64px;

  display: flex;
  align-items: center;
  justify-content: space-between;

  padding:
    0
    clamp(20px, 1.6vw, 30px);

  background: #ffffff;

  color: #111111;

  text-decoration: none;

  text-transform: uppercase;

  font-family: sans-serif;

  font-size: clamp(9px, 0.62vw, 12px);

  font-weight: 400;

  letter-spacing: 0.08em;

  transition:
    background 0.35s ease,
    color 0.35s ease,
    transform 0.35s ease;
}

.discover-btn .arrow {
  font-size: 18px;

  transition: transform 0.35s ease;
}

.discover-btn:hover {
  background: #111111;
  color: #ffffff;

  transform: translateY(-3px);
}

.discover-btn:hover .arrow {
  transform: translateX(5px);
}


/* =========================
   TABLET
========================= */

@media (max-width: 1024px) {

  .dev {
    height: 82vh;
    min-height: 680px;
  }

  .copy {
    width: 65vw;
  }

  .title {
    font-size: clamp(
      3.5rem,
      7vw,
      5.8rem
    );
  }

  .shade {
    background:
      linear-gradient(
        90deg,
        rgba(0, 0, 0, 0.9) 0%,
        rgba(0, 0, 0, 0.68) 55%,
        rgba(0, 0, 0, 0.2) 100%
      );
  }
}


/* =========================
   MOBILE
========================= */

@media (max-width: 767px) {

  .dev {
    height: 82vh;
    min-height: 650px;
  }

  .dev-bg {
    object-position: 60% center;
  }

  .shade {
    background:
      linear-gradient(
        90deg,
        rgba(0, 0, 0, 0.88),
        rgba(0, 0, 0, 0.62)
      );
  }

  .copy {
    left: 6vw;
    right: 6vw;

    width: auto;
  }

  .title {
    font-size: clamp(
      3rem,
      13vw,
      4.8rem
    );

    line-height: 0.95;
  }

  .description {
    max-width: 90%;

    font-size: 13px;
  }

  .facts {
    align-items: flex-start;

    gap: 10px 22px;
  }

  .facts span {
    font-size: 11px;
  }

  .facts span::after {
    display: none;
  }

  .discover-btn {
    width: min(
      100%,
      290px
    );

    min-height: 58px;
  }
}


/* =========================
   SMALL MOBILE
========================= */

@media (max-width: 480px) {

  .dev {
    min-height: 620px;
  }

  .kicker {
    font-size: 9px;
  }

  .title {
    font-size: clamp(
      2.7rem,
      14vw,
      4rem
    );
  }

  .description {
    line-height: 1.6;
  }

  .facts {
    flex-direction: column;
  }
}
</style>