<script>
  import { slide } from "svelte/transition";
  import Footer from "./Components/footer.svelte";
  let borderRadius = 50;
  let userInputs = [{ name: "Title", value: "Event Name" }];
  let rangeSliders = [
    {
      name: "Border Radius",
      value: "20",
      min: "0",
      max: "70",
      placeholder: "Enter a number",
    },
    {
      name: "Card Width",
      value: "350",
      min: "175",
      max: "750",
      placeholder: "Enter a number",
    },
    {
      name: "Card Height",
      value: "200",
      min: "100",
      max: "375",
      placeholder: "Enter a number",
    },
    {
      name: "Font Size",
      value: "30",
      min: "0",
      max: "70",
      placeholder: "Enter"
    }
  ];
  let colorPickers = [
    { name: "Font Color", value: "#FFFFFF" },
    { name: "Background Color", value: "#FC5903" },
  ];
  // Define categories and their respective options
  let categories = [
    { name: "Content Alignment", options: ["Center", "Right", "Left"] },
    { name: "Language", options: ["English", "French", "Spanish"] },
    {
      name: "Font Weight",
      options: ["Bold", "800", "700", "600", "500", "400", "300", "200", "100"],
    },
  ];

  let datePickers = [{ name: "Date Of Event", value: "2025-3-31" }];

  // Variables to store selected values
  let selectedAlignment = categories[0].options[0];
  let selectedLanguage = categories[1].options[0];
  let selectedFontweight = categories[2].options[3];
</script>

{#snippet inputsLeft()}
  {#each userInputs as input}
    <div class="input-container">
      <p class="input-p">{input.name}</p>
      <input class="input" type="text" bind:value={input.value} />
    </div>
  {/each}
  {#each datePickers as datePicker}
    <div class="input-container">
      <p class="input-p mb-2">{datePicker.name}</p>
      <input type="date" bind:value={datePicker.value} class="input" />
    </div>
  {/each}
  {#each rangeSliders as rangeSlider, index}
    <div class="input-container">
      <p class="input-p">{rangeSlider.name}</p>
      <input
        class="range"
        type="range"
        min={rangeSlider.min}
        max={rangeSlider.max}
        placeholder={rangeSlider.placeholder}
        bind:value={rangeSlider.value}
      />
      <p class="text-gray-600 font-semibold">{rangeSlider.value}px</p>
    </div>
  {/each}
  {#each colorPickers as colorPicker}
    <div class="input-container">
      <p class="input-p">{colorPicker.name}</p>
      <input
        type="color"
        bind:value={colorPicker.value}
        class="rounded-2xl w-16 h-16"
      />
    </div>
  {/each}
  {#each categories as category}
    <div class="input-container">
      <p class="input-p mb-2">{category.name}</p>
      <select
        class="select bg-white text-black text-md font-semibold rounded-lg hover:ring-2 mb-2 w-52"
      >
        {#each category.options as option}
          <option class="option" value={option}>{option}</option>
        {/each}
      </select>
    </div>
  {/each}
{/snippet}

<div>
  <h1 class="text-4xl text-blue-600 font-semibold justify-center mt flex mb-4 mt-20">
    Create A Countdown Clock For Your Website
  </h1>
  <p class="justify-center flex text-gray-500 text-lg md:text-sm sm:text-xs">
    Create a beautiful event countdown, which can then be embedded in your
    website or share with friends.
  </p>
</div>

<!-- Adjusted the parent div to remove extra space -->
<div class="flex items-start justify-center">
  <div
    class="PanelContainer ring-2 ring-gray-200 rounded-md w-11/12 bg-white mt-10 relative h-full mb-10"
    style="
      box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);"
  >
    <!-- The card will be at the top center of the container -->
    <div
      id="card"
      class="flex justify-center text-2xl absolute top-10 left-1/2 transform -translate-x-1/2"
      style="width: {rangeSliders[1].value}px; height: {rangeSliders[2]
        .value}px; background-color: {colorPickers[1]
        .value}; border-radius: {rangeSliders[0]
        .value}px; color: {colorPickers[0].value}; font-size: {rangeSliders[3].value}px;"
    >
      <p class="mt-2">{userInputs[0].value}</p>
    </div>
    {@render inputsLeft()}
  </div>
</div>

<Footer />

<style>
  .input {
    @apply hover:ring-1 ring-gray-500 flex border-solid border-gray-400 border-[1px] px-5 py-2 rounded-lg font-bold;
  }
  .input-container {
    @apply py-4 px-7;
  }
  .range {
    @apply accent-gray-900 rounded-lg w-52;
  }
  .input-p {
    @apply text-lg font-semibold tracking-wider text-gray-800;
  }
  .option {
    @apply bg-white text-black;
  }
</style>
