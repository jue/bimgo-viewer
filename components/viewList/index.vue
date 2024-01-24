<template>
  <div class="bg-white shadow h-36 flex space-x-3 rounded">
    <img src="https://filecdn.jue.sh/image/bimgosoft/imgs/tmp/24.png" class="shrink-0 h-36 w-36">
    <div class="py-5 flex-1">
      <div class="font-bold mb-1">
        杨凌-图文综合楼
      </div>
      <div class="text-[11px] text-[#4a555b]">
        已上传 十二月 19, 2023
      </div>
    </div>
    <div class="p-5">
      <DropdownMenu>
        <DropdownMenuTrigger>
          <span
            class="icon-[lucide--more-vertical] hover:text-sky-600 text-base"
          />
        </DropdownMenuTrigger>
        <DropdownMenuContent>
          <DropdownMenuItem class="text-xs">
            <span class="icon-[lucide--share-2] mr-2" />分享
          </DropdownMenuItem>
          <DropdownMenuItem class="text-xs text-red-600">
            <span class="icon-[lucide--trash-2] mr-2" />删除
          </DropdownMenuItem>
        </DropdownMenuContent>
      </DropdownMenu>
    </div>
  </div>
</template>
