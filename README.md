# Steganography Project: Covert Communication via Image Hiding

## 🚀 Project Overview

This project implements a simple yet effective steganography tool that allows for the **covert embedding of text messages within digital images** and their subsequent extraction. Utilizing the Least Significant Bit (LSB) substitution technique, the tool aims to conceal the very existence of secret communication, making it imperceptible to the casual observer.

## ✨ Features

* **Hide Data:** Embeds a secret text message into a cover image.
* **Extract Data:** Retrieves the hidden message from a stego-image.
* **LSB Methodology:** Modifies the least significant bits of pixel color components (RGB) for imperceptible changes.
* **Stop Signal:** Uses a unique marker (`#####END#####`) to accurately determine the end of the hidden message during extraction.
* **Modular Design:** Clear separation of core steganography logic (`steg.py`) from the user interface (`main.py`).

## 🛠️ How It Works (LSB Steganography)

The core of this project relies on **Least Significant Bit (LSB) substitution**. Digital images are composed of pixels, each represented by numerical values for color (e.g., Red, Green, Blue components, typically 0-255). By subtly altering the *least significant bit* (the rightmost bit) of these color values, we can embed data without causing a noticeable visual change. For instance, changing a pixel value from `10101010` to `10101011` is usually imperceptible to the human eye.

The system converts the secret message into a binary stream, then iterates through the image pixels, embedding one bit of the secret message into the LSB of each R, G, and B channel. A pre-defined "stop signal" is embedded at the end of the message, allowing the extraction algorithm to know precisely where the hidden data concludes.

## 📁 Project Structure

```

SteganographyProject/
├── images/                       \# Folder for input (cover) images and output (stego) images
│   └── cover\_image.png           \# Your sample cover image (place your actual image here)
├── steg.py                       \# Contains the core steganography logic (hide\_data, extract\_data, etc.)
├── main.py                       \# Main script to run the application and handle user interaction
├── requirements.txt              \# Lists project dependencies (e.g., Pillow)
└── .gitignore                    \# Specifies files/folders to exclude from Git tracking

````

## 📋 Requirements

* **Python 3.x**
* **Pillow** library (Python Imaging Library fork)

## 🚀 Getting Started

Follow these steps to set up and run the project on your local machine:

1.  **Clone the Repository (or Download):**
    ```bash
    git clone [https://github.com/ArpitAI/Steganography.git](https://github.com/ArpitAI/Steganography.git)
    cd Steganography
    ```

2.  **Create a Virtual Environment (Recommended):**
    This isolates project dependencies.
    ```bash
    python -m venv stegenv
    ```

3.  **Activate the Virtual Environment:**
    * **Windows:**
        ```bash
        .\stegenv\Scripts\activate 
        ```
    * **macOS/Linux:**
        ```bash
        source stegenv/bin/activate 
        ```
    You'll see `(venv)` (or `(stegenv)`) at the beginning of your terminal prompt.

4.  **Install Dependencies:**
    Install all required Python libraries from `requirements.txt`.
    ```bash
    pip install -r requirements.txt
    ```

5.  **Prepare Your Cover Image:**
    * Place your desired cover image (e.g., `my_cover_image.png`) into the `images/` folder. Make sure to use a lossless format like **PNG** for the cover image, as JPEG compression can destroy hidden data.

## 💡 Usage

Run the `main.py` script from your terminal:

```bash
python main.py
````

Follow the on-screen prompts:

### **1. Hide Data:**

```
--- Steganography Tool ---
1. Hide data in an image
2. Extract data from an image
3. Exit
Enter your choice (1, 2, or 3): 1

--- Hide Data ---
Enter the name of the cover image (e.g., cover_image.png): my_cover_image.png
Enter the secret message you want to hide: Your very secret message goes here!
Enter the name for the output stego-image (e.g., stego_image.png): my_stego_image.png
Message hidden successfully! Stego-image saved to 'D:\SteganographyProject\images\my_stego_image.png'
Operation completed successfully.
```

*(A new `my_stego_image.png` will be created in your `images/` folder.)*

### **2. Extract Data:**

```
--- Steganography Tool ---
1. Hide data in an image
2. Extract data from an image
3. Exit
Enter your choice (1, 2, or 3): 2

--- Extract Data ---
Enter the name of the stego-image (e.g., stego_image.png): my_stego_image.png

------------------------------
Extracted Message:
Your very secret message goes here!
------------------------------
Extraction operation completed successfully.
```

## ⚠️ Limitations & Considerations

  * **Capacity:** The amount of data you can hide is limited by the image's size.
  * **Robustness:** LSB steganography is fragile. Saving the stego-image in a lossy format (like JPEG), resizing, cropping, or applying filters will likely corrupt or destroy the hidden message. Use **PNG** for saving stego-images.
  * **Security:** LSB steganography is not a strong security measure on its own. It only conceals the *existence* of data, not its content. For true security, the hidden message should be **encrypted** before embedding.

## 🔮 Future Scope

  * **Encryption:** Integrate encryption (e.g., AES) for the secret message before embedding.
  * **Advanced Techniques:** Explore more robust steganography methods like DCT (Discrete Cosine Transform) or DWT (Discrete Wavelet Transform) for better resilience against image manipulation.
  * **GUI Development:** Create a graphical user interface using libraries like Tkinter or PyQt for improved user experience.
  * **Increased Capacity:** Implement techniques to hide more bits per pixel while maintaining imperceptibility.
  * **Media Support:** Extend functionality to hide data in other media types (audio, video).

## 🤝 Contributing

Feel free to fork this repository, open issues, or submit pull requests to contribute to this project\!

## 📄 License

This project is open-source and available under the [MIT License](https://www.google.com/search?q=LICENSE).

-----

Replace `https://github.com/YourUsername/SteganographyProject.git` with your actual repository URL. If you plan to add a `LICENSE` file, you should create one in the root directory.
