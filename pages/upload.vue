<script setup>
const statusJson = reactive({
  waiting: {
    text: '上传新文件',
    subText: '',
  },
  selected: {
    text: '已选择文件',
    subText: '',
  },
  uploading: {
    text: '上传中',
    subText: '请勿关闭此页面',
  },
  uploaded: {
    text: '正在处理',
    subText: '这可能需要一些时间',
  },
  success: {
    text: '上传成功',
    subText: '点击查看',
  },
  error: {
    text: '上传失败',
    subText: '点击重新上传',
  },
})
const status = ref('uploaded')
const selectedFile = ref(null)

function handleFileChange(event) {
  selectedFile.value = event.target.files[0]
}

function uploadFile() {
  if (!selectedFile.value)
    return

  const formData = new FormData()
  formData.append('file', selectedFile.value)

  // 替换为你的上传 API
  fetch('YOUR_UPLOAD_API_URL', {
    method: 'POST',
    body: formData,
  })
    .then(response => response.json())
    .then((data) => {
      console.log('文件上传成功:', data)
    })
    .catch((error) => {
      console.error('文件上传失败:', error)
    })
}
</script>

<template>
  <div class="flex flex-1 flex-col">
    <div class="text-center p-8">
      <div class="text-3xl">
        {{ statusJson[status].text }}
      </div>
      <div class="text-gray-500 mt-3">
        {{ statusJson[status].subText }}
      </div>
    </div>

    <div class="flex flex-col flex-1 items-center mt-40">
      <template v-if="status === 'waiting'">
        <div class="flex flex-col items-center border-dashed border p-8 rounded hover:border-sky-500 bg-stone-100/40 w-full max-w-[700px] mx-5 relative cursor-pointer">
          <span class="icon-[lucide--package-open] text-5xl text-sky-500" />
          <div class="py-4">
            点击或拖拽上传
          </div>
          <input type="file" class="absolute top-0 left-0 w-full h-full opacity-0 cursor-pointer" @change="handleFileChange">
        </div>
        <div class="text-center mt-10">
          <div class="text-xs mb-1">
            支持大多数二维和三维格式
          </div>
          <div class="text-xs text-sky-500 cursor-pointer">
            查看所有支持的格式
          </div>
        </div>
      </template>

      <template v-if="status === 'selected'">
        <div>
          <Button class="h-8 font-normal px-10">
            确定上传
          </Button>
        </div>
      </template>

      <template v-if="status === 'uploading'">
        <div class="flex flex-col items-center justify-center h-72 w-72 relative">
          <span class="icon-[lucide--file-box] text-7xl" />
          <div class="py-2">
            炬光暖通20140119.rvt
          </div>
          <div class="text-sky-500 font-bold mt-1">
            26%
          </div>
          <div class="animate-spin absolute top-0 left-0 w-full h-full border-4 border-t-sky-500 rounded-full" />
        </div>
      </template>

      <template v-if="status === 'uploaded'">
        <div class="flex flex-col items-center justify-center h-72 w-72 relative">
          <span class="icon-[lucide--file-box] text-7xl mb-2" />
          <div class="text-sky-500 font-bold mt-1">
            正在处理...
            26%
          </div>
          <div class="animate-spin absolute top-0 left-0 w-full h-full border-4 border-t-sky-500 rounded-full" />
        </div>
        <div class="text-center mt-10 text-xs w-80">
          不想等待？我们会在您的文件准备就绪后通过电子邮件向您发送一个链接。
        </div>
      </template>
    </div>
  </div>
</template>
