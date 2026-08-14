<template>
  <footer class="site-footer">

    <div class="footer-shell">

      <!-- =================================================
           SEO / POPULAR SEARCHES
      ================================================== -->
      <section class="seo-section">

        <div class="seo-head">

          <p class="kicker">
            DISCOVER MORE
          </p>

          <h2>
            Popular Searches
          </h2>

          <p class="seo-intro">
            Explore premium residences, investment opportunities
            and desirable locations across Sri Lanka.
          </p>

        </div>


        <div class="seo-grid">

          <!-- APARTMENTS -->
          <div class="seo-column">

            <h3>
              Apartments
            </h3>

            <nav aria-label="Apartment searches">
              <a href="#">
                Luxury apartments in Colombo
              </a>

              <a href="#">
                Apartments in Colombo 03
              </a>

              <a href="#">
                Apartments in Colombo 07
              </a>

              <a href="#">
                Ocean-view apartments
              </a>

              <a href="#">
                Ready residences
              </a>
            </nav>

            <a href="#" class="view-more">
              View more
              <span>→</span>
            </a>

          </div>


          <!-- INVESTMENT -->
          <div class="seo-column">

            <h3>
              Investment
            </h3>

            <nav aria-label="Investment searches">
              <a href="#">
                High-yield residences
              </a>

              <a href="#">
                Rental-ready apartments
              </a>

              <a href="#">
                Long-term investment homes
              </a>

              <a href="#">
                New launch opportunities
              </a>

              <a href="#">
                Prime-location property
              </a>
            </nav>

            <a href="#" class="view-more">
              View more
              <span>→</span>
            </a>

          </div>


          <!-- LOCATIONS -->
          <div class="seo-column">

            <h3>
              Locations
            </h3>

            <nav aria-label="Location searches">
              <a href="#">
                Colombo residences
              </a>

              <a href="#">
                Colombo 03 residences
              </a>

              <a href="#">
                Colombo 07 residences
              </a>

              <a href="#">
                Galle residences
              </a>

              <a href="#">
                Thalpe residences
              </a>
            </nav>

            <a href="#" class="view-more">
              View more
              <span>→</span>
            </a>

          </div>


          <!-- LIFESTYLE -->
          <div class="seo-column">

            <h3>
              Lifestyle
            </h3>

            <nav aria-label="Lifestyle searches">
              <a href="#">
                Ocean-view living
              </a>

              <a href="#">
                City-centre living
              </a>

              <a href="#">
                Private amenity residences
              </a>

              <a href="#">
                Family apartments
              </a>

              <a href="#">
                Penthouse living
              </a>
            </nav>

            <a href="#" class="view-more">
              View more
              <span>→</span>
            </a>

          </div>

        </div>

      </section>


      <!-- =================================================
           MAIN FOOTER
      ================================================== -->
      <section class="footer-main">

        <!-- BRAND -->
        <div class="footer-brand">

          <a href="#" class="brand">
            LUXURY ESTATE
          </a>

          <p>
            Curating distinctive residences, premium addresses
            and considered property opportunities across Sri Lanka.
          </p>

        </div>


        <!-- COMPANY -->
        <div class="footer-column">

          <h4>
            Company
          </h4>

          <a href="#">
            About Us
          </a>

          <a href="#">
            Our Projects
          </a>

          <a href="#">
            Apartments
          </a>

          <a href="#">
            Contact
          </a>

        </div>


        <!-- PROPERTY -->
        <div class="footer-column">

          <h4>
            Property
          </h4>

          <a href="#">
            Featured Residences
          </a>

          <a href="#">
            Hot Deals
          </a>

          <a href="#">
            Trending Properties
          </a>

          <a href="#">
            Area Guide
          </a>

        </div>


        <!-- CONTACT -->
        <div class="footer-column footer-contact">

          <h4>
            Enquiries
          </h4>

          <a href="tel:+94112345678">
            +94 11 234 5678
          </a>

          <a href="mailto:hello@luxuryestate.lk">
            hello@luxuryestate.lk
          </a>

          <p>
            Colombo, Sri Lanka
          </p>

        </div>

      </section>


      <!-- =================================================
           BOTTOM BAR
      ================================================== -->
      <div class="footer-bottom">

        <p>
          © {{ year }} Luxury Estate. All rights reserved.
        </p>


        <div class="legal-links">

          <a href="#">
            Privacy
          </a>

          <a href="#">
            Terms
          </a>

          <a href="#">
            Cookies
          </a>

        </div>

      </div>

    </div>

  </footer>
