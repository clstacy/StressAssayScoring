# Image Scoring App for Yeast Growth

Welcome to the **Stress Assay Scorer**, an interactive, browser-based tool designed for scientific research involving image analysis and scoring. This application allows users to upload images, assign scores based on custom criteria, and export the results for further analysis. It runs entirely in your web browser, requiring no server-side processing or additional software installations.

To use this tool now, visit: [https://clstacy.github.io/StressAssayScoring](https://clstacy.github.io/StressAssayScoring/)
---

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Deployment](#deployment)
- [Usage Instructions](#usage-instructions)
  - [1. Upload Images](#1-upload-images)
  - [2. Set Custom Scores (Optional)](#2-set-custom-scores-optional)
  - [3. Set Default Score (Optional)](#3-set-default-score-optional)
  - [4. Set Replication Factor (Optional)](#4-set-replication-factor-optional)
  - [5. Enable Pagination (Optional)](#5-enable-pagination-optional)
  - [6. Load Images](#6-load-images)
  - [7. Assign Scores to Images](#7-assign-scores-to-images)
  - [8. Navigate Between Pages](#8-navigate-between-pages)
  - [9. Download Scores](#9-download-scores)
- [Features Explanation](#features-explanation)
  - [Randomization](#randomization)
  - [Replication for Consistency Checks](#replication-for-consistency-checks)
  - [Blinding Image Names](#blinding-image-names)
  - [Color-Coded Scores](#color-coded-scores)
  - [Default Score](#default-score)
  - [Pagination](#pagination)
  - [Consistency Checks](#consistency-checks)
  - [Comprehensive Data Export](#comprehensive-data-export)
- [Technical Details](#technical-details)
- [Browser Compatibility](#browser-compatibility)
- [Privacy and Security](#privacy-and-security)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- **User-Friendly Interface**: Intuitive design for easy navigation and scoring.
- **Custom Scoring**: Define your own scoring criteria and labels.
- **Randomization**: Images are displayed in random order to prevent bias.
- **Replication**: Include replicated images to assess intra-observer reliability.
- **Blinding**: Image filenames are anonymized to prevent bias.
- **Color-Coded Scores**: Assign unique colors to scores for quick visual identification.
- **Default Score**: Set a default score to be assigned automatically to all images.
- **Pagination**: Optionally enable pagination and specify the number of images per page.
- **Consistency Checks**: Detect and alert inconsistencies in replicated image scoring.
- **Data Export**: Download scoring results as a CSV file with comprehensive data.

---

## Getting Started

### Prerequisites

- A modern web browser (Google Chrome, Mozilla Firefox, Microsoft Edge, Safari).
- No additional software installations are required.

### Deployment

The app is a static HTML file and can be run locally or hosted online.

#### Running Locally

1. **Download the Repository**:
   - Clone the repository or download the ZIP file and extract it to a folder on your computer.

2. **Open the App**:
   - Open the `index.html` file in your preferred web browser.

#### Hosting Online (GitHub Pages)

1. **Fork or Clone the Repository**:
   - Fork this repository to your GitHub account or clone it.

2. **Enable GitHub Pages**:
   - Go to the repository settings.
   - Scroll down to the "GitHub Pages" section.
   - Under "Source," select the `main` branch and click "Save."

3. **Access the App**:
   - The app will be available at `https://<your-username>.github.io/<repository-name>/`.

---

## Usage Instructions

### 1. Upload Images

- Click on the **"Browse"** button to upload a ZIP file containing your images.
- The app supports images in `.png`, `.jpg`, and `.jpeg` formats.
- Wait for the images to be processed (a loading message will appear).

### 2. Set Custom Scores (Optional)

- **Optional but recommended**.
- Enter your desired scores and labels in the **"Enter Custom Scores"** field.
- **Format**: `score: label`, separated by commas.
  - Example: `0: Poor, 1: Fair, 2: Good, 3: Very Good, 4: Excellent`
- Click **"Set Scores"** to populate the score selector and assign colors.

### 3. Set Default Score (Optional)

- Enter a default score in the **"Default Score"** field.
- The default score must be one of the scores you've set.
- This score will be automatically assigned to all images upon loading.

### 4. Set Replication Factor (Optional)

- Enter a replication factor greater than `1.0` to include replicated images.
- **Example**: `1.2` for 20% replication.

### 5. Enable Pagination (Optional)

- Check the **"Enable Pagination"** box to paginate images.
- Specify the number of images per page in the **"Images Per Page"** field.

### 6. Load Images

- Click the **"Load Images"** button to start the scoring session.
- The images will be randomized and displayed according to your settings.

### 7. Assign Scores to Images

- Select a score from the **dropdown menu**.
- Click on images to assign or change scores.
- Images will display a border color corresponding to their assigned score.
- A score label will appear over each scored image.

### 8. Navigate Between Pages

- **If pagination is enabled**.
- Use the **"Previous"** and **"Next"** buttons to navigate through the pages.
- The current page number and total pages are displayed.

### 9. Download Scores

- Once you have finished scoring, click the **"Download Scores"** button.
- The app will check for unscored images and inconsistencies in replicated images.
- The scoring results will be saved as a CSV file named `image_scores.csv`.

---

## Features Explanation

### Randomization

- Images are shuffled to prevent order bias.
- Ensures that the scoring is not influenced by the sequence of images.

### Replication for Consistency Checks

- Replicates a specified percentage of images.
- Helps assess the reliability of the scoring by comparing scores of original and replicated images.

### Blinding Image Names

- Images are assigned anonymous IDs (e.g., `Image_1`, `Image_2`).
- Original filenames are not displayed during scoring to prevent bias.
- Original filenames are included in the exported CSV for analysis.

### Color-Coded Scores

- Each score is assigned a unique border color.
- Enhances visual differentiation between scores.
- Helps quickly identify images based on their assigned scores.

### Default Score

- Allows setting a default score to be automatically assigned to all images upon loading.
- Useful when most images are expected to have the same initial score.

### Pagination

- Improves performance and usability when dealing with a large number of images.
- Users can enable or disable pagination and specify the number of images per page.

### Consistency Checks

- The app checks for inconsistencies in scoring of replicated images.
- Alerts the user if discrepancies are found between original and replicated image scores.

### Comprehensive Data Export

- Exports scoring data as a CSV file containing:
  - **Image ID**: Anonymous identifier.
  - **File Name**: Original filename of the image.
  - **Score**: Assigned score (with label if provided).
  - **Timestamp**: When the score was assigned.
  - **Is Replicate**: Indicates if the image is a replicate.
  - **Original Image ID**: Anonymous ID of the original image for replicates.

---

## Technical Details

- **Technologies Used**:
  - HTML, CSS, JavaScript.
  - [JSZip](https://stuk.github.io/jszip/) for unzipping files client-side.
  - [FileSaver.js](https://github.com/eligrey/FileSaver.js/) for saving files in the browser.

- **Data Handling**:
  - All data processing is done client-side.
  - No data is uploaded to any server.
  - Images and scores are stored in memory during the session.

---

## Browser Compatibility

- The app is compatible with modern web browsers:
  - Google Chrome
  - Mozilla Firefox
  - Microsoft Edge
  - Safari

- **Note**: Ensure that JavaScript is enabled in your browser settings.

---

## Privacy and Security

- **Data Privacy**:
  - All image processing and scoring are performed locally in your browser.
  - No images or data are transmitted over the internet.
  
- **Security Considerations**:
  - Since the app runs locally, it's important to use it on a secure device.
  - Be cautious when handling sensitive or confidential images.

---

## Contributing

Contributions are welcome! If you'd like to improve the app or add new features:

1. **Fork the Repository**: Create a personal copy on your GitHub account.

2. **Create a New Branch**: For your feature or bug fix.

3. **Make Your Changes**: Implement your improvements.

4. **Submit a Pull Request**: Describe your changes and submit for review.

Please ensure that your contributions align with the project's goals and maintain code quality.

---

## License

This project is licensed under the Apache License.

---

If you have any questions or need assistance, feel free to open an issue or <clstacy.stat@gmail.com>.

Enjoy using the Image Scoring App for your scientific research!
