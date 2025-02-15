<script>
  import { goto } from "$app/navigation"
  // Keep the same URL as the original anchor tag
  let url = "";
  let countdownUUID;

  function navigateToCountdown() {
      countdownUUID = self.crypto.randomUUID()
      url = "/Pagecountdown/" + countdownUUID;
      goto(url)
  }
</script>

<main>
  <div>
    <h1 class="text-4xl font-semibold justify-center mt flex mb-4 mt-20">
      Page Countdowns
    </h1>
    <p class="justify-center flex text-gray-500 text-lg md:text-sm sm:text-xs">
      Create full-page countdowns which can then be shared with friends or shown
      on your website
    </p>
    <div class="flex justify-center max-w-full new-t">
      <button
        on:click={navigateToCountdown}
        class="flex justify-center bg-blue-500 rounded-md h-12 items-center font-bold text-white mt-5 w-48 transition delay-100 duration-200 hover:bg-blue-400"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 20 20"
          class="w-6 mr-2"
        >
          <path
            fill="currentColor"
            fill-rule="evenodd"
            d="M11 9V5H9v4H5v2h4v4h2v-4h4V9h-4zm-1 11a10 10 0 100-20 10 10 0 000 20zm0-2a8 8 0 100-16 8 8 0 000 16z"
          ></path>
        </svg>
        New Countdown
      </button>
    </div>
  </div>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap");

  .new-t {
    font-family: "Nunito", serif;
    font-optical-sizing: auto;
    font-weight: bold;
    font-style: normal;
    user-select: none;
  }
</style>
