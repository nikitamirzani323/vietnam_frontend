<script>
    import { link } from "svelte-spa-router";
    let lang = localStorage.getItem("lang");
    if(lang == null){
      localStorage.setItem("lang", "vietnam");
    }
    let content_text_1 = "";
    let content_text_2 = "";
    let content_text_3 = "";
    let content_text_4 = "";
    let content_text_5 = "";
    if(lang == null || lang == "english"){
        content_text_1 = "HOME";
        content_text_2 = "RESULT";
        content_text_3 = "PAYMENT";
        content_text_4 = "RESPONSIBILITY";
        content_text_5 = "ABOUT";
    }else{
        content_text_1 = "TRANG CHỦ";
        content_text_2 = "KẾT QUẢ HỒ BƠI";
        content_text_3 = "CÁCH CHƠI";
        content_text_4 = "CHƠI CÓ TRÁCH NHIỆM";
        content_text_5 = "VỀ CHÚNG TÔI";
    }
    const changeCountry = (e) => {
      localStorage.setItem("lang", e);
      window.location.href = "/";
    };
</script>
<main class="w-full max-w-6xl mx-auto">
  <div class="lg:flex justify-end gap-1 hidden">
    <img on:click={() => {
          changeCountry("vietnam");
      }} class="cursor-pointer mt-1" src="http://lottery-vietnam.com/en/images/vie.jpg" alt="">
    <img on:click={() => {
          changeCountry("english");
      }} class="cursor-pointer mt-1" src="http://lottery-vietnam.com/en/images/en.jpg" alt="">
  </div>
  <nav class="navbar  w-full bg-black lg:bg-transparent">
    <div class="flex-1 w-full">
      <a class="btn btn-ghost  normal-case text-xl text-center" use:link href="/">
        <img class="w-[100px] lg:w-[250px] lg:-mt-8" src="images/logocombine.png" alt="Hải Phòng Lottery">
      </a>
    </div>
    <div class="flex-none ">
      <ul class="hidden lg:menu lg:menu-horizontal p-0">
        <li><a class="text-sm  hover:bg-transparent focus:bg-transparent"use:link href="/">
          <span class="text-[#7ea8da]">{content_text_1}</span>
        </a></li>
        <li><a class="text-sm hover:bg-transparent focus:bg-transparent"use:link href="/result">
          <span class="text-[#7ea8da]">{content_text_2}</span>
        </a></li>
        <li><a class="text-sm hover:bg-transparent focus:bg-transparent"use:link href="/">
          <span class="text-[#7ea8da]">{content_text_3}</span>
        </a></li>
        <li><a class="text-sm hover:bg-transparent focus:bg-transparent"use:link href="/">
          <span class="text-[#7ea8da]">{content_text_4}</span>
        </a></li>
        <li><a class="text-sm hover:bg-transparent focus:bg-transparent"use:link href="/">
          <span class="text-[#7ea8da]">{content_text_5}</span>
        </a></li>
      </ul>
    </div>
    <div class="dropdown dropdown-end lg:hidden">
      <label tabindex="0" class="btn btn-ghost btn-circle">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 bg-white" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h7" /></svg>
      </label>
      <ul tabindex="0" class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-content rounded-box w-52">
        <li><a class="text-xs text-white font-bold hover:bg-transparent focus:bg-transparent"use:link href="/">{content_text_1}</a></li>
        <li><a class="text-xs text-white font-bold hover:bg-transparent focus:bg-transparent"use:link href="/result">{content_text_2}</a></li>
        <li><a class="text-xs text-white font-bold hover:bg-transparent focus:bg-transparent"use:link href="/">{content_text_3}</a></li>
        <li><a class="text-xs text-white font-bold hover:bg-transparent focus:bg-transparent"use:link href="/">{content_text_4}</a></li>
        <li><a class="text-xs text-white font-bold hover:bg-transparent focus:bg-transparent"use:link href="/">{content_text_5}</a></li>
      </ul>
    </div>
  </nav>
</main>