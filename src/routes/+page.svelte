<script> 
import img1 from '../img/icon-arrow.svg';

let old = false
let req = true
let yrs = new Date().getFullYear();
let month = 12;
let day = 30

let y;
let m;
let d;

const getdate =()=>{
   if(y =='' && m == '' && d == ''){
    old = false
    req = false
    return
   }else{
    old = true;
    y = (yrs - y);
    m = (month - m);
    d = (day - d);
   }
   setTimeout(()=>{
        old = false;
        req = true;
        y = '';
        m = '';
        d = '';
    },6000)
}
   
</script>


<div class="flex flex-col container mx-auto md:w-1/3 md:h-2/3 bg-white md:my-auto 
rounded-tl-xl rounded-tr-xl rounded-bl-xl rounded-br-3xl my-5 shadow-lg p-5 h-auto">
<div class="flex flex-col pt-2 m-5">
    <form class="flex flex-col  border-gray-600 space-x-10" on:click|preventDefault on:keydown>
     <div class="flex flex-row space-x-5 pt-2 pr-5">
        {#if req == false}
        <div class="flex flex-col w-24">
            <label for="day" class="text-left text-2xl pb-2 font-bold font-PoppinsBold">Day</label>
            <input type="number" class="p-2 rounded-md border border-red-600 font-bold font-PoppinsBold" required bind:value={d} placeholder="DD">
        </div>
        <div class="flex flex-col w-24">
            <label for="day" class="text-left text-2xl pb-2 font-bold font-PoppinsBold">Month</label>
            <input type="number" class="p-2 rounded-md border border-red-600 font-bold font-PoppinsBold" required bind:value={m} placeholder="MM">
        </div>
        <div class="flex flex-col w-24">
            <label for="day" class="text-left text-2xl pb-2 font-bold font-PoppinsBold">Year</label>
            <input type="number" class="p-2 rounded-md border border-red-600 font-bold font-PoppinsBold" required bind:value={y} placeholder="YY">
        </div>
         {:else} 
         <div class="flex flex-col w-24">
            <label for="day" class="text-left text-2xl pb-2 font-bold font-PoppinsBold">Day</label>
            <input type="number" class="p-2 text-gray-600 rounded-md border border-gray-600 font-bold font-PoppinsBold" required bind:value={d} placeholder="DD">
        </div>
        <div class="flex flex-col w-24">
            <label for="day" class="text-left text-2xl pb-2 font-bold font-PoppinsBold">Month</label>
            <input type="number" class="p-2 text-gray-600 rounded-md border border-gray-600 font-bold font-PoppinsBold" required bind:value={m} placeholder="MM">
        </div>
        <div class="flex flex-col w-24">
            <label for="day" class="text-left text-2xl pb-2 font-bold font-PoppinsBold">Year</label>
            <input type="number" class="p-2 text-gray-600 rounded-md border border-gray-600 font-bold font-PoppinsBold" required bind:value={y} placeholder="YY">
        </div>  
        {/if}
     </div>
     {#if req == false}
     <small class="flex text-red-600"> Fields are required </small>  
     {:else}
     <small class="hidden"> Fields are required </small>
     {/if}
     <div class="flex flex-col pt-10 relative pr-2">
        <p class="border-b-2 border-gray-700 relative -left-2"></p>
        <button class="bg-black rounded-full text-center p-6 h-20 w-20 absolute left-80 top-0" on:click|preventDefault={getdate} on:keydown>
            <img src="{img1}" alt="" srcset="">
        </button>
    </div>
    </form>
   {#if old == false}
   <div class="flex flex-col p-15 items-left">
    <h3 class="text-6xl font-bold font-PoppinsBold">...years</h3>
    <h3 class="text-6xl font-bold font-PoppinsBold">...months</h3>
    <h3 class="text-6xl font-bold font-PoppinsBold">...days</h3>
    </div>
    {:else}
    <div class="flex flex-col p-15 items-left">
        <h3 class="text-6xl font-bold font-PoppinsBold"><strong class="text-green-800">{y}</strong> years</h3>
        <h3 class="text-6xl font-bold font-PoppinsBold"><strong class="text-green-800">{m}</strong> months</h3>
        <h3 class="text-6xl font-bold font-PoppinsBold"><strong class="text-green-800">{d}</strong> days</h3>
    </div>
   {/if}
</div>
</div>