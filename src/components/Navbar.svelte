<script>

  export let menu_open;

  let y = 0;

  $: scrolled = y > 100;

  function findPos(obj) {
    var curtop = 0;
    if (obj.offsetParent) {
        do {
            curtop += obj.offsetTop;
        } while (obj = obj.offsetParent);
    return [curtop];
    }
  }

  const handleCyclo = (e) => {
    e.preventDefault()
    let button = e.target.closest('[data-target]');
    let target = button.getAttribute('data-target');
    let offset = button.getAttribute('data-offset');
    
    window.scroll({
      left:0,
      top:findPos(document.getElementById(target))-offset, 
      behavior:'smooth'
    });

    
    
  }

</script>

<svelte:window bind:scrollY={y}/>

<div id="navbar" class=" sticky  space-x-4 md:space-x-0 min-h-fit w-screen sm:min-h-0  left-0 top-0 
    flex sm:items-center
     ease-in-out transition-all transform duration-300
     z-50 
     {scrolled?'bg-black':'bg-transparent'}
    ">
  
    <div class="w-full container mx-auto  flex justify-between px-4">
      <div class=" md:px-2 m-0 font-medium w-fit p-0 rounded-md flex items-center justify-center ">
       <a href="/" ><img src="/img/logo.svg" alt="logo" class=" md:h-24 h-16 "></a> 
      </div>

      <main class=" flex  items-start px-16 my-auto">
        
        <div class="flex bg-white my-auto spl_cursor  ">    
          <div on:click="{()=> menu_open = !menu_open }" class="z-50 spl_cursor md:pt-4 pt-1 my-auto  bg-black absolute cursor-pointer  md:top-5 top-2 md:right-8 right-4 w-10 h-10 md:text-xl text-xs ml-auto transition duration-150 hover:shadow py-1 border border-solid border-transparent rounded bg-transparent block outline-none focus:outline-none" type="button">
            <div class="block absolute w-6 h-0.5 rounded-sm bg-white top-5  duration-500 { menu_open ? 'opacity-0':'' }" ></div>
            <div class="block absolute w-6 h-0.5 rounded-sm bg-white top-6 duration-500 { menu_open ? 'transform rotate-45':'' }"></div>
            <div class="block absolute w-6 h-0.5 rounded-sm bg-white top-7 duration-500 { menu_open ? 'transform -rotate-45':'' }"></div>
            <div class="block absolute w-6 h-0.5 rounded-sm bg-white top-8 duration-500 { menu_open ? 'opacity-0':'' }" ></div>

            <!-- <span class="block absolute w-6 h-0.5 rounded-sm bg-white top0-3 duration-500 { menu_open ? 'opacity-0':'' }"></span> -->
          </div>
        </div>
      </main>
    </div>

</div>





<div id="navbar" class=" min-h-screen   h-20 p-8 sm:py-3 bg-black left-0 top-0 
    flex items-center
     ease-in-out transition-all transform duration-300
    -translate-x-full  fixed z-50 
     {menu_open?'translate-x-0':''}
    ">
  
    <div class="flex bg-white top-4 absolute spl_cursor">    
      <button on:click="{()=> menu_open = !menu_open }" class="z-50 spl_cursor bg-black cursor-pointer fixed right-5 w-10 h-10 text-xl ml-auto transition duration-150 hover:shadow leading-none px-2 py-1 border border-solid border-transparent rounded bg-transparent block outline-none focus:outline-none" type="button">
        <span class="block spl_cursor absolute w-6 h-1 rounded-sm bg-white top-3 duration-500 { menu_open ? 'opacity-0':'' }" ></span>
        <span class="block spl_cursor absolute w-6 h-1 rounded-sm bg-white duration-500 { menu_open ? 'transform rotate-45':'' }"></span>
        <span class="block spl_cursor absolute w-6 h-1 rounded-sm bg-white duration-500 { menu_open ? 'transform -rotate-45':'' }"></span>
        <span class="block spl_cursor absolute w-6 h-1 rounded-sm bg-white bottom-2.5 duration-500 { menu_open ? 'opacity-0':'' }"></span>
      </button>
    </div>
    


    <div class="w-fit container mx-auto sm:items-center sm:justify-between">
      <div class="mb-5 sm:m-0 font-medium sm:bg-transparent p-5 sm:p-0 rounded-md flex items-center justify-center">
       
        <img src="/img/logo.svg" alt="logo" class="h-14">
      </div>

      <nav>
        <ul class=" md:text-sm gap-2 font-data">
          <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100">
            <a href="/"  class="md:text-white text-white font-bold hover:text-black uppercase ">Home</a>
        </li>
          <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100 md:hidden flex">
            <a href="/#speakers" class="md:text-white text-white font-bold hover:text-black uppercase ">Speakers</a>
          </li>
          <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100 md:hidden flex">
              <a href="/#investors" data-target="investors" on:click={handleCyclo} data-offset="150" class="md:text-white text-white font-bold hover:text-black uppercase ">Investors</a>
            </li>
            <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100 md:hidden flex">
              <a href="/#mentors" data-target="mentors" on:click={handleCyclo} data-offset="150" class="md:text-white text-white font-bold hover:text-black uppercase ">Mentors</a>
            </li>

            <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100 md:hidden flex">
              <a href="/#agenda" data-target="agenda" on:click={handleCyclo} data-offset="150" class="md:text-white text-white font-bold hover:text-black uppercase ">Agenda</a>
            </li>

          <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100 md:hidden flex">
              <a href="/#tracks" class="md:text-white text-white font-bold hover:text-black uppercase ">Tracks</a>
          </li>

          <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100 md:hidden flex">
            <a href="/exhibitors" class="md:text-white text-white font-bold hover:text-black uppercase ">Exhibitors</a>
        </li>

          <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100">
              <a href="/nearby_attractions" target="_blank" class="md:text-white text-white font-bold hover:text-black uppercase">Nearby Attractions</a>
          </li>
          <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100">
              <a href="/2022" target="_blank" class="md:text-white text-white font-bold hover:text-black uppercase ">Previous Edition</a>
          </li>
         
         
          <li on:click="{()=> menu_open = !menu_open }" class="px-5 py-2 transform hover:bg-gray-400 transition duration-500 hover:scale-100">
               <a onclick="functionshow('pop_up')" class="md:text-white text-white font-bold hover:text-black uppercase ">SPONSORSHIP OPPORTUNITIES</a>
          </li>


        </ul>
      </nav>
    </div>


</div>
