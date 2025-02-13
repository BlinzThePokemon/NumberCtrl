<script>
    import { page } from "$app/stores";
 </script>
 
 <div class="holder">
    {#if $page.error?.message === "Not Found"}
       <h1 class="flex justify-center mt-20 text-5xl font-semibold">Error {$page.status}: Page not found.</h1>
       <p class="justify-center mt-10 flex text-xl">Please don't try again later.</p> <br><br>
       <h3 class="flex justify-center text-2xl">
          And while you're searching, try to find Error Page 403 and 405, I lost
          them in my basement.
       </h3>
       <br><br><br>
    {/if}
    <h4 class="text-3xl h-40 justify-center">Country Rooooaaaaddddsss Take me <a href="/">Home</a></h4>
 </div>
 
 
 <style>
    ::selection {
        background: orange;
    }
    a{
        text-decoration: underline;
        transition: all 200ms;
    
    &:hover{
        font-size: larger;
    }
    }
    .holder{
        text-align: center;
    }
    </style>