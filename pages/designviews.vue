<template>
  <div class="bg-[#f6f7f9] flex-1">
    <div class="flex items-center justify-between bg-white p-6">
      <div class="text-2xl">
        设计视图
      </div>
      <div>
        <Button class="h-8">
          <RouterLink to="/upload" class="flex items-center text-xs font-normal">
            <span class="icon-[lucide--upload] mr-2" />上载新文件
          </RouterLink>
        </Button>
      </div>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 p-8">
      <ViewList v-for="i in 9" :key="i" />
    </div>
  </div>
</template>
