<template>
  <section class="featured-banner">

    <!-- LEFT CONTENT -->
    <div class="banner-content">

      <div class="banner-top">

        <p class="kicker">
          FEATURED DEVELOPMENT
        </p>
        
      </div>


      <h2 class="title">
        Architecture
        <br />
        with a lasting
        <br />
        identity.
      </h2>


      <p class="description">
        A contemporary residence shaped around intelligent layouts,
        natural light and refined private amenities. Designed for
        calm, connected and enduring modern living.
      </p>


      <!-- DETAILS -->
      <div class="property-details">

        <div class="detail-item">
          <span>Bedrooms</span>
          <strong>3–4</strong>
        </div>


        <div class="detail-item">
          <span>Residence Size</span>
          <strong>2,200–3,600</strong>
          <small>sq.ft</small>
        </div>


        <div class="detail-item">
          <span>Location</span>
          <strong>Thalpe</strong>
          <small>Galle</small>
        </div>

      </div>


      <!-- BOTTOM -->
      <div class="banner-bottom">

        <a href="#" class="discover-btn">

          <span>
            Discover Development
          </span>

          <span class="arrow">
            →
          </span>

        </a>


        <div class="starting-price">

          <span>
            Starting From
          </span>

          <div>
            <small>LKR</small>
            <strong>84M</strong>
          </div>

        </div>

      </div>

    </div>


    <!-- RIGHT IMAGE -->
    <div class="banner-image">

      <img
        :src="thalpeImage"
        alt="Featured luxury development"
      />

      <div class="image-overlay"></div>


      <div class="image-top">

        <span class="image-number">
          01
        </span>

        <span class="image-location">
          THALPE · GALLE
        </span>

      </div>


      <div class="image-caption">

        <span>
          COASTAL LIVING
        </span>

        <p>
          Contemporary architecture shaped around privacy,
          natural light and connection to place.
        </p>

      </div>

    </div>

  </section>
</template>


<script setup>
import thalpeImage from "../images/Thalpe.webp";
</script>


<style scoped>

/* =========================================================
   RESET
========================================================= */

.featured-banner,
.featured-banner *,
.featured-banner *::before,
.featured-banner *::after {
  box-sizing: border-box;
  font-family: sans-serif;
}


/* =========================================================
   FULL WIDTH BANNER
========================================================= */

.featured-banner {
  width: 100%;

  min-height:
    clamp(
      470px,
      56vh,
      620px
    );

  display: grid;

  grid-template-columns:
    0.9fr
    1.1fr;

  background: #111111;

  overflow: hidden;

  color: #ffffff;
}


/* =========================================================
   LEFT CONTENT
========================================================= */

.banner-content {
  min-width: 0;

  display: flex;

  flex-direction: column;

  justify-content: center;

  padding:
    clamp(
      2.5rem,
      4.5vw,
      5.5rem
    )
    clamp(
      2rem,
      5vw,
      6.5rem
    );

  background: #111111;
}


/* =========================================================
   TOP
========================================================= */

.banner-top {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 1rem;

  margin-bottom:
    clamp(
      1rem,
      1.8vh,
      1.5rem
    );
}


.kicker {
  margin: 0;

  color: #b99c68;

  font-size:
    clamp(
      0.45rem,
      0.5vw,
      0.58rem
    );

  font-weight: 650;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}


.project-status {
  padding:
    0.42rem
    0.68rem;

  border:
    1px solid
    rgba(255, 255, 255, 0.14);

  color:
    rgba(255, 255, 255, 0.55);

  font-size:
    clamp(
      0.36rem,
      0.4vw,
      0.46rem
    );

  font-weight: 600;

  letter-spacing: 0.09em;

  white-space: nowrap;
}


/* =========================================================
   TITLE
========================================================= */

.title {
  max-width: 620px;

  margin: 0;

  color: #f6f5f2;

  font-size:
    clamp(
      2rem,
      3vw,
      4rem
    );

  font-weight: 300;

  line-height: 1.12;

  letter-spacing: -0.045em;
}


/* =========================================================
   DESCRIPTION
========================================================= */

