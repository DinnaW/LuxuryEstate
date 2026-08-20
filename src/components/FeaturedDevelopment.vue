<template>
  <section class="testimonials">

    <div class="testimonials-container">

      <!-- HEADER -->
      <div class="testimonials-header">

        <p class="kicker">
          <span class="kicker-line"></span>
          Client Stories
          <span class="kicker-line"></span>
        </p>

        <h2 class="title">
          Stories Behind The Residences
        </h2>

        <p class="subtitle">
          Discover heartfelt accounts of joy and fulfillment as our valued
          clients embark on the quest for their dream homes and prime
          investments.
        </p>

      </div>


      <!-- BENTO LAYOUT -->
      <div class="testimonials-bento">

        <!-- FEATURED CARD -->
        <div class="featured-card">

          <div class="featured-top">

            <span class="index">01</span>

            <div class="stars">

              <span
                v-for="n in 5"
                :key="n"
                class="star"
                :class="{
                  filled: n <= featured.rating,
                  half: n - featured.rating === 0.5
                }"
              >
                ★
              </span>

            </div>

          </div>

          <p class="featured-quote">
            {{ featured.quote }}
          </p>

          <div class="featured-identity">

            <img
              :src="featured.avatar"
              :alt="featured.name"
              class="avatar-lg"
            />

            <div>
              <span class="name">{{ featured.name }}</span>
              <span class="role">Verified Client</span>
            </div>

          </div>

        </div>


        <!-- COMPACT LIST -->
        <div class="compact-list">

          <div
            v-for="(item, i) in restTestimonials"
            :key="item.name"
            class="compact-card"
          >

            <img
              :src="item.avatar"
              :alt="item.name"
              class="avatar-sm"
            />

            <div class="compact-body">

              <div class="compact-head">

                <span class="name">{{ item.name }}</span>

                <div class="stars">

                  <span
                    v-for="n in 5"
                    :key="n"
                    class="star"
                    :class="{
                      filled: n <= item.rating,
                      half: n - item.rating === 0.5
                    }"
                  >
                    ★
                  </span>

                </div>

              </div>

              <p class="compact-quote">
                {{ item.quote }}
              </p>

            </div>

          </div>

        </div>

      </div>

    </div>

  </section>
</template>


<script setup>
import { ref, computed } from "vue";

const testimonials = ref([

  {
    name: "Rachel Hadid",
    avatar: "https://i.pravatar.cc/160?img=47",
    rating: 5,
    quote:
      "Choosing this real estate service was the best decision I ever made. Their team demonstrated exceptional professionalism and expertise from the very first meeting through to closing. I highly recommend their services to anyone searching for their next home."
  },

  {
    name: "Louis Padtrige",
    avatar: "https://i.pravatar.cc/140?img=13",
    rating: 4.5,
    quote:
      "Their expert negotiation skills helped me sell my property at a great price in no time. I would definitely work with them again."
  },

  {
    name: "Anastasia Baldwin",
    avatar: "https://i.pravatar.cc/140?img=32",
    rating: 4.5,
    quote:
      "They patiently answered all our questions, provided valuable insights, and helped us secure our dream home within our budget."
  },

  {
    name: "Harry Jenda",
    avatar: "https://i.pravatar.cc/140?img=11",
    rating: 5,
    quote:
      "They presented us with a stunning selection of homes that perfectly matched our preferences and impressed us with their local knowledge."
  }

]);

const featured = computed(() => testimonials.value[0]);
const restTestimonials = computed(() => testimonials.value.slice(1));
</script>


<style scoped>

/* =========================================================
   RESET
========================================================= */

.testimonials,
.testimonials *,
.testimonials *::before,
.testimonials *::after {
  box-sizing: border-box;
  font-family: sans-serif;
}

.testimonials {
  --gold: #c6a87c;
  --ink: #0a0a0a;
}


/* =========================================================
   SECTION
========================================================= */

.testimonials {
  width: 100%;

  padding:
    clamp(3.5rem, 6vh, 5.5rem)
    0
    clamp(4rem, 7vh, 6rem);

  background: #ffffff;

  color: var(--ink);
}


.testimonials-container {
  width: min(86vw, 1180px);
  margin: 0 auto;
}


/* =========================================================
   HEADER
========================================================= */

.testimonials-header {
  max-width: 620px;
  margin: 0 auto clamp(2.6rem, 4.5vh, 3.6rem);

  text-align: center;
}


.kicker {
  margin:
    0
    0
    0.6rem;

  color: #9d7e46;
  font-size: clamp(16px, 1.02vw, 18px);

  font-weight: 700;

  letter-spacing: 0.2em;

  text-transform: uppercase;
}

.kicker-line {
  width: 26px;
  height: 1px;
  background: var(--gold);
}


.title {
margin: 0;
  font-size: clamp(48px, 3.4vw, 64px);

  font-weight: 400;
  line-height: 1.15;
  letter-spacing: -0.035em;
}


