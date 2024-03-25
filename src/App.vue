<template>
  <div>
    test
    <div class="p-4">
        <!-- tabs -->
        <div class="flex flex-wrap gap-4">
      <div class="py-4 px-6 bg-violet-500 text-white rounded-md" role="button">單人房</div>
      <div class="py-4 px-6 border-solid border-2 border-violet-500 text-violet-500 rounded-md" role="button">雙人房</div>
      <div class="py-4 px-6 border-solid border-2 border-violet-500 text-violet-500 rounded-md" role="button">四人房</div>
      <div class="py-4 px-6 border-solid border-2 border-violet-500 text-violet-500 rounded-md" role="button">海景房</div>
      <div class="py-4 px-6 border-solid border-2 border-violet-500 text-violet-500 rounded-md" role="button">山景房</div>
      <div class="py-4 px-6 border-solid border-2 border-violet-500 text-violet-500 rounded-md" role="button">市景房</div>
    
      </div>
    </div>
    <!-- block -->
    <section class="p-4">
     <div class="grid grid-cols-3 gap-4">
      <div class="shadow-xl rounded-md overflow-hidden">
        <img src="https://picsum.photos/id/557/500/500">
        <div class="flex flex-col p-4">
         <div class="flex justify-between mb-4">
            <span class="font-semibold text-slate-900 truncate dark:text-slate-100">海景雙人房</span>
            <span class="text-lg text-gray-500 font-medium">NT 120</span>
         </div>
         <button class="py-2 px-6 border-solid border-2 border-violet-500 text-violet-500 rounded-md">加入購物車</button>
        </div>
      </div>
     </div>
    </section>
  </div>
</template>