.description {
  max-width: 540px;

  margin:
    clamp(
      1.2rem,
      2.1vh,
      1.7rem
    )
    0
    0;

  color:
    rgba(255, 255, 255, 0.53);

  font-size:
    clamp(
      0.65rem,
      0.72vw,
      0.82rem
    );

  line-height: 1.8;
}


/* =========================================================
   DETAILS
========================================================= */

.property-details {
  display: grid;

  grid-template-columns:
    repeat(
      3,
      minmax(0, 1fr)
    );

  margin-top:
    clamp(
      1.5rem,
      2.6vh,
      2.2rem
    );

  border-top:
    1px solid
    rgba(255, 255, 255, 0.12);

  border-bottom:
    1px solid
    rgba(255, 255, 255, 0.12);
}


.detail-item {
  min-width: 0;

  padding:
    clamp(
      1rem,
      1.4vw,
      1.25rem
    );

  border-right:
    1px solid
    rgba(255, 255, 255, 0.11);
}


.detail-item:first-child {
  padding-left: 0;
}


.detail-item:last-child {
  border-right: none;
}


.detail-item > span {
  display: block;

  margin-bottom: 0.4rem;

  color:
    rgba(255, 255, 255, 0.35);

  font-size:
    clamp(
      0.37rem,
      0.42vw,
      0.48rem
    );

  font-weight: 650;

  letter-spacing: 0.1em;

  text-transform: uppercase;
}


.detail-item strong {
  display: block;

  color: #ffffff;

  font-size:
    clamp(
      1rem,
      1.25vw,
      1.5rem
    );

  font-weight: 400;
}


.detail-item small {
  display: block;

  margin-top: 0.2rem;

  color:
    rgba(255, 255, 255, 0.38);

  font-size:
    clamp(
      0.37rem,
      0.41vw,
      0.47rem
    );

  text-transform: uppercase;

  letter-spacing: 0.06em;
}


/* =========================================================
   BOTTOM
========================================================= */

.banner-bottom {
  display: flex;

  align-items: flex-end;

  justify-content: space-between;

  gap: 2rem;

  margin-top:
    clamp(
      1.5rem,
      2.6vh,
      2rem
    );
}


/* =========================================================
   BUTTON
========================================================= */

.discover-btn {
  width:
    clamp(
      210px,
      17vw,
      270px
    );

  min-height: 52px;

  padding:
    0
    1.2rem;

  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 1rem;

  background: #f4f2ee;

  color: #111111;

  border:
    1px solid #f4f2ee;

  text-decoration: none;

  text-transform: uppercase;

  font-size:
    clamp(
      0.43rem,
      0.48vw,
      0.55rem
    );

  font-weight: 650;

  letter-spacing: 0.08em;

  transition:
    background 0.3s ease,
    color 0.3s ease,
    transform 0.3s ease;
}


.discover-btn:hover {
  background: transparent;

  color: #ffffff;

  transform: translateY(-2px);
}


.arrow {
  font-size: 1rem;

  transition:
    transform 0.3s ease;
}


.discover-btn:hover
.arrow {
  transform: translateX(5px);
}


/* =========================================================
   PRICE
========================================================= */

.starting-price {
  text-align: right;
}


.starting-price > span {
  display: block;

  margin-bottom: 0.3rem;

  color:
    rgba(255, 255, 255, 0.35);

  font-size:
    clamp(
      0.36rem,
      0.4vw,
      0.46rem
    );

  font-weight: 650;

  letter-spacing: 0.1em;

  text-transform: uppercase;
}


.starting-price > div {
  display: flex;

  align-items: baseline;

  justify-content: flex-end;

  gap: 0.35rem;
}


.starting-price small {
  color: #b99c68;

  font-size:
    clamp(
      0.46rem,
      0.52vw,
      0.6rem
    );

  font-weight: 700;
}


.starting-price strong {
  color: #ffffff;

  font-size:
    clamp(
      1.6rem,
      2.15vw,
      2.7rem
    );

  font-weight: 500;

  line-height: 1;

  letter-spacing: -0.04em;
}


/* =========================================================
   RIGHT IMAGE
========================================================= */

