<template>
  <section class="market">

    <div class="shell">

      <!-- =========================
           TITLE ROW
      ========================== -->
      <div class="top-row">

        <div class="title-wrap">

          <p class="kicker">
            MARKET INTELLIGENCE
          </p>

          <div class="title-line">

            <h2>
              Property Price Trends
            </h2>

            <div class="property-select">
              <select v-model="propertyType">
                <option>Apartments</option>
                <option>Penthouses</option>
                <option>Luxury Residences</option>
              </select>
            </div>

          </div>

          <p class="intro">
            Track indicative residential price movement across selected
            Sri Lankan property markets.
          </p>

        </div>

      </div>


      <!-- =========================
           MAIN WHITE PANEL
      ========================== -->
      <div class="market-card">

        <!-- CONTROLS -->
        <div class="controls">

          <div class="mode-switch">

            <button
              type="button"
              :class="{ active: mode === 'Buy' }"
              @click="mode = 'Buy'"
            >
              Buy
            </button>

            <button
              type="button"
              :class="{ active: mode === 'Rent' }"
              @click="mode = 'Rent'"
            >
              Rent
            </button>

          </div>


          <div class="bedroom-filter">

            <span>
              Bedrooms
            </span>

            <select v-model="bedrooms">
              <option>All</option>
              <option>1 Bedroom</option>
              <option>2 Bedrooms</option>
              <option>3 Bedrooms</option>
              <option>4+ Bedrooms</option>
            </select>

          </div>

        </div>


        <!-- =========================
             STATS
        ========================== -->
        <div class="stats">

          <div class="stat">

            <span class="stat-label">
              Average Price
              <small>
                Last 12 months
              </small>
            </span>

            <strong class="main-stat">
              {{
                mode === "Buy"
                  ? "Rs 48,556.8"
                  : "Rs 385,000"
              }}
            </strong>

            <span class="unit">
              {{
                mode === "Buy"
                  ? "per sq.ft"
                  : "per month"
              }}
            </span>

          </div>


          <div class="stat">

            <span class="stat-label">
              Past 12 months
            </span>

            <div class="growth">

              <strong>
                {{
                  mode === "Buy"
                    ? "6.38%"
                    : "4.92%"
                }}
              </strong>

              <span class="arrow">
                ↑
              </span>

            </div>

          </div>


          <div class="stat">

            <span class="stat-label">
              Past 3 months
            </span>

            <div class="growth">

              <strong>
                {{
                  mode === "Buy"
                    ? "7.7%"
                    : "3.8%"
                }}
              </strong>

              <span class="arrow">
                ↑
              </span>

            </div>

          </div>

        </div>


        <!-- =========================
             CHART AREA
        ========================== -->
        <div class="chart">

          <!-- Y AXIS VALUES -->
          <div class="y-axis">
            <span>60K</span>
            <span>50K</span>
            <span>40K</span>
            <span>30K</span>
          </div>


          <!-- GRID -->
          <div class="chart-grid">

            <i></i>
            <i></i>
            <i></i>
            <i></i>

          </div>


          <!-- BUY GRAPH -->
          <svg
            v-if="mode === 'Buy'"
            class="graph"
            viewBox="0 0 1000 320"
            preserveAspectRatio="none"
          >

            <defs>

              <linearGradient
                id="buyGradient"
                x1="0"
                y1="0"
                x2="0"
                y2="1"
              >
                <stop
                  offset="0%"
                  stop-color="#111111"
                  stop-opacity="0.12"
                />

                <stop
                  offset="100%"
                  stop-color="#111111"
                  stop-opacity="0.01"
                />
              </linearGradient>

            </defs>


            <path
              class="graph-area"
              fill="url(#buyGradient)"
              d="
              M0,270
              C35,270 55,275 80,260
              C105,245 120,195 150,180
              C185,160 205,165 235,145
              C265,130 280,105 310,110
              C350,115 355,160 390,150
              C425,135 430,200 470,185
              C505,170 515,150 545,165
              C575,180 595,165 620,150
              C650,135 665,165 700,145
              C730,130 745,95 775,85
              C810,72 820,60 845,75
              C870,90 885,95 910,78
              C930,60 950,55 1000,50
              L1000,320
              L0,320
              Z
              "
            />

            <path
              class="graph-line"
              d="
              M0,270
              C35,270 55,275 80,260
              C105,245 120,195 150,180
              C185,160 205,165 235,145
              C265,130 280,105 310,110
              C350,115 355,160 390,150
              C425,135 430,200 470,185
              C505,170 515,150 545,165
              C575,180 595,165 620,150
              C650,135 665,165 700,145
              C730,130 745,95 775,85
              C810,72 820,60 845,75
              C870,90 885,95 910,78
              C930,60 950,55 1000,50
              "
            />

          </svg>


          <!-- RENT GRAPH -->
          <svg
            v-else
            class="graph"
            viewBox="0 0 1000 320"
            preserveAspectRatio="none"
          >

            <defs>

              <linearGradient
                id="rentGradient"
                x1="0"
                y1="0"
                x2="0"
                y2="1"
              >
                <stop
                  offset="0%"
                  stop-color="#111111"
                  stop-opacity="0.12"
                />

                <stop
                  offset="100%"
                  stop-color="#111111"
                  stop-opacity="0.01"
                />
              </linearGradient>

            </defs>


            <path
              class="graph-area"
              fill="url(#rentGradient)"
              d="
              M0,265
              C50,255 70,240 110,225
              C150,210 180,190 220,195
              C260,200 280,215 320,195
              C360,175 390,160 430,165
              C470,170 500,185 540,165
              C585,145 610,125 650,130
              C690,135 725,150 760,125
              C800,100 840,95 875,85
              C915,72 950,60 1000,58
              L1000,320
              L0,320
              Z
              "
            />

            <path
              class="graph-line"
              d="
              M0,265
              C50,255 70,240 110,225
              C150,210 180,190 220,195
              C260,200 280,215 320,195
              C360,175 390,160 430,165
              C470,170 500,185 540,165
              C585,145 610,125 650,130
              C690,135 725,150 760,125
              C800,100 840,95 875,85
              C915,72 950,60 1000,58
              "
            />

          </svg>


          <!-- X AXIS -->
          <div class="years">

            <span>
              Jan '22
            </span>

            <span>
              Feb '23
            </span>

            <span>
              Mar '24
            </span>

            <span>
              Apr '25
            </span>

            <span>
              Jul '26
            </span>

          </div>

        </div>

      </div>


      <!-- DISCLAIMER -->
      <p class="note">

        <span class="note-icon">
          △
        </span>

        Indicative price information is shown for presentation purposes
        and should be verified against current market data.

      </p>

    </div>

  </section>
