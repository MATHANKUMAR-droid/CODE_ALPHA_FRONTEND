# CODE_ALPHA_FRONTEND\
**#TASK 1 IMAGE GALLERY**
_________________________________________________________________________________________________________________________________________
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Gallery</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="gallery-container">
        <div class="gallery">
            <img src="image1.jpg" alt="Image 1" class="gallery-image">
            <img src="image2.jpg" alt="Image 2" class="gallery-image">
            <img src="image3.jpg" alt="Image 3" class="gallery-image">
            <!-- Add more images as needed -->
        </div>
        <button class="nav-button prev" onclick="prevImage()">Previous</button>
        <button class="nav-button next" onclick="nextImage()">Next</button>
    </div>
    <script src="script.js"></script>
</body>
</html>
__________________________________________________________________________________________________________________________________________body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background-color: #f0f0f0;
}

.gallery-container {
    position: relative;
    width: 80%;
    max-width: 800px;
    overflow: hidden;
    border: 2px solid #ccc;
    background-color: #fff;
}

.gallery {
    display: flex;
    transition: transform 0.5s ease;
}

.gallery-image {
    width: 100%;
    flex-shrink: 0;
}

.nav-button {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0, 0, 0, 0.5);
    color: #fff;
    border: none;
    padding: 10px;
    cursor: pointer;
    z-index: 10;
}

.prev {
    left: 10px;
}

.next {
    right: 10px;
}
__________________________________________________________________________________________________________________________________________let currentIndex = 0;

function showImage(index) {
    const gallery = document.querySelector('.gallery');
    const images = document.querySelectorAll('.gallery-image');
    const totalImages = images.length;

    if (index >= totalImages) {
        currentIndex = 0;
    } else if (index < 0) {
        currentIndex = totalImages - 1;
    } else {
        currentIndex = index;
    }

    const offset = -currentIndex * 100;
    gallery.style.transform = `translateX(${offset}%)`;
}

function nextImage() {
    showImage(currentIndex + 1);
}

function prevImage() {
    showImage(currentIndex - 1);
}

// Initialize gallery
showImage(currentIndex);