</template>


<script setup>
const year = new Date().getFullYear();
</script>


<style scoped>

/* =========================================================
   GLOBAL
========================================================= */

.site-footer,
.site-footer *,
.site-footer *::before,
.site-footer *::after {
  box-sizing: border-box;
  font-family: sans-serif;
}


/* =========================================================
   FOOTER
========================================================= */

.site-footer {
  width: 100%;

  background: #f4f1eb;

  color: #111111;
}


.footer-shell {
  width: min(91vw, 1550px);

  margin: 0 auto;
}


/* =========================================================
   SEO SECTION
========================================================= */

.seo-section {
  padding:
    clamp(2.8rem, 5vh, 4rem)
    0
    clamp(2.5rem, 4vh, 3.5rem);

  border-bottom:
    1px solid #dad5cd;
}


/* SMALLER HEADER GAP */
.seo-head {
  text-align: center;

  max-width: 650px;

  margin:
    0 auto
    clamp(1.6rem, 3vh, 2.3rem);
}


.kicker {
  margin: 0;

  color: #9b7b42;

  font-size:
    clamp(
      0.48rem,
      0.53vw,
      0.6rem
    );

  font-weight: 700;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}


.seo-head h2 {
  margin:
    0.55rem
    0
    0;

  font-size:
    clamp(
      2rem,
      2.8vw,
      3.5rem
    );

  font-weight: 400;

  line-height: 1;

  letter-spacing: -0.04em;
}


.seo-intro {
  max-width: 520px;

  margin:
    0.8rem
    auto
    0;

  color: #817a72;

  font-size:
    clamp(
      0.66rem,
      0.72vw,
      0.8rem
    );

  line-height: 1.65;
}


/* =========================================================
   SEO GRID
========================================================= */

.seo-grid {
  display: grid;

  grid-template-columns:
    repeat(
      4,
      minmax(0, 1fr)
    );

  gap:
    clamp(
      2rem,
      4vw,
      5rem
    );
}


.seo-column h3 {
  margin:
    0
    0
    0.8rem;

  padding-bottom:
    0.7rem;

  border-bottom:
    1px solid #ccc7bf;

  color: #5b5651;

  font-size:
    clamp(
      1rem,
      1.15vw,
      1.35rem
    );

  font-weight: 500;

  letter-spacing: -0.02em;
}


.seo-column nav {
  display: flex;

  flex-direction: column;

  gap: 0.6rem;
}


.seo-column nav a {
  width: fit-content;

  color: #23201d;

  font-size:
    clamp(
      0.6rem,
      0.66vw,
      0.74rem
    );

  font-weight: 400;

  line-height: 1.35;

  text-decoration: none;

  transition:
    color 0.25s ease,
    transform 0.25s ease;
}


.seo-column nav a:hover {
  color: #9b7b42;

  transform: translateX(3px);
}


.view-more {
  width: fit-content;

  display: inline-flex;

  align-items: center;

  gap: 0.55rem;

  margin-top: 1rem;

  padding-bottom: 0.2rem;

  border-bottom:
    1px solid transparent;

  color: #111111;

  font-size:
    clamp(
      0.46rem,
      0.5vw,
      0.56rem
    );

  font-weight: 700;

  letter-spacing: 0.08em;

  text-decoration: none;

  text-transform: uppercase;

  transition:
    border-color 0.25s ease;
}


.view-more:hover {
  border-color: #111111;
}


