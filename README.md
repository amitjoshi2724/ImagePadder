# Image and Video Padder

<p align="center">
  <img src="https://github.com/amitjoshi2724/ImagePadder/raw/main/favicon.jpg" width="150" alt="Image Padder Logo">
</p>

A tool that pads images or videos to any aspect ratio while preserving the original resolution. Add space around your images/videos with custom padding or convert to specific aspect ratios like 16:9, 4:3, 1:1 square, and more. Perfect for social media posts or vlogs, video thumbnails, and printing.

## Features

- Preserve original image/video resolution and quality
- Choose any background color, with optional transparency
- Pad images with specific aspect ratios or custom padding
- Process multiple images at once (website only, for now)
- Pad videos (command-line version only)
- Works with all common image formats (JPG, PNG, HEIC etc.)
- Works with all common video formats (mp4, mov, etc.)

## Website  
[https://amitjoshi2724.github.io/ImagePadder/](https://amitjoshi2724.github.io/ImagePadder/)  

The web version is the easiest way to use Image Padder, with a user-friendly interface and additional options like custom padding. The website does NOT support video padding, for that keep reading.

**Note:** Browser-based tools have resolution limits (typically 16,384 × 16,384 pixels). For very high-resolution images, HEIC/HEIF images, or video padding, use the command-line version or Python Graphical-User-Interface (GUI) below.


## 📲 Install as an App & Use Offline (Mac, iOS & Android)

**Image Padder** is built as a full **Progressive Web App (PWA)** powered by a dedicated **Service Worker (`sw.js`)** and Web App Manifest (`manifest.json`). 

Once installed to your desktop or smartphone:
- ✈️ **100% Offline Capable:** The entire client-side image processing engine, canvas pipeline, and UI are pre-cached directly to persistent device storage via the **Cache Storage API**. You can pad photos in Airplane Mode with zero Wi-Fi or cellular data anytime, anywhere.
- 🖥️ **Native Standalone Window:** Launches in its own dedicated window without browser address bars, URL fields, or tabs.
- 🔄 **Zero-Hassle Background Updates:** When you connect to Wi-Fi, the Service Worker automatically fetches and updates any new changes pushed to GitHub.

### 🍎 Mac (macOS Desktop App)

You can install **Image Padder** directly as a native macOS desktop application with its own dedicated window, Dock icon, and full offline support:

#### Method A: Safari (macOS Sonoma / Sequoia or newer)
1. Open **[https://amitjoshi2724.github.io/ImagePadder/](https://amitjoshi2724.github.io/ImagePadder/)** in **Safari**.
2. In the top menu bar, click **File** > **Add to Dock...** (or click the **Share** button in the Safari toolbar and select **Add to Dock**).
3. Name it **Image Padder** and click **Add**.
4. The app is saved to your `Applications` folder and pinned to your **macOS Dock**.
5. Launch it like any native Mac app—it runs in its own window without browser tabs or address bars, and is 100% functional offline!

#### Method B: Google Chrome, Brave, or Microsoft Edge
1. Open **[https://amitjoshi2724.github.io/ImagePadder/](https://amitjoshi2724.github.io/ImagePadder/)** in **Chrome**, **Brave**, or **Edge**.
2. Click the **Install Image Padder** icon in the right side of the address/URL bar (or go to **Settings (⋮)** > **Save and share** > **Install Image Padder...**).
3. Click **Install**.
4. The app opens in its own standalone desktop window and is added to your Mac's **Launchpad**, **Spotlight**, and `~/Applications/Chrome Apps` folder.

### 🍏 iPhone & iPad (iOS Safari)
1. Open **[https://amitjoshi2724.github.io/ImagePadder/](https://amitjoshi2724.github.io/ImagePadder/)** in **Safari**.
2. Tap the **Share** button at the bottom of the screen (the square with an arrow pointing upward).
3. Scroll down the share sheet and tap **"Add to Home Screen"**.
4. Tap **Add** in the top-right corner. A dedicated Image Padder icon will appear on your home screen.
5. Tap the new icon once while online to let the Service Worker cache all assets—after that, it is permanently usable offline!

### 🤖 Android (Google Chrome)
1. Open **[https://amitjoshi2724.github.io/ImagePadder/](https://amitjoshi2724.github.io/ImagePadder/)** in **Google Chrome**.
2. Tap the **three-dots menu (⋮)** in the top-right corner.
3. Tap **"Install app"** (or **"Add to Home screen"**).
4. Tap **Install** on the prompt. The app will install directly to your home screen and app drawer as an offline-ready utility app.

## Padding Images and Videos Locally ##

### Installation ###
Python 3.4+ is required to run this.

No virtual environment is required for running this. However, if this makes you feel more comfortable, you can set one up by using the following code:

1. `python3 -m venv .venv`
2. `source .venv/bin/activate`

### Dependencies

Install required dependencies using the requirements.txt file:

```
pip install -r requirements.txt
```

This will install:
- PIL (Pillow): Core image processing library
- pillow-heif: For HEIC/HEIF support (Apple's image format)
- moviepy: For video padding support
- tkinter: For GUI (included with standard Python)

Or install Python dependencies manually:

```
pip install Pillow
pip install moviepy
pip install pillow-heif
```

### External Dependencies

For video padding functionality, FFmpeg needs to be installed on your system:
- macOS: `brew install ffmpeg`
- Ubuntu/Linux: `sudo apt-get install ffmpeg`
- Windows: Download from [ffmpeg.org](https://ffmpeg.org/download.html) or use `choco install ffmpeg` with Chocolatey

**Note:** The command-line tool will automatically detect if you're missing any required dependencies.

### Usage
Fortunately, I have just made a new GUI if you prefer

#### GUI Mode

![GUI Screenshot](https://github.com/amitjoshi2724/ImagePadder/blob/main/guiss.jpg)

1. Run: `python imagepaddergui.py`
2. Select an image or video using the "Browse" button
3. Choose between "Aspect Ratio" or "Custom Padding" modes
4. Configure your padding settings
5. Select a background color (with optional transparency)
6. Click "Process" to create your padded image/video

#### Command Line Mode

The image padder can be ran either by passing in command-line arguments to `imagepadder2.py` or by using the interactive prompt also within `imagepadder2.py`. 

##### CLI arguments

###### Image Padding

For image aspect ratio padding:
```
python3 imagepadder2.py '/Users/apple/Pictures/best_friends_photo.jpg' aspect 16x9 #FFFFFF 255
```

| Parameter | Description |
|-----------|-------------|
| 1: Image/Video path | Path to the image/video file |
| 2: Mode | `aspect` for aspect ratio mode |
| 3: Ratio | Width and height in format `WxH` (e.g., `16x9`) |
| 4: Color | Background color in hex format (e.g., `#FFFFFF` for white) |
| 5: Opacity | Background opacity, 0-255 (e.g., `255` for fully opaque) |

For image custom padding:
```
python3 imagepadder2.py '/Users/apple/Pictures/best_friends_photo.jpg' custom 20 30 20 30 #000000 128
```

| Parameter | Description |
|-----------|-------------|
| 1: Image path | Path to the image file |
| 2: Mode | `custom` for custom padding mode |
| 3-6: Padding | Four values for padding in pixels: `top right bottom left` |
| 7: Color | Background color in hex format (e.g., `#000000` for black) |
| 8: Opacity | Background opacity, 0-255 (e.g., `128` for half-transparent) |

###### Video Padding (works the same way)

For video aspect ratio padding:
```
python3 imagepadder2.py '/Users/apple/Videos/vacation.mp4' aspect 16x9 #000000 255
```

For video custom padding:
```
python3 imagepadder2.py '/Users/apple/Videos/vacation.mp4' custom 50 50 50 50 #0000FF 255
```

##### Interactive Prompt (Works with both Images and Videos) #####


```
python3 imagepadder2.py
```

Then follow the prompts:
```
> image's filename to pad: /Users/apple/Pictures/best_friends_photo.jpg
> Choose padding mode ('aspect' for aspect ratio or 'custom' for custom padding): aspect
> Enter aspect ratio you desire in the form of WIDTHxHEIGHT, e.g. "4x3": 16x9
> Background color (hex format, e.g. #FFFFFF for white) [default: #FFFFFF]: 
> Background opacity (0-255, default: 255): 255
```
OR
```
> image's filename to pad: /Users/apple/Videos/vacation.mp4
> Choose padding mode ('aspect' for aspect ratio or 'custom' for custom padding): aspect
> Enter aspect ratio you desire in the form of WIDTHxHEIGHT, e.g. "4x3": 16x9
> Background color (hex format, e.g. #FFFFFF for white) [default: #FFFFFF]: #000000
> Background opacity (0-255, default: 255): 255
```
OR
```
> image's filename to pad: /Users/apple/Pictures/best_friends_photo.jpg
> Choose padding mode ('aspect' for aspect ratio or 'custom' for custom padding): custom
> Enter top padding (pixels): 20
> Enter right padding (pixels): 30
> Enter bottom padding (pixels): 20
> Enter left padding (pixels): 30
> Background color (hex format, e.g. #FFFFFF for white) [default: #FFFFFF]: #000000
> Background opacity (0-255, default: 255): 128
```

#### Examples

| **Command** | **Description** |
|-------------|-----------------|
| `python -m imagepadder2 image.jpg` | Interactive command-line mode |
| `python imagepaddergui.py` | Launch the graphical user interface |
| `python -m imagepadder2 image.jpg aspect 16x9` | Pad to 16:9 aspect ratio |
| `python -m imagepadder2 image.jpg custom 10 20 30 40` | Custom padding (top, right, bottom, left) |
| `python -m imagepadder2 image.jpg aspect 1x1 #FF0000 128` | Square with semi-transparent (128 out of 255) red (#FF0000) background |


### Notes ###

#### Working with High-Resolution Images ####

While most image processing tools in browsers have canvas size limitations (typically around 16,384 × 16,384 pixels), the command-line version of Image Padder can handle much larger images by using Python's PIL/Pillow library directly. For gigapixel images, or other extremely large files, the command-line version or GUI are needed, otherwise the website works fine.

#### Working with Videos ####
The command-line version and python GUI support padding videos to different aspect ratios or adding custom padding. Supported formats include MP4, AVI, MOV, MKV, WEBM, and WMV. The padding is applied to each frame while preserving the original audio track. Due to the processing required, video padding may take some time depending on the length and resolution of the video, but progress is shown in command line, and somewhat in the logs section of the GUI.

The parameters work the same way as for images, but the tool will automatically detect if the file is a video based on the extension (mp4, avi, mov, mkv, webm, wmv). Note that the script is still called "imagepadder2.py" even for videos. 

You can use the interactive prompt, CLI arguments, or GUI with both images and videos - the tool will automatically detect the file type and pad accordingly:

## Credits

The program and the image padding algorithm were originally written by Amit Joshi ([@amitjoshi2724](https://github.com/amitjoshi2724)). Code improvements were made by Jeffrey Wang ([@jeffw16](https://github.com/jeffw16)).

## Support the Project

If you find this tool useful, consider supporting its development through one of these options:

- [PayPal](https://paypal.me/amitjoshi168)
- [Venmo](https://venmo.com/Amit-Joshi-11) 
- [Ko-fi](https://ko-fi.com/amitjoshi2724)

Thank you for your support!
