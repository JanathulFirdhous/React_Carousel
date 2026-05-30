# Ex05 Image Carousel
## Date: 30/05/2026
## NAME: JANATHUL FIRDHOUS A
## REG NO:212224040129

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
## app.css
```
body {
  margin: 0;
  font-family: "Poppins", sans-serif;
  background: linear-gradient(135deg, #ffd6e8, #d6e4ff);
}

.container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: #5a4b81;
}

.carousel-image {
  width: 550px;
  height: 330px;
  object-fit: cover;
  border-radius: 25px;
  border: 5px solid white;
  box-shadow: 0px 8px 25px rgba(0, 0, 0, 0.15);
}

h1 {
  color: #7b68ee;
  margin-bottom: 20px;
  font-size: 36px;
}

h3 {
  color: #6a5acd;
  margin-top: 15px;
  font-size: 24px;
}

.buttons {
  margin-top: 20px;
}

.buttons button {
  margin: 10px;
  padding: 12px 30px;
  border: none;
  border-radius: 30px;
  background: #cdb4db;
  color: white;
  font-size: 17px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
}

.buttons button:hover {
  background: #b185db;
  transform: scale(1.08);
}

.dots {
  margin-top: 20px;
}

.dot {
  height: 15px;
  width: 15px;
  margin: 5px;
  background-color: #e0c3fc;
  border-radius: 50%;
  display: inline-block;
  transition: 0.3s;
}

.active {
  background-color: #9d4edd;
  transform: scale(1.3);
}
```

## app.jsx
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const places = [
    {
      url: "https://images.unsplash.com/photo-1519046904884-53103b34b206?w=1200",
      name: "Sunny Beach",
    },
    {
      url: "https://images.unsplash.com/photo-1501785888041-af3ef285b470?w=1200",
      name: "Mountain View",
    },
    {
      url: "https://images.unsplash.com/photo-1441974231531-c6227db76b6e?w=1200",
      name: "Forest Path",
    },
    {
      url: "https://images.unsplash.com/photo-1511497584788-876760111969?w=1200",
      name: "City Lights",
    },
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % places.length);
  };

  const prevImage = () => {
    setCurrentIndex(
      (currentIndex - 1 + places.length) % places.length
    );
  };

  return (
    <div className="container">
      <h1>🌸 Nature Image Carousel 🌸</h1>

      <img
        src={places[currentIndex].url}
        alt={places[currentIndex].name}
        className="carousel-image"
      />

      <h3>{places[currentIndex].name}</h3>

      <div className="buttons">
        <button onClick={prevImage}>⬅ Previous</button>
        <button onClick={nextImage}>Next ➡</button>
      </div>

      <div className="dots">
        {places.map((_, index) => (
          <span
            key={index}
            className={
              index === currentIndex
                ? "dot active"
                : "dot"
            }
          ></span>
        ))}
      </div>
    </div>
  );
}

export default App;
```


## OUTPUT
<img width="1919" height="1066" alt="image" src="https://github.com/user-attachments/assets/3d863986-982b-42a5-9902-09a6af02f5da" />

<img width="1919" height="1064" alt="image" src="https://github.com/user-attachments/assets/7271f7da-d5f4-4fc6-af2d-77df8bafa235" />

<img width="1919" height="1070" alt="image" src="https://github.com/user-attachments/assets/d8a86b95-4216-4fee-83b2-af6ecba0bc65" />

<img width="1919" height="1073" alt="image" src="https://github.com/user-attachments/assets/7845f8c0-2bfe-4d83-b76f-262062d58b22" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
