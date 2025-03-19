# **Updating the Sandbox Website Data**

The Sandbox website is built on the **MkDocs Material** framework. MkDocs is a static site generator that creates documentation from Markdown files. The Material theme provides a modern, responsive UI for the site.

For more details about MkDocs Material, visit:  
🔗 [MkDocs Material Documentation](https://squidfunk.github.io/mkdocs-material/)

The source code for the website is hosted on GitHub:  
🔗 [GitHub Repository: IDREsandbox/sandbox](https://github.com/IDREsandbox/sandbox)

---

## **1. Cloning and Running the Website Locally**
To work with the website, follow these steps:

1. Clone the repository:
   ```sh
   git clone https://github.com/IDREsandbox/sandbox.git
   ```
2. Navigate to the project folder:
   ```sh
   cd sandbox
   ```
3. Use command-line tools to navigate to the `docs/` folder:
   ```sh
   cd docs
   ```
4. Run the MkDocs development server to preview the site locally:
   ```sh
   mkdocs serve
   ```
   This will start a local server at `http://127.0.0.1:8000/`, allowing you to preview the changes in real-time.
5. Once satisfied, build the static site:
   ```sh
   mkdocs build
   ```
   This generates the final version of the website in the `site/` folder.

---

## **2. Enter Data into the Google Sheet**
- Open the Google Sheet:  
  [Sandbox Website Data](https://docs.google.com/spreadsheets/d/1bQDVVO-R3tt99eR7ageBYu5XK8lnnlxHZLzJghYSLa0/edit?hl=en&forcehl=1&gid=1135922496#gid=1135922496).
- The spreadsheet has separate tabs for different website sections:
  - **Learn**
  - **Work**
  - **Consult**
  - **Musings**
- Each sheet requires the following information for each entry:
  - **Title** – The title of the content.
  - **Category** – The section classification.
  - **Description** – A brief summary of the content.
  - **Tags** – Keywords that describe the entry.
  - **Main Image** – The filename of the corresponding image (without file path).

---

## **3. Upload the Corresponding Image to the Server**
- Locate the image file corresponding to the filename entered in the **Main Image** column.
- Upload the image to the appropriate section folder on the server:
  - `docs/learn/images/`
  - `docs/work/images/`
  - `docs/consult/images/`
  - `docs/musings/images/`
- Ensure the image file is named **exactly** as entered in the spreadsheet to avoid broken links.

---

## **4. Mark Splashable Images**
- If an image is **usable as a splash page image**, set the **"Splashable"** column value to **TRUE**.
- This ensures the image can be randomly selected when a user visits the website.

---

## **5. Run the Python Script to Update the Website Data**
- After updating the Google Sheet, execute the Python script to generate a new JSON snapshot of the data.
- The script is located in:
  ```sh
  docs/js/getdata.py
  ```
- Run the script using:
  ```sh
  python docs/js/getdata.py
  ```
- Running this script ensures that the website reflects the latest changes.

---

## **6. Verify the Changes on the Website**
- Refresh the website and confirm that the updated entries appear correctly.
- Check images, categories, and descriptions to ensure accuracy.

By following these steps, the website data will be successfully updated with new content.

