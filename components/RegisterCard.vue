<template>
  <div class="mt-6">
    <p class="font-semibold text-[22px]">
      Masuk ke akun atau daftar untuk memesan
    </p>
    <div class="mt-6">
      <form>
        <div class="grid rounded-xl overflow-hidden border border-gray-300">
          <select class="outline-0 border-b border-gray-300 p-3">
            <option value="+62" class="p-3">Indonesia (+62)</option>
          </select>
          <div class="p-0.5 relative form-input group">
            <input
              class="outline-0 p-3 w-full focus:outline-1 focus:rounded-lg relative bg-transparent z-40"
            />
            <span
              class="absolute top-[50%] -translate-y-[50%] left-4 text-lg text-gray-500 z-30 group-hover:top-4 group-hover:text-sm transition-all ease"
              >Nomor Telepon</span
            >
          </div>
        </div>
      </form>
      <p class="text-xs text-gray-600 mt-1.5">
        <span
          >Kami akan menelepon atau mengirim SMS guna mengonfirmasikan nomor
          Anda. Tarif standar SMS dan data berlaku.
        </span>
        <span class="underline text-black font-semibold">
          Kebijakan Privasi</span
        >
      </p>
      <div class="mt-4 flex">
        <button class="w-full">
          <div
            class="w-full text-center py-3 bg-[#EF5A5F] hover:bg-[#FF5F5C] rounded-lg font-semibold text-white transition-all ease"
          >
            Lanjutkan
          </div>
        </button>
      </div>
      <div class="mt-5 flex gap-x-4 justify-between items-center">
        <span class="h-1 border-t w-full"></span>
        <span class="text-sm text-gray-600">atau</span>
        <span class="h-1 border-t w-full"></span>
      </div>
      <div class="mt-5 grid grid-cols-3 gap-5">
        <div
          class="py-4 hover:bg-gray-100 transition-all ease cursor-pointer text-center border border-black rounded-lg"
        >
          <svg
            class="mx-auto"
            viewBox="0 0 32 32"
            xmlns="http://www.w3.org/2000/svg"
            aria-hidden="true"
            role="presentation"
            focusable="false"
            style="display: block; height: 20px; width: 20px"
          >
            <path fill="#1877F2" d="M32 0v32H0V0z"></path>
            <path
              d="M22.938 16H18.5v-3.001c0-1.266.62-2.499 2.607-2.499h2.018V6.562s-1.831-.312-3.582-.312c-3.654 0-6.043 2.215-6.043 6.225V16H9.436v4.625H13.5V32h5V20.625h3.727l.71-4.625z"
              fill="#FFF"
            ></path>
          </svg>
        </div>
        <div
          class="py-4 hover:bg-gray-100 transition-all ease cursor-pointer text-center border border-black rounded-lg"
        >
          <svg
            class="mx-auto"
            viewBox="0 0 32 32"
            xmlns="http://www.w3.org/2000/svg"
            aria-hidden="true"
            role="presentation"
            focusable="false"
            style="display: block; height: 20px; width: 20px"
          >
            <g transform="translate(4.376957 4.073369)">
              <path
                d="m19.7480429 20.9266305c2.813-2.625 4.063-7 3.313-11.18799996h-11.188v4.62599996h6.375c-.25 1.5-1.125 2.75-2.375 3.562z"
                fill="#4285f4"
              ></path>
              <path
                d="m1.24804285 17.2396305c.82223 1.6196 2.0014 3.0314 3.4486 4.129s3.1247 1.8523 4.906 2.2073c1.78130005.355 3.62000005.301 5.37740005-.1579s3.3877-1.3108 4.768-2.4914l-3.875-3c-3.313 2.188-8.81300005 1.375-10.68800005-3.75z"
                fill="#34a853"
              ></path>
              <path
                d="m5.18573285 14.1766305c-.5-1.563-.5-3 0-4.56299996l-3.938-3.062c-1.438 2.875-1.875 6.93799996 0 10.68799996z"
                fill="#fbbc02"
              ></path>
              <path
                d="m5.18604285 9.61463054c1.374-4.31301 7.25000005-6.81301 11.18700005-3.126l3.438-3.37401c-4.875-4.688-14.37500005-4.5-18.56300005 3.43601l3.938 3.063z"
                fill="#ea4335"
              ></path>
            </g>
          </svg>
        </div>
        <div
          class="py-4 hover:bg-gray-100 transition-all ease cursor-pointer text-center border border-black rounded-lg"
        >
          <svg
            class="mx-auto"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
            role="presentation"
            aria-hidden="true"
            focusable="false"
            style="
              height: 20px;
              width: 20px;
              display: block;
              fill: currentcolor;
            "
          >
            <path
              d="m13.3 2.1a5.1 5.1 0 0 1 3.8-2.1 5.1 5.1 0 0 1 -1.2 3.8 4.1 4.1 0 0 1 -3.6 1.7 4.5 4.5 0 0 1 1-3.4zm-5 3.7c-2.8 0-5.8 2.5-5.8 7.3 0 4.9 3.5 10.9 6.3 10.9 1 0 2.5-1 4-1s2.6.9 4 .9c3.1 0 5.3-6.4 5.3-6.4a5.3 5.3 0 0 1 -3.2-4.9 5.2 5.2 0 0 1 2.6-4.5 5.4 5.4 0 0 0 -4.7-2.4c-2 0-3.5 1.1-4.3 1.1-.9 0-2.4-1-4.2-1z"
            ></path>
          </svg>
        </div>
        <div
          class="col-span-3 py-4 px-6 hover:bg-gray-100 transition-all ease cursor-pointer text-center border border-black rounded-lg flex justify-between"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 32 32"
            aria-hidden="true"
            role="presentation"
            focusable="false"
            style="
              display: block;
              height: 20px;
              width: 20px;
              fill: currentcolor;
            "
          >
            <path
              d="M30.5105,5.87921A5.06207,5.06207,0,0,0,26,3H6A5.06215,5.06215,0,0,0,1.48932,5.87946,4.9444,4.9444,0,0,0,1,8V24a5.00588,5.00588,0,0,0,5,5H26a5.00588,5.00588,0,0,0,5-5V8A4.94373,4.94373,0,0,0,30.5105,5.87921ZM6,5H26a2.97234,2.97234,0,0,1,1.77252.59253l-9.8194,8.41675a2.98373,2.98373,0,0,1-3.90527,0l-9.82013-8.417A2.97238,2.97238,0,0,1,6,5ZM29,24a3.00328,3.00328,0,0,1-3,3H6a3.00328,3.00328,0,0,1-3-3V8a2.96566,2.96566,0,0,1,.10266-.73773l9.64343,8.26556a4.97272,4.97272,0,0,0,6.50782,0L28.89728,7.262A2.96542,2.96542,0,0,1,29,8Z"
            ></path>
          </svg>
          <p>Lanjutkan dengan email</p>
          <p></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup></script>
