# Introduction to JavaScript and DOM Manipulation

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive DOM Demo</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1 id="main-heading">DOM Manipulation Demo</h1>
    </header>

    <main>
        <section class="content-section">
            <p id="dynamic-text">This text will change when you click the button below.</p>
            <button id="text-changer" class="btn">Change Text</button>
        </section>

        <section class="content-section">
            <div id="style-box" class="box">This box will change style</div>
            <button id="style-changer" class="btn">Toggle Style</button>
        </section>

        <section class="content-section">
            <div id="element-container">
                <p>Watch elements appear/disappear below:</p>
            </div>
            <button id="element-toggler" class="btn">Toggle Element</button>
        </section>
    </main>

    <footer>
        <p>Open the console to see JavaScript events!</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>

style.css

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
}

.content-section {
    margin: 30px 0;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 5px;
}

.btn {
    padding: 10px 15px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
}

.btn:hover {
    background-color: #45a049;
}

.box {
    padding: 20px;
    background-color: #f4f4f4;
    border: 1px solid #ccc;
    margin: 15px 0;
    transition: all 0.3s ease;
}

.highlight {
    background-color: #ffeb3b;
    border: 2px solid #ffc107;
    transform: scale(1.05);
}

.hidden {
    display: none;
}



script.js
// 1. Change Text Content Dynamically
const textChangerBtn = document.getElementById('text-changer');
const dynamicText = document.getElementById('dynamic-text');

textChangerBtn.addEventListener('click', () => {
    dynamicText.textContent = "Text successfully changed using JavaScript!";
    console.log("Text content updated");
});

// 2. Modify CSS Styles via JavaScript
const styleChangerBtn = document.getElementById('style-changer');
const styleBox = document.getElementById('style-box');
let isHighlighted = false;

styleChangerBtn.addEventListener('click', () => {
    isHighlighted = !isHighlighted;
    
    if (isHighlighted) {
        styleBox.classList.add('highlight');
        console.log("Styles applied");
    } else {
        styleBox.classList.remove('highlight');
        console.log("Styles removed");
    }
});

// 3. Add/Remove Element on Button Click
const elementTogglerBtn = document.getElementById('element-toggler');
const elementContainer = document.getElementById('element-container');
let demoElementExists = false;
let demoElement = null;

elementTogglerBtn.addEventListener('click', () => {
    if (!demoElementExists) {
        // Create new element
        demoElement = document.createElement('div');
        demoElement.className = 'box';
        demoElement.textContent = 'I am a dynamically created element!';
        demoElement.id = 'demo-element';
        elementContainer.appendChild(demoElement);
        demoElementExists = true;
        console.log("Element added to DOM");
    } else {
        // Remove existing element
        elementContainer.removeChild(demoElement);
        demoElementExists = false;
        console.log("Element removed from DOM");
    }
});
