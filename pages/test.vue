<script setup>
const isMobile = ref()

const openApp = () => {
  navigator.getInstalledRelatedApps().then((relatedApps) => {
    for (let app of relatedApps) {
      console.log(app.platform)
      console.log(app.url)
      console.log(app.id)
    }
  })

  const regex = /Mobi|Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i
  isMobile.value = regex.test(navigator.userAgent)

  if (!isMobile.value) {
    alert('此裝置為電腦')
  } else {
    if (/android/i.test(navigator.userAgent)) {
      alert('此裝置為android')
    }

    if (/iPad|iPhone|iPod/.test(navigator.userAgent)) {
      // alert('此裝置為ipone')
      // 鏡好聽app store

      const isOpenApp = ref(false)

      const open1 = setTimeout(() => {
        window.location.replace('fb1://')
      }, 400)

      const open2 = setTimeout(() => {
        if (!isOpenApp.value) window.location.replace('https://apps.apple.com/us/app/id1457065131')
      }, 1500)

      document.addEventListener(
        'visibilitychange',
        () => {
          if (document.hidden) {
            isOpenApp.value = true
            clearTimeout(open1)
            clearTimeout(open2)
          }
        },
        false
      )

      // window.location.replace('https://apps.apple.com/us/app/id1457065131')
    }
  }
}
</script>

<template>
  <div @click="openApp">打開ＡＰＰ</div>
</template>
