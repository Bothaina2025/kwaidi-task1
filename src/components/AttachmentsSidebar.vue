<template>
    <div class="w-1/4 bg-white rounded-lg shadow p-4 fixed-right">
      <h3 class="text-xl font-semibold mb-6">Media (36)</h3>
      <div class="grid grid-cols-3  gap-1">
        <img
          v-for="img in  media  "
          :key="img.id"
          :src="img.src"
          class="w-16 h-16 rounded-lg object-cover"
        />
      </div>
       
     <div class="section">
       <h3>Files (36)</h3>
      <div class="file-list">
        <div class="file-item">
         <img src="@/image.png/pdf-icon.png" alt="PDF file" class="img">
         <p class="name">service-task.pdf</p>
         <span class="size-date">2 MB &bull; 2 Dec 2022</span>
        </div>

        <div class="file-item">
         <img src="@/image.png/fig-icon.png" alt="Figma file" class="img">
         <p class="name">homepage-design.fig</p>
         <span class="size-date">2 MB &bull; 2 Dec 2022</span>
        </div>

        <div class="file-item">
         <img src="@/image.png/html-icon.png" alt="HTML file" class="img">
         <p class="name">about-us.html</p>
         <span class="size-date">2 MB &bull; 2 Dec 2022</span>
        </div>

        <div class="file-item">
         <img src="@/image.png/zip-icon.png" alt="ZIP file" class="img">
         <p class="name">work-project.zip</p>
         <span class="size-date">2 MB &bull; 2 Dec 2022</span>
        </div>

        <div class="file-item">
         <img src="@/image.png/js-icon.png" alt="JavaScript file" class="img">
         <p class="name">custom.js</p>
         <span class="size-date">2 MB &bull; 2 Dec 2022</span>
        </div>
    </div>
  </div>
    </div>
</template>

<script>
  import media1 from '@/image.png/media1.jpg';
  import media2 from '@/image.png/media2.jpg';
  import media3 from '@/image.png/media3.jpg';
  import media4 from '@/image.png/media4.jpg';
  import media5 from '@/image.png/media1.jpg';
  import media6 from '@/image.png/media2.jpg';
  export default {
    data() {
      return {
        media: [
          { id: 1, src: media1 },
          { id: 2, src: media2 },
          { id: 3, src: media3 },
          { id: 4, src: media4 },
          { id: 5, src: media5 },
          { id: 6, src: media6 }
        ],
      };
    }
  };
</script>

<style scoped>

  .fixed-right {
  position: absolute; 
  width: 300px;
  height:783px ;
  top: 77%; 
  right: -30px; 
  transform: translateY(-50%);

}
.image-file,img{
  width: 35px;
  height: 35px; 
  border-radius: 11px;
  margin-right: 10px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); 
  gap: 10px;
}

  .container {
    width: 250px;
    background: white;
    padding: 10px;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgb(255, 255, 255);
    
  }
  .section {
    font-family: Arial, sans-serif;
    padding:4px;
    
  }
  h3 {
    font-size: 14px;
    font-weight: bold;
    margin-bottom: 10px;
    color: #000;
  }
  .media-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 9px;
  }
  
    .img {
     width: 40px;
     height: 40px;
     background-color: #f1f1f1;
     border-radius: 8px;
     padding: 4px;
    }

    .name {
        font-weight:bold;
        font-size:12px;
        color: #333;
        flex-grow:1;
    }
    .size-date {
        color: #999;
        font-size: 12px;
    }
    h3 {
        color: #000000;
        font-size: 16px;
        font-weight: normal;
    }
 .grid img {
  width: 60px; 
  height: 50px;
 }

  .file-list {
    display: flex;
    flex-direction: column;
  }
  .file-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 7px 1px;
  }
  .file-info {
    font-size: 106px;
  }
  .file-name {
    font-weight:lighter;
  }
</style>