</template>


<script setup>

import { ref } from "vue";


const mode = ref("Buy");

const propertyType = ref("Apartments");

const bedrooms = ref("All");

</script>


<style scoped>

/* =====================================================
   SECTION
===================================================== */

.market {
  width: 100%;

  padding:
    clamp(4rem, 7vh, 6rem)
    0;

  background:
    #f3f3f2;

  color:
    #111111;
}


.shell {
  width:
    min(
      91vw,
      1500px
    );

  margin:
    0 auto;
}


/* =====================================================
   TOP TITLE
===================================================== */

.top-row {
  margin-bottom:
    clamp(
      1.4rem,
      2.5vh,
      2rem
    );
}


.kicker {
  margin:
    0
    0
    clamp(
      0.45rem,
      0.7vh,
      0.6rem
    );

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.48rem,
      0.54vw,
      0.62rem
    );

  font-weight:
    400;

  letter-spacing:
    0.2em;

  text-transform:
    uppercase;

  color:
    #74716d;
}


.title-line {
  display:
    flex;

  align-items:
    center;

  flex-wrap:
    wrap;

  gap:
    clamp(
      1rem,
      2vw,
      2rem
    );
}


.title-line h2 {
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
}


/* =====================================================
   PROPERTY TYPE
===================================================== */

.property-select {
  position:
    relative;
}


.property-select select {
  min-width:
    clamp(
      160px,
      15vw,
      220px
    );

  height:
    42px;

  padding:
    0
    2.4rem
    0
    0.9rem;

  border:
    1px solid
    #c9c7c3;

  background:
    #ffffff;

  color:
    #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.62rem,
      0.68vw,
      0.76rem
    );

  outline:
    none;

  cursor:
    pointer;
}