/* =========================================================
   MAIN FOOTER
========================================================= */

.footer-main {
  display: grid;

  grid-template-columns:
    1.7fr
    0.75fr
    0.9fr
    1fr;

  gap:
    clamp(
      2rem,
      5vw,
      6rem
    );

  padding:
    clamp(3rem, 5vh, 4.5rem)
    0;
}


/* =========================================================
   BRAND
========================================================= */

.brand {
  display: inline-flex;

  padding:
    0.4rem
    0.8rem;

  border:
    1px solid #111111;

  border-radius: 3px;

  color: #111111;

  font-size:
    clamp(
      1rem,
      1.35vw,
      1.5rem
    );

  font-weight: 500;

  letter-spacing: 0.04em;

  text-decoration: none;
}


.footer-brand p {
  max-width: 390px;

  margin:
    1rem
    0
    0;

  color: #7b756e;

  font-size:
    clamp(
      0.62rem,
      0.68vw,
      0.76rem
    );

  line-height: 1.65;
}


/* =========================================================
   FOOTER COLUMNS
========================================================= */

.footer-column {
  display: flex;

  flex-direction: column;

  align-items: flex-start;

  gap: 0.65rem;
}


.footer-column h4 {
  margin:
    0
    0
    0.35rem;

  color: #928d86;

  font-size:
    0.52rem;

  font-weight: 700;

  letter-spacing: 0.14em;

  text-transform: uppercase;
}


.footer-column > a {
  color: #201e1b;

  font-size:
    clamp(
      0.61rem,
      0.66vw,
      0.74rem
    );

  font-weight: 500;

  text-decoration: none;

  transition:
    color 0.25s ease,
    transform 0.25s ease;
}


.footer-column > a:hover {
  color: #9b7b42;

  transform: translateX(2px);
}


.footer-contact p {
  margin: 0;

  color: #827c75;

  font-size:
    clamp(
      0.6rem,
      0.64vw,
      0.71rem
    );
}


/* =========================================================
   FOOTER BOTTOM
========================================================= */

.footer-bottom {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 2rem;

  padding:
    0.9rem
    0
    1rem;

  border-top:
    1px solid #dad5cd;
}


.footer-bottom p {
  margin: 0;

  color: #908a83;

  font-size:
    clamp(
      0.5rem,
      0.54vw,
      0.6rem
    );
}


.legal-links {
  display: flex;

  align-items: center;

  flex-wrap: wrap;

  gap:
    clamp(
      0.8rem,
      1.5vw,
      1.5rem
    );
}


.legal-links a {
  color: #777169;

  font-size:
    clamp(
      0.5rem,
      0.54vw,
      0.6rem
    );

  text-decoration: none;
}


.legal-links a:hover {
  color: #111111;
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 950px) {

  .seo-grid {
    grid-template-columns:
      repeat(
        2,
        minmax(0, 1fr)
      );
  }


  .footer-main {
  display: grid;

  grid-template-columns:
    1.7fr
    0.75fr
    0.9fr
    1fr;

  gap:
    clamp(2rem, 5vw, 6rem);

  padding:
    clamp(2rem, 3.5vh, 3rem)
    0;
}


  .footer-brand {
    grid-column:
      1 / -1;
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 560px) {

  .footer-shell {
    width: 91vw;
  }


  .seo-section {
    padding:
      3.5rem
      0;
  }


  .seo-grid {
    grid-template-columns: 1fr;

    gap: 2rem;
  }


  .seo-head {
    text-align: left;
  }


  .seo-intro {
    margin-left: 0;
  }


  .footer-main {
    grid-template-columns:
      1fr
      1fr;

    gap:
      2rem
      1.5rem;
  }


  .footer-brand {
    grid-column:
      1 / -1;
  }


  .footer-contact {
    grid-column:
      1 / -1;
  }


  .footer-bottom {
    flex-direction: column;

    align-items: flex-start;

    gap: 0.7rem;
  }

}
</style>