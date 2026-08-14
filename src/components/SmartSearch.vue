<template>
  <footer class="site-footer">

    <div class="footer-shell">

      <!-- ==========================================
           POPULAR SEARCHES / SEO
      =========================================== -->
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


        <!-- SEARCH COLUMNS -->
        <div class="seo-grid">

          <!-- APARTMENTS -->
          <div class="seo-column">

            <h3>Apartments</h3>

            <nav>
              <a href="#">Luxury apartments in Colombo</a>
              <a href="#">Apartments in Colombo 03</a>
              <a href="#">Apartments in Colombo 07</a>
              <a href="#">Ocean-view apartments</a>
            </nav>

            <a href="#" class="view-more">
              View more
              <span>→</span>
            </a>

          </div>


          <!-- INVESTMENT -->
          <div class="seo-column">

            <h3>Investment</h3>

            <nav>
              <a href="#">High-yield residences</a>
              <a href="#">Rental-ready apartments</a>
              <a href="#">Long-term investment homes</a>
              <a href="#">New launch opportunities</a>
            </nav>

            <a href="#" class="view-more">
              View more
              <span>→</span>
            </a>

          </div>


          <!-- LOCATIONS -->
          <div class="seo-column">

            <h3>Locations</h3>

            <nav>
              <a href="#">Colombo residences</a>
              <a href="#">Colombo 03 residences</a>
              <a href="#">Colombo 07 residences</a>
              <a href="#">Galle residences</a>
            </nav>

            <a href="#" class="view-more">
              View more
              <span>→</span>
            </a>

          </div>


          <!-- LIFESTYLE -->
          <div class="seo-column">

            <h3>Lifestyle</h3>

            <nav>
              <a href="#">Ocean-view living</a>
              <a href="#">City-centre living</a>
              <a href="#">Private amenity residences</a>
              <a href="#">Penthouse living</a>
            </nav>

            <a href="#" class="view-more">
              View more
              <span>→</span>
            </a>

          </div>

        </div>

      </section>


      <!-- ==========================================
           FOOTER
      =========================================== -->
      <section class="footer-main">

        <!-- BRAND -->
        <div class="footer-brand">

          <a href="#" class="brand">
            LUXURY ESTATE
          </a>

          <p>
            Distinctive residences and premium property
            opportunities across Sri Lanka.
          </p>

        </div>


        <!-- COMPANY -->
        <div class="footer-column">

          <h4>Company</h4>

          <a href="#">About Us</a>
          <a href="#">Our Projects</a>
          <a href="#">Apartments</a>
          <a href="#">Contact</a>

        </div>


        <!-- PROPERTY -->
        <div class="footer-column">

          <h4>Property</h4>

          <a href="#">Featured Residences</a>
          <a href="#">Hot Deals</a>
          <a href="#">Trending Properties</a>
          <a href="#">Area Guide</a>

        </div>


        <!-- CONTACT -->
        <div class="footer-column">

          <h4>Enquiries</h4>

          <a href="tel:+94112345678">
            +94 11 234 5678
          </a>

          <a href="mailto:hello@luxuryestate.lk">
            hello@luxuryestate.lk
          </a>

          <span>
            Colombo, Sri Lanka
          </span>

        </div>

      </section>


      <!-- ==========================================
           BOTTOM
      =========================================== -->
      <div class="footer-bottom">

        <p>
          © {{ year }} Luxury Estate. All rights reserved.
        </p>

        <div class="legal">
          <a href="#">Privacy</a>
          <a href="#">Terms</a>
          <a href="#">Cookies</a>
        </div>

      </div>

    </div>

  </footer>
</template>


<script setup>
const year = new Date().getFullYear();
</script>


<style scoped>

/* =========================================
   GLOBAL
========================================= */

.site-footer,
.site-footer *,
.site-footer *::before,
.site-footer *::after {
  box-sizing: border-box;
  font-family: sans-serif;
}


/* =========================================
   MAIN
========================================= */

.site-footer {
  width: 100%;
  background: #f5f3ee;
  color: #111111;
}


.footer-shell {
  width: min(91vw, 1550px);
  margin: 0 auto;
}


/* =========================================
   SEO SECTION
   COMPACT HEIGHT
========================================= */

.seo-section {
  width: 100%;

  padding:
    2.2rem
    0
    2rem;

  border-bottom:
    1px solid rgba(17, 17, 17, 0.12);
}


/* =========================================
   SEO HEADER
========================================= */

.seo-head {
  max-width: 600px;

  margin:
    0 auto
    1.5rem;

  text-align: center;
}


.kicker {
  margin: 0;

  color: #9b7b42;

  font-size:
    clamp(
      0.46rem,
      0.5vw,
      0.55rem
    );

  font-weight: 600;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}


.seo-head h2 {
  margin:
    0.35rem
    0
    0;

  font-size:
    clamp(
      0.5rem,
      1.8vw,
      1.1rem
    );

  font-weight: 100;

  line-height: 1.05;

  letter-spacing: -0.035em;
}


.seo-intro {
  max-width: 450px;

  margin:
    0.5rem
    auto
    0;

  color: #77736e;

  font-size:
    clamp(
      0.58rem,
      0.62vw,
      0.68rem
    );

  line-height: 1.5;
}


/* =========================================
   SEO GRID
========================================= */

.seo-grid {
  display: grid;

  grid-template-columns:
    repeat(4, minmax(0, 1fr));

  gap:
    clamp(
      1.5rem,
      3vw,
      3.5rem
    );
}


/* =========================================
   SEO COLUMNS
========================================= */