.intro {
  max-width:
    620px;

  margin:
    clamp(
      0.65rem,
      1.2vh,
      0.9rem
    )
    0
    0;

  color:
    #77736f;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.62rem,
      0.68vw,
      0.76rem
    );

  line-height:
    1.6;
}


/* =====================================================
   WHITE CARD
===================================================== */

.market-card {
  position:
    relative;

  padding:
    clamp(
      1.2rem,
      2vw,
      2rem
    );

  background:
    #ffffff;

  border:
    1px solid
    rgba(
      17,
      17,
      17,
      0.08
    );

  border-radius:
    0;

  box-shadow:
    0
    16px
    40px
    rgba(
      0,
      0,
      0,
      0.025
    );
}


/* =====================================================
   CONTROLS
===================================================== */

.controls {
  display:
    flex;

  align-items:
    center;

  justify-content:
    flex-end;

  gap:
    clamp(
      1rem,
      2vw,
      2rem
    );

  margin-bottom:
    clamp(
      1.6rem,
      3vh,
      2.4rem
    );
}


/* =====================================================
   BUY RENT
===================================================== */

.mode-switch {
  display:
    flex;

  border:
    1px solid
    #111111;
}


.mode-switch button {
  min-width:
    70px;

  height:
    38px;

  padding:
    0
    1rem;

  border:
    0;

  border-right:
    1px solid
    #111111;

  background:
    #ffffff;

  color:
    #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.6rem,
      0.64vw,
      0.7rem
    );

  cursor:
    pointer;

  transition:
    all
    0.3s
    ease;
}


.mode-switch button:last-child {
  border-right:
    0;
}


.mode-switch .active {
  background:
    #111111;

  color:
    #ffffff;
}


/* =====================================================
   BEDROOM FILTER
===================================================== */

.bedroom-filter {
  display:
    flex;

  align-items:
    center;

  gap:
    0.8rem;

  padding-left:
    clamp(
      1rem,
      1.7vw,
      1.6rem
    );

  border-left:
    1px solid
    #e5e3df;
}


.bedroom-filter span {
  color:
    #8c8883;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.58rem,
      0.64vw,
      0.72rem
    );
}


.bedroom-filter select {
  height:
    38px;

  padding:
    0
    2rem
    0
    0.75rem;

  border:
    1px solid
    #c9c7c3;

  background:
    #ffffff;

  color:
    #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.58rem,
      0.63vw,
      0.7rem
    );

  outline:
    none;
}


/* =====================================================
   STATS
===================================================== */

.stats {
  display:
    grid;

  grid-template-columns:
    1.4fr
    1fr
    1fr;

  max-width:
    850px;

  margin-bottom:
    clamp(
      1.8rem,
      3vh,
      2.5rem
    );
}


.stat {
  padding:
    0
    clamp(
      1rem,
      1.7vw,
      1.6rem
    );

  border-right:
    1px solid
    #ebe9e6;
}


.stat:first-child {
  padding-left:
    0;
}


.stat:last-child {
  border-right:
    0;
}


.stat-label {
  display:
    block;

  margin-bottom:
    0.35rem;

  color:
    #8f8a84;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.58rem,
      0.64vw,
      0.72rem
    );

  line-height:
    1.3;
}


.stat-label small {
  font-size:
    inherit;

  font-weight:
    400;
}


.main-stat {
  display:
    inline-block;

  color:
    #111111;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      1rem,
      1.2vw,
      1.35rem
    );

  font-weight:
    400;

  line-height:
    1;
}


.unit {
  margin-left:
    0.3rem;

  color:
    #55514c;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.66rem,
      0.72vw,
      0.8rem
    );
}


/* =====================================================
   GROWTH
===================================================== */

.growth {
  display:
    flex;

  align-items:
    center;

  gap:
    0.35rem;
}


.growth strong {
  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      1rem,
      1.18vw,
      1.35rem
    );

  font-weight:
    400;
}


