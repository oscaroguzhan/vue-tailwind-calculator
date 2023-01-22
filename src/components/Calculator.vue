<template>
  <div id="container" class="flex flex-col items-center justify-center h-screen bg-black">
    <h1 class="my-8 text-5xl text-center text-white">Calculator</h1>
    <form id="wrapper" class="border w-[500px] h-[450px] flex flex-col pl-6 pt-6 bg-slate-200 gap-8 rounded-lg">
      <div id="display" class="flex flex-col">
        <label for="monthlyCostLabel" class="space-x-4 text-xl font-bold tracking-wide">{{ monthlyCostLabel }}</label>

        <span class="space-x-3 text-2xl font-light leading-8">{{Math.round(MonthlyCost)}} {{ monthlyCostSuffix }}</span>
      </div>
      <div>
        <label for="loanAmountLabel" class="text-xl font-bold">{{ loanAmountLabel }}</label>
        <div class="flex items-center justify-between gap-4 w-[90%]">
          <button class="buttonStyle" @click="decreaseLoanAmount">-</button>
          <input type="number" class="inputStyle" v-model="loanAmount" min="5000" max="600000">
          <button class="buttonStyle" @click="increaseLoanAmount">+</button>
        </div>
      </div>
      <div>
        <label for="repaymentYearsLabel" class="text-xl font-bold">{{ repaymentYearsLabel }}</label>
        <div class="flex items-center justify-between gap-4 w-[90%]">
          <button class="buttonStyle" @click="decreaseRepaymentYear">-</button>
          <input type="number" class="inputStyle" v-model="repaymentYear" min="1" max="15">
          <button class="buttonStyle" @click="increaseRepaymentYear">+</button>
        </div>
      </div>
      <div>
        <button
          class="flex items-center pl-5 text-2xl text-white bg-green-400 w-[90%] py-2 rounded-3xl border border-transparent focus:outline-none focus:ring-green-500 cursor-pointe focus:ring-2 focus:ring-offset-2 hover:bg-green-500 hover:animate-pulse justify-evenly">
          {{ ctaLabel }}
          <span> <i class="text-white fa-solid fa-arrow-right fa-1xl"></i></span>
        </button>

      </div>
    </form>
  </div>
</template>

<script>


export default {
  name: 'Calculator',
  data() {
    return {
      monthlyCostLabel: "Månadkostnad",
      monthlyCostSuffix: "kr",
      loanAmountLabel: "Lånebelopp",
      loanAmountSuffix: "kr",
      repaymentYearsLabel: "Återbetalningstid",
      repaymentYearsSuffix: "år",
      ctaLabel: "Ansök nu",
      interest: 5.77,
      loanAmount: 250000,
      repaymentYear: 14
    }
  },
  computed: {
    MonthlyCost() {
      const rate = this.interest / 100 / 12;
      const months = this.repaymentYear * 12;
      const p = this.loanAmount;

      return (p * rate * (1 + rate) ** months) / ((1 + rate) ** months - 1);
    }
  },
  methods: {
    increaseLoanAmount(event) {
      event.preventDefault();
      this.loanAmount = this.loanAmount + 5000;
      if (this.loanAmount > 600000) {
        this.loanAmount = 600000;
      }
    },
    decreaseLoanAmount(event) {
      event.preventDefault();
      if (this.loanAmount > 5000) {
        this.loanAmount = this.loanAmount - 5000;
      } else {
        this.loanAmount = 5000
      }
    },
    decreaseRepaymentYear(e) {
      e.preventDefault();
      { { this.repaymentYear > 1 ? this.repaymentYear-- : 1 } }
    },
    increaseRepaymentYear(e) {
      e.preventDefault();
      { { this.repaymentYear < 15 ? this.repaymentYear++ : 15 } }
    },
  }

}
</script>