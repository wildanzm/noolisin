# Noolisin Project Documentation

## 1. Introduction

Noolisin is a web-based application designed to transform typed text into a simulated handwritten format on a digital piece of paper. This tool is particularly useful for users who prefer the aesthetic of handwritten notes but want the convenience of digital text input. The project is built with standard web technologies and is easy to set up and use.

## 2. Features

* **Text-to-Handwriting Conversion**: The core feature of Noolisin is its ability to take user-inputted text and render it on a digital paper background with a handwritten-style font.
* **Customizable Fields**: Users can input various details to personalize the output, including:
    * Name
    * Class/NIM
    * Subject
    * Date
    * Number
* **Font Selection**: The application provides a dropdown menu to choose from various handwriting fonts, allowing users to select the style that best suits their preference.
* **Real-time Canvas Preview**: As the user types, the text is dynamically drawn onto an HTML5 canvas, providing a real-time preview of the final output.
* **Downloadable Image**: Users can download the generated handwritten note as a PNG image file.
* **Responsive Design**: The user interface is designed to be responsive and works on different screen sizes.

## 3. Technologies Used

The Noolisin project is built using the following technologies:

* **HTML5**: For the basic structure and layout of the web page.
* **CSS3**: For styling the user interface, including the use of Bootstrap for a responsive layout.
* **JavaScript (ES6)**: For the core logic of the application, including handling user input, drawing on the canvas, and managing font selection.
* **p5.js**: A JavaScript library for creative coding, used here to manage the canvas and render the text with the selected fonts.
* **jQuery**: A popular JavaScript library used for DOM manipulation and event handling to enhance the user experience.
* **Bootstrap**: A front-end framework for creating responsive and visually appealing user interfaces.
* **Font Awesome**: For including scalable vector icons in the user interface.
* **ScrollReveal.js**: To add scroll animations to elements for a more dynamic user experience.
* **Waypoints.js & Counter-Up.js**: Used for creating animated counters that activate on scroll.

## 4. Project Structure

The project has a straightforward structure with the main files organized as follows:

* `index.html`: The main HTML file that contains the structure of the web page, including the input form and the canvas for displaying the handwritten text.
* `assets/`: This directory contains all the static assets for the project.
    * `css/`: Contains the stylesheets for the application, including Bootstrap, Font Awesome, and custom styles in `templatemo-lava.css`.
    * `js/`: Holds the JavaScript files, including jQuery, p5.js, and other plugins, as well as the custom application logic in `custom.js`.
    * `images/`: Stores images used in the application, such as background images and icons.
    * `fonts/`: Contains the font files used for the handwriting effect.

## 5. How It Works

The application's logic is primarily driven by JavaScript and the p5.js library:

1.  **User Input**: The user fills out the form fields in the `index.html` file. Each input field has an `oninput` event listener that updates a corresponding JavaScript variable (`txtName`, `txtClass`, etc.) in real-time.
2.  **Font Selection**: The user can select a font from the dropdown menu. The `onchange` event listener on the font selection dropdown updates the `fontIndex` in the browser's local storage and re-initializes the canvas with the new font.
3.  **Canvas Rendering**: The `setup()` function in the p5.js script initializes the canvas, loads the background image, and sets the default font. The `draw()` function is called repeatedly to render the text on the canvas. It clears the canvas and redraws the text from the input variables, creating a live preview.
4.  **Downloading the Image**: When the "Download" button is clicked, the `downloadCanvas()` function is triggered. This function converts the content of the canvas into a data URL and creates a temporary anchor (`<a>`) element with the `download` attribute set to the desired filename. It then programmatically clicks the link to initiate the download of the canvas as a PNG image.

## 6. Setup and Usage

To run the project locally, you can follow these steps:

1.  **Clone the Repository**:
    ```bash
    git clone [https://github.com/wildanzm/noolisin.git](https://github.com/wildanzm/noolisin.git)
    ```
2.  **Open `index.html`**:
    Navigate to the project directory and open the `index.html` file in a web browser.

No special server setup is required as the project is based on static files.

## 7. Customization

### Adding New Fonts

To add a new font, you need to:

1.  Place the font file (e.g., `.ttf` or `.otf`) in the `assets/fonts/` directory.
2.  Update the `fonts` array in the `index.html` file with the new font's information:
    ```javascript
    let fonts = [
        // ... existing fonts
        {
            'index': 8, // New index
            'name': 'Your New Font Name',
            'file': 'YourNewFont.ttf'
        }
    ];
    ```

### Changing the Paper Background

To change the paper background:

1.  Place the new background image in the `assets/images/` directory.
2.  In the `setup()` function of the p5.js script in `index.html`, change the path in the `loadImage()` function to your new image file:
    ```javascript
    bg = loadImage('/img/your-new-background.jpg');
    ```
Demo: https://noolisin.vercel.app
