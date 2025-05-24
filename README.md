# Ex05 Image Carousel
## Date:24/5/2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
# App.js
```
import React, { useState, useEffect } from 'react';
import './App.css';
import img1 from './assets/img1.png';
import img2 from './assets/img2.png';
import img3 from './assets/img3.png';

const images = [img1, img2, img3];


function App() {

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(() => {
      nextImage();
    }, 3000);
    return () => clearInterval(interval);
  });

  return (
    <div className="carousel-container">
      <h1>Image Carousel</h1>
      <div className="carousel">
        <button onClick={prevImage} className="nav-btn">‹</button>
        <img src={images[currentIndex]} alt={`Slide ${currentIndex + 1}`} />
        <button onClick={nextImage} className="nav-btn">›</button>
      </div>
      <div className="indicators">
        {images.map((_, index) => (
          <span
            key={index}
            className={`dot ${index === currentIndex ? 'active' : ''}`}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
      <footer className="footer">
        <p>Dhareene R K (212222040035)</p>
      </footer>
    </div>
  );
}

export default App;

```

# App.css
```
body {
  margin: 0;
  font-family: 'Courier New', Courier, monospace;
  background-color: #1a1a1a;  /* dark background */
  color: #e6e6e6;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  flex-direction: column;
}

.carousel-container {
  background: #2b0000; /* deep red background */
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 20px 5px #ff0000cc; /* red glow */
  text-align: center;
  max-width: 850px;
  width: 90%;
  border: 3px solid #ff0000; /* red border */
}

h1 {
  margin-bottom: 20px;
  color: #ff0000;
  font-weight: 900;
  letter-spacing: 2px;
  text-transform: uppercase;
  text-shadow: 2px 2px 4px #660000;
}

.carousel {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

.carousel img {
  width: 100%;
  max-width: 800px;
  height: 450px;
  object-fit: cover;
  border-radius: 10px;
  box-shadow: 0 0 15px #ff0000aa;
  transition: all 0.5s ease;
  border: 4px solid #b30000;
}

.nav-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  font-size: 3rem;
  background-color: #660000;
  color: #ff0000;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  cursor: pointer;
  z-index: 1;
  transition: background-color 0.3s ease, color 0.3s ease;
  box-shadow: 0 0 10px #ff0000cc;
}

.nav-btn:hover {
  background-color: #ff0000;
  color: #fff;
}

.nav-btn:first-of-type {
  left: 10px;
}

.nav-btn:last-of-type {
  right: 10px;
}

.indicators {
  margin-top: 15px;
}

.dot {
  height: 14px;
  width: 14px;
  margin: 0 6px;
  background-color: #660000;
  border-radius: 50%;
  display: inline-block;
  cursor: pointer;
  transition: background 0.3s ease;
  box-shadow: 0 0 6px #b30000;
}

.dot.active {
  background-color: #ff0000;
  box-shadow: 0 0 12px #ff4d4d;
}

.footer {
  margin-top: 30px;
  padding-top: 10px;
  font-size: 0.9rem;
  color: #999;
  border-top: 1px solid #440000;
  font-style: italic;
  letter-spacing: 1px;
}

```

## OUTPUT
![web ex5 1](https://github.com/user-attachments/assets/3bb1d2d4-ff1f-439f-861a-f5b90e8d41da)
![web ex5 2](https://github.com/user-attachments/assets/02a9a7e5-a2a9-43aa-b6cd-1623c1cec877)
![web ex5 3](https://github.com/user-attachments/assets/2791703d-12d4-41d9-b358-16d19c6437c9)



## RESULT
The program for creating Image Carousel using React is executed successfully.