.banner-image {
  position: relative;

  min-width: 0;

  min-height: 100%;

  overflow: hidden;

  background: #222222;
}


.banner-image > img {
  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

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


.featured-banner:hover
.banner-image > img {
  transform: scale(1.025);
}


/* =========================================================
   OVERLAY
========================================================= */

.image-overlay {
  position: absolute;

  inset: 0;

  z-index: 1;

  background:
    linear-gradient(
      180deg,
      rgba(0, 0, 0, 0.13)
      0%,
      rgba(0, 0, 0, 0.01)
      50%,
      rgba(0, 0, 0, 0.52)
      100%
    );

  pointer-events: none;
}


/* =========================================================
   IMAGE TOP
========================================================= */

.image-top {
  position: absolute;

  z-index: 3;

  top:
    clamp(
      1.4rem,
      2vw,
      2rem
    );

  left:
    clamp(
      1.5rem,
      2.4vw,
      2.8rem
    );

  right:
    clamp(
      1.5rem,
      2.4vw,
      2.8rem
    );

  display: flex;

  align-items: center;

  justify-content: space-between;
}


.image-number {
  width: 38px;
  height: 38px;

  display: grid;

  place-items: center;

  border:
    1px solid
    rgba(255, 255, 255, 0.65);

  color: #ffffff;

  font-size: 0.55rem;
}


.image-location {
  color:
    rgba(255, 255, 255, 0.75);

  font-size:
    clamp(
      0.4rem,
      0.45vw,
      0.52rem
    );

  font-weight: 650;

  letter-spacing: 0.16em;
}


/* =========================================================
   CAPTION
========================================================= */

.image-caption {
  position: absolute;

  z-index: 3;

  left:
    clamp(
      1.5rem,
      2.4vw,
      2.8rem
    );

  bottom:
    clamp(
      1.5rem,
      2.4vw,
      2.8rem
    );

  width:
    min(
      360px,
      60%
    );
}


.image-caption > span {
  display: block;

  margin-bottom: 0.45rem;

  color: #d2b77f;

  font-size:
    clamp(
      0.4rem,
      0.45vw,
      0.52rem
    );

  font-weight: 700;

  letter-spacing: 0.17em;
}


.image-caption p {
  margin: 0;

  color:
    rgba(255, 255, 255, 0.79);

  font-size:
    clamp(
      0.61rem,
      0.67vw,
      0.77rem
    );

  line-height: 1.6;
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 1000px) {

  .featured-banner {
    grid-template-columns:
      0.95fr
      1.05fr;
  }


  .banner-content {
    padding:
      2.5rem;
  }


  .property-details {
    grid-template-columns:
      1fr
      1fr;
  }


  .detail-item:nth-child(2) {
    border-right: none;
  }


  .detail-item:last-child {
    grid-column: 1 / -1;

    border-top:
      1px solid
      rgba(255, 255, 255, 0.11);
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 800px) {

  .featured-banner {
    grid-template-columns: 1fr;

    min-height: 0;
  }


  .banner-image {
    order: 1;

    min-height:
      clamp(
        360px,
        85vw,
        500px
      );
  }


  .banner-content {
    order: 2;

    padding:
      2.2rem
      6vw
      2.6rem;
  }


  .banner-bottom {
    flex-direction: column;

    align-items: flex-start;
  }


  .starting-price {
    text-align: left;
  }


  .starting-price > div {
    justify-content: flex-start;
  }

}


/* =========================================================
   SMALL MOBILE
========================================================= */

@media (max-width: 520px) {

  .banner-top {
    flex-direction: column;

    align-items: flex-start;
  }


  .title {
    font-size:
      clamp(
        2rem,
        10vw,
        3rem
      );
  }


  .property-details {
    grid-template-columns: 1fr;
  }


  .detail-item {
    padding:
      0.9rem
      0;

    border-right: none;

    border-bottom:
      1px solid
      rgba(255, 255, 255, 0.11);
  }


  .detail-item:last-child {
    grid-column: auto;

    border-top: none;

    border-bottom: none;
  }


  .discover-btn {
    width: 100%;

    max-width: 280px;
  }


  .image-caption {
    width: 78%;
  }

}

</style>