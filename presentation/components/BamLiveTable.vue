<script setup>
// ============================================================
//  EDIT YOUR DATA HERE — no need to touch the HTML below
// ============================================================

const bamCore = [
  { company: "Alphabet Inc.", bam: "10.5%", sp: "3.1%" },
  { company: "Airbnb, Inc.", bam: "6.0%", sp: "0.1%" },
  { company: "ServiceNow, Inc.", bam: "5.7%", sp: "0.3%" },
  { company: "Micron Technology, Inc.", bam: "5.5%", sp: "0.6%" },
  { company: "Applied Materials, Inc.", bam: "4.4%", sp: "0.4%" },
  { company: "Tesla, Inc.", bam: "4.4%", sp: "2.1%" },
  { company: "HP Inc.", bam: "3.0%", sp: "0.0%" },
  { company: "Synopsys, Inc.", bam: "3.0%", sp: "0.2%" },
  { company: "Analog Devices, Inc.", bam: "2.7%", sp: "0.2%" },
  { company: "S&P Global Inc.", bam: "2.7%", sp: "0.3%" },
];
const bamCoreTotal = { bam: "47.9%", sp: "7.2%" };

const sp500 = [
  { company: "NVIDIA Corp", sp: "7.8%", bam: "-" },
  { company: "Apple Inc", sp: "6.8%", bam: "2.5%" },
  { company: "Microsoft Corp", sp: "6.0%", bam: "-" },
  { company: "Amazon.com Inc", sp: "3.8%", bam: "-" },
  { company: "Alphabet Inc Class A", sp: "3.1%", bam: "10.5%" },
  { company: "Broadcom Inc", sp: "2.8%", bam: "-" },
  { company: "Alphabet Inc Class C", sp: "2.5%", bam: "-" },
  { company: "Meta Platforms Inc Class A", sp: "2.4%", bam: "-" },
  { company: "Tesla Inc", sp: "2.1%", bam: "4.4%" },
  { company: "Berkshire Hathaway Inc Class B", sp: "1.6%", bam: "-" },
];
const sp500Total = { sp: "38.9%", bam: "17.4%" };

const sectors = [
  { sector: "Information Technology", bam: "34%", sp: "34%" },
  { sector: "Financials", bam: "13%", sp: "13%" },
  { sector: "Communication Services", bam: "10%", sp: "10%" },
  { sector: "Consumer Discretionary", bam: "10%", sp: "10%" },
  { sector: "Health Care", bam: "10%", sp: "10%" },
  { sector: "Industrials", bam: "8%", sp: "8%" },
  { sector: "Consumer Staples", bam: "5%", sp: "5%" },
  { sector: "Energy", bam: "3%", sp: "3%" },
  { sector: "Utilities", bam: "2%", sp: "2%" },
  { sector: "Real Estate", bam: "2%", sp: "2%" },
];

// ============================================================
//  END OF DATA — everything below is auto-rendered
// ============================================================
</script>

<template>
  <div class="bam-live-table" style="display: flex; gap: 15px; width: 100%">
    <!-- BAM CORE TOP 10 WEIGHT -->
    <table>
      <thead>
        <tr>
          <th colspan="4" class="table-title">BAM CORE TOP 10 WEIGHT</th>
        </tr>
        <tr class="header-row">
          <th class="col-nr">Nr</th>
          <th class="col-name">Company</th>
          <th class="col-val">BAM Core</th>
          <th class="col-val">S&amp;P 500</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, i) in bamCore" :key="i" :class="{ alt: i % 2 === 1 }">
          <td class="col-nr">{{ i + 1 }}</td>
          <td class="col-name">{{ row.company }}</td>
          <td class="col-val">{{ row.bam }}</td>
          <td class="col-val">{{ row.sp }}</td>
        </tr>
        <tr class="total-row">
          <td></td>
          <td class="col-name">Total</td>
          <td class="col-val">{{ bamCoreTotal.bam }}</td>
          <td class="col-val">{{ bamCoreTotal.sp }}</td>
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
          <th class="col-val">BAM Core</th>
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
          <th class="col-val">BAM Core</th>
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
.bam-live-table table {
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