.subtitle {
  max-width: 520px;
  margin: 0.9rem auto 0;

  color: rgba(0, 0, 0, 0.52);

  font-size: clamp(16px, 1.02vw, 18px);
  font-weight: 300;

  line-height: 1.7;
}




/* =========================================================
   BENTO LAYOUT
========================================================= */

.testimonials-bento {
  display: grid;
  grid-template-columns: 1.15fr 1fr;
  gap: clamp(1rem, 1.6vw, 1.4rem);
}


/* =========================================================
   FEATURED CARD
========================================================= */

.featured-card {
  position: relative;

  padding: clamp(2rem, 2.8vw, 2.7rem);

  display: flex;
  flex-direction: column;
  justify-content: space-between;

  background: var(--ink);
  color: #ffffff;

  overflow: hidden;
}


.featured-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
}


.index {
  color: rgba(255, 255, 255, 0.25);

  font-family: sans-serif;
  font-size: clamp(3rem, 4vw, 4rem);
  font-weight: 400;

  line-height: 1;
}


.featured-quote {
  margin: clamp(1.6rem, 2.4vw, 2.2rem) 0;

  color: rgba(255, 255, 255, 0.9);

  font-family: sans-serif;
  font-size: clamp(19px, 1.3vw, 23px);
  font-weight: 200;

  line-height: 1.55;
}


.featured-identity {
  display: flex;
  align-items: center;
  gap: 14px;

  padding-top: clamp(1.2rem, 1.8vw, 1.6rem);

  border-top: 1px solid rgba(255, 255, 255, 0.14);
}


.avatar-lg {
  width: 52px;
  height: 52px;
  flex-shrink: 0;

  border-radius: 50%;
  object-fit: cover;

  border: 1px solid rgba(255, 255, 255, 0.25);
}


.featured-identity div {
  display: flex;
  flex-direction: column;
  gap: 3px;
}


.featured-identity .name {
  color: #ffffff;
  font-size: 16px;
  font-weight: 700;
}


.featured-identity .role {
  color: var(--gold);

  font-size: 12px;
  font-weight: 600;

  letter-spacing: 0.08em;
  text-transform: uppercase;
}


/* =========================================================
   STARS (shared)
========================================================= */

.stars {
  display: flex;
  gap: 3px;
}

.star {
  color: rgba(0, 0, 0, 0.16);
  font-size: 14px;
}

.featured-card .star {
  color: rgba(255, 255, 255, 0.25);
}

.star.filled {
  color: var(--gold);
}

.star.half {
  position: relative;
  color: rgba(0, 0, 0, 0.16);
}

.featured-card .star.half {
  color: rgba(255, 255, 255, 0.25);
}

.star.half::before {
  content: "★";

  position: absolute;
  inset: 0;

  width: 50%;
  overflow: hidden;

  color: var(--gold);
}


/* =========================================================
   COMPACT LIST
========================================================= */

.compact-list {
  display: flex;
  flex-direction: column;
  gap: clamp(1rem, 1.6vw, 1.4rem);
}


.compact-card {
  flex: 1;

  padding: clamp(1.2rem, 1.6vw, 1.5rem);

  display: flex;
  gap: 14px;

  background: #f5f4f1;

  border: 1px solid rgba(0, 0, 0, 0.06);

  transition:
    border-color 0.3s ease,
    background 0.3s ease;
}


.compact-card:hover {
  border-color: rgba(198, 168, 124, 0.4);
  background: #ffffff;
}


.avatar-sm {
  width: 40px;
  height: 40px;
  flex-shrink: 0;

  margin-top: 2px;

  border-radius: 50%;
  object-fit: cover;

  border: 1px solid rgba(0, 0, 0, 0.07);
}


.compact-body {
  min-width: 0;

  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}


.compact-head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}


.compact-head .name {
  color: var(--ink);
  font-size: 14px;
  font-weight: 700;

  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}


.compact-quote {
  margin: 0;

  color: rgba(0, 0, 0, 0.58);

  font-size: 16px;
  font-weight: 300;

  line-height: 1.6;
}


/* =========================================================
   TABLET
========================================================= */

@media (max-width: 900px) {

  .testimonials-bento {
    grid-template-columns: 1fr;
  }


  .featured-card {
    min-height: 0;
  }

}


/* =========================================================
   MOBILE
========================================================= */

@media (max-width: 560px) {

  .testimonials {
    padding: 3rem 0 3.6rem;
  }


  .testimonials-container {
    width: 90vw;
  }


  .testimonials-header {
    margin-bottom: 2.2rem;
  }


  .title {
    font-size: clamp(40px, 10vw, 52px);
  }


  .featured-quote {
    font-size: 16px;
  }


  .compact-card {
    flex-direction: column;
  }


  .avatar-sm {
    margin-top: 0;
  }

}

</style>