.seo-column h3 {
  margin:
    0
    0
    0.5rem;

  padding-bottom: 0.45rem;

  border-bottom:
    1px solid #d1cdc6;

  color: #55514d;

  font-size:
    clamp(
      0.82rem,
      0.9vw,
      1rem
    );

  font-weight: 500;
}


.seo-column nav {
  display: flex;

  flex-direction: column;

  gap: 0.3rem;
}


.seo-column nav a {
  width: fit-content;

  color: #252321;

  font-size:
    clamp(
      0.55rem,
      0.59vw,
      0.65rem
    );

  font-weight: 400;

  line-height: 1.3;

  text-decoration: none;

  transition:
    color 0.25s ease,
    transform 0.25s ease;
}


.seo-column nav a:hover {
  color: #9b7b42;

  transform: translateX(3px);
}


/* =========================================
   VIEW MORE
========================================= */

.view-more {
  width: fit-content;

  display: inline-flex;

  align-items: center;

  gap: 0.4rem;

  margin-top: 0.55rem;

  padding-bottom: 0.12rem;

  color: #111111;

  border-bottom:
    1px solid transparent;

  font-size:
    clamp(
      0.42rem,
      0.46vw,
      0.5rem
    );

  font-weight: 700;

  letter-spacing: 0.1em;

  text-decoration: none;

  text-transform: uppercase;

  transition:
    border-color 0.25s ease;
}


.view-more:hover {
  border-color: #111111;
}


/* =========================================
   FOOTER MAIN
========================================= */

.footer-main {
  display: grid;

  grid-template-columns:
    1.7fr
    0.7fr
    0.9fr
    1fr;

  gap:
    clamp(
      1.5rem,
      3.5vw,
      4rem
    );

  padding:
    1.5rem
    0;
}


/* =========================================
   BRAND
========================================= */

.brand {
  display: inline-block;

  color: #111111;

  font-size:
    clamp(
      0.9rem,
      1.1vw,
      1.2rem
    );

  font-weight: 700;

  letter-spacing: 0.06em;

  text-decoration: none;
}


.footer-brand p {
  max-width: 320px;

  margin:
    0.5rem
    0
    0;

  color: #7c7770;

  font-size:
    clamp(
      0.54rem,
      0.58vw,
      0.64rem
    );

  line-height: 1.45;
}


/* =========================================
   FOOTER COLUMNS
========================================= */

.footer-column {
  display: flex;

  flex-direction: column;

  align-items: flex-start;

  gap: 0.3rem;
}


.footer-column h4 {
  margin:
    0
    0
    0.2rem;

  color: #99938b;

  font-size: 0.45rem;

  font-weight: 700;

  letter-spacing: 0.15em;

  text-transform: uppercase;
}


.footer-column a {
  color: #24211f;

  font-size:
    clamp(
      0.54rem,
      0.58vw,
      0.64rem
    );

  font-weight: 500;

  line-height: 1.35;

  text-decoration: none;

  transition:
    color 0.25s ease,
    transform 0.25s ease;
}


.footer-column a:hover {
  color: #9b7b42;

  transform: translateX(2px);
}


.footer-column span {
  color: #7d7871;

  font-size:
    clamp(
      0.53rem,
      0.57vw,
      0.63rem
    );
}


/* =========================================
   BOTTOM
========================================= */

.footer-bottom {
  display: flex;

  align-items: center;

  justify-content: space-between;

  gap: 1rem;

  padding:
    0.6rem
    0
    0.7rem;

  border-top:
    1px solid rgba(17, 17, 17, 0.12);
}


.footer-bottom p {
  margin: 0;

  color: #8a857e;

  font-size:
    clamp(
      0.44rem,
      0.48vw,
      0.53rem
    );
}


.legal {
  display: flex;

  align-items: center;

  gap:
    clamp(
      0.6rem,
      1vw,
      1rem
    );
}


.legal a {
  color: #77716b;

  font-size:
    clamp(
      0.44rem,
      0.48vw,
      0.53rem
    );

  text-decoration: none;
}


.legal a:hover {
  color: #111111;
}


/* =========================================
   TABLET
========================================= */

@media (max-width: 900px) {

  .seo-section {
    padding:
      2rem
      0;
  }


  .seo-grid {
    grid-template-columns:
      repeat(2, minmax(0, 1fr));

    gap:
      1.3rem
      2rem;
  }


  .footer-main {
    grid-template-columns:
      repeat(3, 1fr);

    gap: 1.5rem;
  }


  .footer-brand {
    grid-column:
      1 / -1;
  }

}


/* =========================================
   MOBILE
========================================= */

@media (max-width: 560px) {

  .footer-shell {
    width: 90vw;
  }


  .seo-section {
    padding:
      1.8rem
      0;
  }


  .seo-head {
    margin-bottom: 1.3rem;

    text-align: left;
  }


  .seo-intro {
    margin-left: 0;
    margin-right: 0;
  }


  .seo-grid {
    grid-template-columns: 1fr;

    gap: 1.25rem;
  }


  .footer-main {
    grid-template-columns:
      1fr
      1fr;

    gap:
      1.2rem
      1rem;

    padding:
      1.3rem
      0;
  }


  .footer-brand {
    grid-column:
      1 / -1;
  }


  .footer-column:last-child {
    grid-column:
      1 / -1;
  }


  .footer-bottom {
    flex-direction: column;

    align-items: flex-start;

    gap: 0.4rem;

    padding:
      0.6rem
      0
      0.8rem;
  }

}

</style>