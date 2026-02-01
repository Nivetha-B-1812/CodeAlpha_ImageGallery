<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Image Gallery</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background: #f4f4f4;
      text-align: center;
    }

    h1 {
      margin-bottom: 20px;
    }

    /* Filter buttons */
    .filters {
      margin-bottom: 20px;
    }

    .filters button {
      padding: 10px 15px;
      margin: 5px;
      border: none;
      background: #333;
      color: white;
      cursor: pointer;
      border-radius: 5px;
    }

    .filters button:hover {
      background: #555;
    }

    /* Gallery */
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
    }

    .gallery img {
      width: 100%;
      height: 200px;
      object-fit: cover;
      border-radius: 10px;
      cursor: pointer;
      transition: transform 0.3s, box-shadow 0.3s;
    }

    .gallery img:hover {
      transform: scale(1.05);
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
    }

    /* Lightbox */
    .lightbox {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.8);
      justify-content: center;
      align-items: center;
    }

    .lightbox img {
      max-width: 90%;
      max-height: 80%;
      border-radius: 10px;
    }

    .close {
      position: absolute;
      top: 20px;
      right: 30px;
      font-size: 30px;
      color: white;
      cursor: pointer;
    }

    /* Responsive */
    @media (max-width: 600px) {
      .gallery img {
        height: 150px;
      }
    }
  </style>
</head>
<body>

  <h1>Image Gallery</h1>

  <!-- Filter Buttons -->
  <div class="filters">
    <button onclick="filterImages('all')">All</button>
    <button onclick="filterImages('nature')">Nature</button>
    <button onclick="filterImages('animals')">Animals</button>
    <button onclick="filterImages('city')">City</button>
  </div>

  <!-- Gallery -->
  <div class="gallery">
    <img src="https://picsum.photos/id/1015/400/300" class="image nature" onclick="openLightbox(this)">
    <img src="https://picsum.photos/id/1025/400/300" class="image animals" onclick="openLightbox(this)">
    <img src="https://picsum.photos/id/1035/400/300" class="image city" onclick="openLightbox(this)">
    <img src="https://picsum.photos/id/1040/400/300" class="image nature" onclick="openLightbox(this)">
    <img src="https://picsum.photos/id/1062/400/300" class="image animals" onclick="openLightbox(this)">
    <img src="https://picsum.photos/id/1011/400/300" class="image city" onclick="openLightbox(this)">
  </div>

  <!-- Lightbox -->
  <div class="lightbox" id="lightbox">
    <span class="close" onclick="closeLightbox()">&times;</span>
    <img id="lightbox-img">
  </div>

  <script>
    function openLightbox(img) {
      document.getElementById("lightbox").style.display = "flex";
      document.getElementById("lightbox-img").src = img.src;
    }

    function closeLightbox() {
      document.getElementById("lightbox").style.display = "none";
    }

    function filterImages(category) {
      let images = document.getElementsByClassName("image");

      for (let i = 0; i < images.length; i++) {
        if (category === "all") {
          images[i].style.display = "block";
        } else {
          if (images[i].classList.contains(category)) {
            images[i].style.display = "block";
          } else {
            images[i].style.display = "none";
          }
        }
      }
    }
  </script>

</body>
</html>