.arrow {
  color:
    #111111;

  font-size:
    clamp(
      0.9rem,
      1vw,
      1.1rem
    );

  line-height:
    1;
}


/* =====================================================
   CHART
===================================================== */

.chart {
  position:
    relative;

  height:
    clamp(
      290px,
      31vw,
      440px
    );

  padding-left:
    48px;

  padding-bottom:
    30px;
}


/* =====================================================
   Y AXIS
===================================================== */

.y-axis {
  position:
    absolute;

  top:
    0;

  bottom:
    32px;

  left:
    0;

  width:
    40px;

  display:
    flex;

  flex-direction:
    column;

  justify-content:
    space-between;

  color:
    #9a9690;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.48rem,
      0.52vw,
      0.58rem
    );
}


/* =====================================================
   GRID
===================================================== */

.chart-grid {
  position:
    absolute;

  top:
    0;

  right:
    0;

  bottom:
    32px;

  left:
    48px;

  display:
    flex;

  flex-direction:
    column;

  justify-content:
    space-between;
}


.chart-grid i {
  width:
    100%;

  height:
    1px;

  background:
    #eceae6;
}


/* =====================================================
   GRAPH
===================================================== */

.graph {
  position:
    absolute;

  top:
    0;

  right:
    0;

  bottom:
    32px;

  left:
    48px;

  width:
    calc(100% - 48px);

  height:
    calc(100% - 32px);
}


.graph-line {
  fill:
    none;

  stroke:
    #111111;

  stroke-width:
    2.7;

  stroke-linecap:
    round;

  stroke-linejoin:
    round;

  vector-effect:
    non-scaling-stroke;
}


/* =====================================================
   YEARS
===================================================== */

.years {
  position:
    absolute;

  left:
    48px;

  right:
    0;

  bottom:
    0;

  display:
    flex;

  justify-content:
    space-between;

  color:
    #8f8b85;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.48rem,
      0.53vw,
      0.6rem
    );
}


/* =====================================================
   NOTE
===================================================== */

.note {
  display:
    flex;

  align-items:
    center;

  gap:
    0.5rem;

  margin:
    clamp(
      0.9rem,
      1.6vh,
      1.3rem
    )
    0
    0;

  color:
    #aaa6a0;

  font-family:
    Georgia,
    "Times New Roman",
    serif;

  font-size:
    clamp(
      0.48rem,
      0.53vw,
      0.6rem
    );

  line-height:
    1.5;
}


.note-icon {
  font-size:
    0.62rem;
}


/* =====================================================
   TABLET
===================================================== */

@media (max-width: 850px) {

  .controls {
    justify-content:
      space-between;
  }


  .stats {
    max-width:
      none;
  }

}


/* =====================================================
   MOBILE
===================================================== */

@media (max-width: 600px) {

  .market {
    padding:
      3.5rem
      0;
  }


  .title-line {
    align-items:
      flex-start;

    flex-direction:
      column;
  }


  .title-line h2 {
    font-size:
      clamp(
        2rem,
        10vw,
        3rem
      );
  }


  .property-select {
    width:
      100%;
  }


  .property-select select {
    width:
      100%;
  }


  .market-card {
    padding:
      1rem;
  }


  .controls {
    align-items:
      stretch;

    flex-direction:
      column;
  }


  .mode-switch {
    width:
      100%;
  }


  .mode-switch button {
    flex:
      1;
  }


  .bedroom-filter {
    justify-content:
      space-between;

    padding-left:
      0;

    border-left:
      0;
  }


  .stats {
    grid-template-columns:
      1fr;

    margin-bottom:
      1.6rem;
  }


  .stat,
  .stat:first-child {
    padding:
      0.9rem
      0;

    border-right:
      0;

    border-bottom:
      1px solid
      #ebe9e6;
  }


  .stat:first-child {
    padding-top:
      0;
  }


  .stat:last-child {
    border-bottom:
      0;
  }


  .chart {
    height:
      260px;

    padding-left:
      36px;
  }


  .chart-grid,
  .graph,
  .years {
    left:
      36px;
  }


  .graph {
    width:
      calc(100% - 36px);
  }


  .y-axis {
    width:
      30px;
  }

}

</style>