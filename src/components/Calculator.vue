<template>
  <div id="container" class="flex flex-col items-center justify-center h-screen bg-black">
    <h1 class="my-8 text-5xl text-center text-white">Calculator</h1>
    <form id="wrapper" class="border w-[500px] h-[450px] flex flex-col pl-6 pt-6 bg-slate-200 gap-8 rounded-lg">
      <div id="display" class="flex flex-col">
        <label for="monthlyCostLabel" class="space-x-4 text-xl font-bold tracking-wide">{{ monthlyCostLabel }}</label>
       
        <span class="space-x-3 text-2xl font-light leading-8">2450 {{ monthlyCostSuffix }}</span>
      </div>
      <div>
        <label for="loanAmountLabel" class="text-xl font-bold">{{ loanAmountLabel }}</label>
        <div class="flex items-center justify-between gap-4 w-[90%]">
          <button class="buttonStyle">-</button>
          <input type="number" class="inputStyle" v-model="loanAmount" min="5000" max="600000">
          <button class="buttonStyle">+</button>
        </div>
      </div>
      <div>
        <label for="repaymentYearsLabel" class="text-xl font-bold">{{ repaymentYearsLabel }}</label>
        <div class="flex items-center justify-between gap-4 w-[90%]">
          <button class="buttonStyle">-</button>
          <input type="number" class="inputStyle" v-model="repaymentYear" min="1" max="15">
          <button class="buttonStyle">+</button>
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
  }

}
</script>