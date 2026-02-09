<script setup>
// ============================================================
//  EDIT YOUR DATA HERE — no need to touch the HTML below
// ============================================================

const bamUC = [
  { company: "ServiceNow, Inc.", bam: "14.1%", sp: "0.26%" },
  { company: "Micron Technology, Inc.", bam: "13.4%", sp: "0.60%" },
  { company: "Alphabet Inc.", bam: "10.8%", sp: "3.12%" },
  { company: "Applied Materials, Inc.", bam: "8.7%", sp: "0.36%" },
  { company: "ResMed Inc.", bam: "7.8%", sp: "0.06%" },
  { company: "HP Inc.", bam: "4.1%", sp: "0.04%" },
  { company: "Synopsys, Inc.", bam: "4.0%", sp: "0.15%" },
  { company: "Booking Holdings Inc.", bam: "3.7%", sp: "0.29%" },
  { company: "S&P Global Inc.", bam: "3.6%", sp: "0.27%" },
  { company: "Analog Devices, Inc.", bam: "3.3%", sp: "0.23%" },
];
const bamUCTotal = { bam: "73.5%", sp: "5.4%" };

const sp500 = [
  { company: "NVIDIA Corp", sp: "7.82%", bam: "-" },
  { company: "Apple Inc", sp: "6.82%", bam: "3%" },
  { company: "Microsoft Corp", sp: "5.99%", bam: "-" },
  { company: "Amazon.com Inc", sp: "3.75%", bam: "-" },
  { company: "Alphabet Inc Class A", sp: "3.12%", bam: "11%" },
  { company: "Broadcom Inc", sp: "2.80%", bam: "-" },
  { company: "Alphabet Inc Class C", sp: "2.50%", bam: "-" },
  { company: "Meta Platforms Inc Class A", sp: "2.41%", bam: "-" },
  { company: "Tesla Inc", sp: "2.10%", bam: "-" },
  { company: "Berkshire Hathaway Inc Class B", sp: "1.55%", bam: "-" },
];
const sp500Total = { sp: "38.9%", bam: "13.5%" };

const sectors = [
  { sector: "Information Technology", bam: "66.4%", sp: "34%" },
  { sector: "Financials", bam: "6.6%", sp: "13%" },
  { sector: "Communication Services", bam: "10.8%", sp: "10%" },
  { sector: "Consumer Discretionary", bam: "3.7%", sp: "10%" },
  { sector: "Health Care", bam: "7.8%", sp: "10%" },
  { sector: "Industrials", bam: "2.4%", sp: "8%" },
  { sector: "Consumer Staples", bam: "0.0%", sp: "5%" },
  { sector: "Energy", bam: "2.4%", sp: "3%" },
  { sector: "Utilities", bam: "0.0%", sp: "2%" },
  { sector: "Real Estate", bam: "0.0%", sp: "2%" },
];

// ============================================================
//  END OF DATA — everything below is auto-rendered
// ============================================================
</script>

<template>
  <div class="bam-un-live-table" style="display: flex; gap: 15px; width: 100%">
    <!-- BAM UNCONSTRAINED TOP 10 -->
    <table>
      <thead>
        <tr>
          <th colspan="4" class="table-title">BAM UNCONSTRAINED TOP 10</th>
        </tr>
        <tr class="header-row">
          <th class="col-nr">Nr</th>
          <th class="col-name">Company</th>
          <th class="col-val">BAM UC</th>
          <th class="col-val">S&amp;P 500</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, i) in bamUC" :key="i" :class="{ alt: i % 2 === 1 }">
          <td class="col-nr">{{ i + 1 }}</td>
          <td class="col-name">{{ row.company }}</td>
          <td class="col-val">{{ row.bam }}</td>
          <td class="col-val">{{ row.sp }}</td>
        </tr>
        <tr class="total-row">
          <td></td>
          <td class="col-name">Total</td>
          <td class="col-val">{{ bamUCTotal.bam }}</td>
          <td class="col-val">{{ bamUCTotal.sp }}</td>
        </tr>
      </tbody>
    </table>

    <!-- S&P 500 TOP 10 WEIGHT -->
    <table>
      <thead>
        <tr>
          <th colspan="4" class="table-title">S&amp;P 500 TOP 10 WEIGHT</th>
        </tr>
        <tr class="header-row">
          <th class="col-nr">Nr</th>
          <th class="col-name">Company</th>
          <th class="col-val">S&amp;P 500</th>
          <th class="col-val">BAM UC</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, i) in sp500" :key="i" :class="{ alt: i % 2 === 1 }">
          <td class="col-nr">{{ i + 1 }}</td>
          <td class="col-name">{{ row.company }}</td>
          <td class="col-val">{{ row.sp }}</td>
          <td class="col-val">{{ row.bam }}</td>
        </tr>
        <tr class="total-row">
          <td></td>
          <td class="col-name">Total</td>
          <td class="col-val">{{ sp500Total.sp }}</td>
          <td class="col-val">{{ sp500Total.bam }}</td>
        </tr>
      </tbody>
    </table>

    <!-- SECTOR WEIGHT -->
    <table>
      <thead>
        <tr>
          <th colspan="4" class="table-title">SECTOR WEIGHT</th>
        </tr>
        <tr class="header-row">
          <th class="col-nr">Nr</th>
          <th class="col-name">Sector</th>
          <th class="col-val">BAM UC</th>
          <th class="col-val">S&amp;P 500</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, i) in sectors" :key="i" :class="{ alt: i % 2 === 1 }">
          <td class="col-nr">{{ i + 1 }}</td>
          <td class="col-name">{{ row.sector }}</td>
          <td class="col-val">{{ row.bam }}</td>
          <td class="col-val">{{ row.sp }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.bam-un-live-table table {
  border-collapse: collapse;
  flex: 1;
  font-size: 0.45em;
}
.table-title {
  text-align: center;
  font-weight: bold;
  border-bottom: 2px solid #5d8392;
  color: #5d8392;
  padding: 0.3rem;
}
.header-row {
  border-bottom: 1px solid #e0e0e0;
  color: #666;
  font-size: 0.9em;
}
.col-nr {
  text-align: center;
  padding: 0.15rem 0.25rem;
}
.col-name {
  text-align: left;
  padding: 0.15rem 0.25rem;
}
.col-val {
  text-align: center;
  padding: 0.15rem 0.25rem;
}
tbody td {
  border-bottom: 1px solid #e0e0e0;
}
.alt {
  background: #f9f9fb;
}
.total-row {
  font-weight: bold;
  border-top: 2px solid #ccc;
  background: #f9f9fb;
}
</style>
