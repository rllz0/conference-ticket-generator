# Frontend Mentor - Conference Ticket Generator Solution

This is a solution to the [Conference Ticket Generator challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/conference-ticket-generator-LS8J-j4NY6). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of Contents

- [Frontend Mentor - Conference Ticket Generator Solution](#frontend-mentor---conference-ticket-generator-solution)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
    - [The Challenge](#the-challenge)
    - [Screenshot](#screenshot)
    - [Links](#links)
  - [My Process](#my-process)
    - [Built With](#built-with)
    - [What I Learned](#what-i-learned)
      - [Custom File Upload with Drag and Drop](#custom-file-upload-with-drag-and-drop)
      - [File Size Validation](#file-size-validation)
      - [Real-time Form Validation](#real-time-form-validation)
      - [Dynamic UI Updates](#dynamic-ui-updates)
      - [Complex Background Layering](#complex-background-layering)
      - [Responsive Design Across Devices](#responsive-design-across-devices)
      - [Dynamic Ticket Generation](#dynamic-ticket-generation)
    - [Continued Development](#continued-development)
  - [Author](#author)

## Overview

### The Challenge

Users should be able to:

- Upload an avatar image with drag-and-drop functionality and file size validation
- Complete a form with personal details (name, email, GitHub username)
- Receive form validation messages for any required fields
- Generate a personalized conference ticket upon successful form submission
- View the optimal layout for the interface depending on their device's screen size
- See hover and focus states for all interactive elements on the page

### Screenshot

![Conference Ticket Generator Screenshot](./Frontend%20Mentor%20|%20Conference%20Ticket%20Generator.png)

*Add your screenshot here when ready*

### Links

- Solution URL: [Add your solution URL here](https://github.com/rllz0/conference-ticket-generator.git)
- Live Site URL: [Add your live site URL here](https://rllz0.github.io/conference-ticket-generator/)

## My Process

### Built With

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Vanilla JavaScript
- Responsive design for mobile, tablet, and desktop
- Custom file upload with drag and drop functionality
- Dynamic content generation for the ticket

### What I Learned

This project provided valuable experience in several areas:

#### Custom File Upload with Drag and Drop

Creating an intuitive file upload interface with drag and drop functionality and file size validation:

```javascript
// Handle drag and drop events
label.addEventListener("dragover", (e) => {
  e.preventDefault();
  label.classList.add("dragOver");
});

label.addEventListener("dragleave", (e) => {
  e.preventDefault();
  label.classList.remove("dragOver");
});

label.addEventListener("drop", (e) => {
  e.preventDefault();
  label.classList.remove("dragOver");
  const file = e.dataTransfer.files[0];
  checkFileSize(file); // Validate file size
});
```

#### File Size Validation

Implementing file size validation to ensure uploaded images meet requirements:

```javascript
// File size limit (500 KB)
const FILE_SIZE_LIMIT = 500 * 1024;

// Function to check file size and display the image
function checkFileSize(file) {
  if (!file) return;

  if (file.size > FILE_SIZE_LIMIT) {
    // Show error if file size exceeds limit
    sizeWarning.style.display = "none";
    fileError.style.display = "block";
    btnContainer.style.display = "none";
    dragText.style.display = "block";
    return;
  }
  
  // Preview the uploaded image
  const reader = new FileReader();
  reader.readAsDataURL(file);
  reader.onload = () => {
    uploadedImg.src = reader.result;
    avatar.src = reader.result;
    uploadedImg.style.display = "block";
    uploadIcon.style.display = "none";
    btnContainer.style.display = "block";
    dragText.style.display = "none";
  };
}
```

#### Real-time Form Validation

Implementing real-time validation to provide immediate feedback:

```javascript
// Real-time validation for Email
email.addEventListener("input", () => {
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (emailRegex.test(email.value.trim())) {
    errorWarning[1].style.display = "none";
    email.style.border = "2px solid var(--Neutral-700)";
    emailVal.textContent = email.value;
  }
});
```

#### Dynamic UI Updates

Creating a dynamic UI that updates in real-time as users interact with the form:

```css
.nameValue {
  background: var(--Gradient-text);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
```

```javascript
fullName.addEventListener("input", () => {
  if (fullName.value.trim() !== "") {
    errorWarning[0].style.display = "none";
    fullName.style.border = "2px solid var(--Neutral-700)";
    username.textContent = fullName.value;
    nameVal.textContent = fullName.value;
  }
});
```

#### Complex Background Layering

Creating a visually appealing UI with multiple background layers:

```css
body {
  background-image: url("./assets/images/pattern-lines.svg"),
    url("./assets/images/pattern-circle.svg"),
    url("./assets/images/pattern-squiggly-line-top.svg"),
    url("./assets/images/pattern-squiggly-line-bottom-desktop.svg"),
    url("./assets/images/background-desktop.png");
  background-repeat: no-repeat;
  background-position: center, bottom right 20%, top right, bottom left, center;
  background-size: cover, 20%, 30%, 50%, cover;
  background-attachment: fixed;
}
```

#### Responsive Design Across Devices

Implementing a responsive design that adapts to different screen sizes:

```css
@media (max-width: 639px) {
  body {
    background-image: url("./assets/images/pattern-lines.svg"),
      url("./assets/images/pattern-circle.svg"),
      url("./assets/images/pattern-squiggly-line-top.svg"),
      url("./assets/images/pattern-squiggly-line-bottom.svg"),
      url("./assets/images/background-mobile.png");
    padding-top: 2rem;

    main {
      width: 100%;
      padding: 1rem;

      .first-section {
        h1 {
          margin: 0;
          font-size: 2rem;
          margin-bottom: 1rem;
        }
      }
    }
  }
}
```

#### Dynamic Ticket Generation

Creating a personalized conference ticket with user data and a randomly generated ticket number:

```javascript
// Generate random ticket number
ticketNumber.textContent = "#" + Math.floor(Math.random() * 100000);

// Set current date
const currentDate = new Date();
const options = { month: 'short', day: 'numeric', year: 'numeric' };
timeValue.textContent = currentDate.toLocaleDateString('en-US', options);
```

### Continued Development

Areas I want to focus on in future projects include:

- Enhancing accessibility features to ensure the application is usable by everyone
- Adding animation effects for smoother transitions between form and ticket views
- Implementing actual server-side functionality to store ticket information
- Adding the ability to download or share the generated ticket
- Enhancing the drag and drop functionality with progress indicators
- Adding more robust image processing capabilities
## Author

