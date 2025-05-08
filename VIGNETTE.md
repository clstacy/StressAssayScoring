# Stress Assay Scoring Workflow Tutorial

This guide walks through the process of using the Stress Assay Tools (Image Grid Dicer and Scoring App) to process plate images and score wells.

## Part 1: Preparing Images with the Image Grid Dicer

### 1. Start with Scanned Plate Images

Begin with your scanned `.tif`, `.jpg`, `.png`, etc., images of the stress assay plates. You can process multiple plates at once if they share the same grid layout (rows/columns) and column/row metadata (e.g., concentrations, strain names). This example uses one image.

*Example Original File:* `ExperimentName_Strain_PlateID_RepX.tif`

### 2. Crop the Plate Image (Optional but Recommended)

Cropping the image to include only the assay spots can improve the accuracy of the Dicer tool.

* **MacOS Example:**

  1. Open the original image in Preview.
  2. Export it as a PNG (`File > Export...` select PNG format). Save it in a dedicated folder (e.g., `plate_images_to_dice`).
  3. Close the original `.tif`.
  4. Open the newly saved PNG file in Preview.
  5. Select the rectangular area containing just the spots using click-and-drag.
     * *Tip:* Try to center the selection box accurately. If you have an even number of rows/columns, center the box edge between the middle two. If odd, center the box edge on the middle row/column. It's better to slightly overlap a spot than to have excessive empty margin space.
     * ![PictureCropping](https://github.com/user-attachments/assets/6412f689-90a9-4849-8d2c-9471ad8b6b3b)
  6. Go to `Tools > Crop` (or use keyboard shortcut `Cmd+K`).
  7. Save the cropped image (`File > Save` or `Cmd+S`). Ensure the filename contains relevant metadata for the *entire plate* (e.g., `ExperimentName_Strain_PlateID_RepX`).
     *Example Cropped Filename:* `GeneKOdefect_H2O2resistance_WT_Plate2_Rep1.png` (Adding `_Rep1` is good practice even for single reps).

### 3. Use the Image Grid Dicer Tool

1. Go to the [Stress Assay Scoring Tool](https://clstacy.github.io/StressAssayScoring/).
2. Ensure you are on the **Image Grid Dicer** tab (it should be the default tab on the left).
3. Click the "Upload plate photo(s)" button and select your *cropped* plate image(s) (e.g., `GeneKOdefect_H2O2resistance_WT_Plate2_Rep1.png`).
4. Update the **Rows** and **Cols** fields to match your plate layout (e.g., Rows: 8, Cols: 12).
5. Update the **Row labels** field. Enter the unique identifier for each row, separated by commas. Based on your example:
   * `WT_Mock,WT_0.4M.NaCl,WT_5pctEthanol,WT_0.4mMh2o2,geneKO_Mock,geneKO_0.4MNaCl,geneKO_5pctEthanol,geneKO_0.4mMh2o2`
   * *Note:* Using underscores (`_`) instead of spaces is recommended for labels.
6. Update the **Column labels** field. Enter the unique identifier for each column, separated by commas.
   * `0.125,0.25,0.5,1,2,4,8,16,32,64,128` (Assuming "mMH2O2" is implied context, otherwise include it like `0.125mMH2O2`).
7. Click **Process Images**.
8. Once processing is complete, click **Download Cropped Images ZIP**.

### 4. Verify Cropped Images

1. Unzip the downloaded file (usually `cropped_well_images.zip`).
2. Inside, you'll find folders named after your original uploaded plate image(s). Each folder contains the individual well images (e.g., `GeneKOdefect_H2O2resistance_WT_Plate2_Rep1/GeneKOdefect_H2O2resistance_WT_Plate2_Rep1_WT_Mock_0.125.jpg`).
3. Briefly check a few images to ensure they look correctly cropped. If the grid dimensions were wrong, the cropped images will look incorrect.

## Part 2: Scoring Wells with the Stress Assay Scoring App

### 1. Navigate to the Scoring App

Go back to the [Stress Assay Scoring Tool](https://clstacy.github.io/StressAssayScoring/) and click the **Stress Assay Scoring** tab (on the right).

### 2. Upload Cropped Well Images

1. Click the **"1. Upload well images (folder)"** button.
2. Select the **folder(s)** containing the cropped well images you just created and verified (e.g., select the `GeneKOdefect_H2O2resistance_WT_Plate2_Rep1` folder).
   * You can upload multiple folders at once if you processed multiple plates.
   * Your browser might ask for permission to upload the folder contents.
   * *Privacy Note:* This is a static HTML tool. No image data leaves your computer. The code can be inspected on [GitHub](https://github.com/clstacy/StressAssayScoring).

### 3. Enter Scorer Information

Fill in the **"2. Scorer name"** field with your name or initials. *This is required before analyzing images.*

### 4. Set Scoring System (Optional)

* The app defaults to a 0-4 scoring system for yeast stress assays.
* If you need a different system, enter it in the **"3. (Optional) Custom scores"** box. Use commas to separate scores and colons for labels (e.g., `0:None, 1:Low, 2:Medium, 3:High`).
* Click **Set** to apply your custom system. The score selector dropdown will update.

### 5. Set Replication Factor (Optional)

* Use the **"4. (Optional) Replication factor"** field to score replicates for consistency checks.
  * `1` = No replication (score each image once).
  * `2` = Score each image twice (Default).
  * `1.5` = Score each image once, plus a random 50% subset a second time.
* Replicates appear on subsequent pages.

### 6. Load Images

Click the **"5. Load Images for Scoring"** button. The images will load into the main panel, randomized and potentially rotated to aid blinded scoring.

### 7. Score Images

1. Use the **"6. Select score & Click Image to Assign"** dropdown in the bottom-left panel to choose the score you want to assign (e.g., `0 (0-2 colonies)`).
2. Click on the image thumbnails in the main grid to assign the selected score.
3. Scored images will move towards the bottom/end of the current page view to help you focus on unscored ones.
4. Change the selected score in the dropdown as needed.
5. To correct a mistake, simply select the correct score and click the mis-scored image again.
6. *Tip:* If a well image contains parts of two spots, score based on the spot that occupies the majority of the image area.

### 8. Score Replicates (If Applicable)

* If your replication factor was greater than 1, once you finish scoring all images on the current page, use the **Next Page ▶** button (sticky at the top of the image grid) to move to the next replicate set.
* The images for the replicate will be presented in a new random order.
* Repeat the scoring process until all replicate pages are complete.

### 9. Finish and Review Results

1. Once all scoring is done, click the **Finish & View Results** button (bottom left).
2. A pop-up window will show:
   * Summary counts for each score category.
   * Replicate QC statistics (how many sets matched/mismatched).
   * Cohen's Weighted Kappa (κ) score, measuring inter-replicate agreement.
3. Review the summary. Close the pop-up using the '×' in the top-right corner.

### 10. Download Results

1. Click the **Download Scores & Mosaics** button (bottom left).
2. A ZIP file will be downloaded (e.g., `StressAssay_ScoringResults_YourInitials_YYYY-MM-DD.zip`).
3. This ZIP file contains:
   * `image_scores.csv`: A comma-separated file with detailed results for each scored image (including PlateID, FilePath, Row, Column, Score, Timestamp, etc.).
   * `summary_statistics.txt`: A text file containing the same summary and QC report shown in the results pop-up.
   * `plate_mosaics/` (folder): Contains reconstructed mosaic images for each plate processed.
     * Each mosaic PNG is named after its PlateID (e.g., `GeneKOdefect_H2O2resistance_WT_Plate2_Rep1.png`).
     * Wells are shown in their original orientation (unrotated).
     * Scores are overlaid on each well (larger font size). If replicates had different scores, they are shown separated by `/`.
     * Row labels on the mosaic include the unique identifiers parsed from the filenames.

### 11. Final Check

Open the downloaded files, especially the mosaic images, to perform a final visual check of the results.

You have now successfully processed and scored your stress assay plates!
