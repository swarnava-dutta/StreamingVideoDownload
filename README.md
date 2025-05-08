## 🔍 How to Find the Streaming(M3U8) URL from Any Video

To download a video using this tool, you first need to obtain its `.m3u8` streaming URL. Follow these steps:

### 🖥️ Using Browser Developer Tools

1. **Open the Video in Your Browser**
   - Navigate to the page that contains the video you want to download.

2. **Open Developer Tools**
   - Right-click anywhere on the page and select **Inspect**, or press `F12` or `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Option+I` (Mac).

3. **Go to the "Network" Tab**
   - In the developer tools panel, click the **Network** tab.
   - Refresh the page (`F5`) to capture all network activity.

4. **Filter by "m3u8"**
   - In the filter/search bar, type `m3u8` to show only requests with `.m3u8` in the URL.

5. **Play the Video**
   - If the video is not playing automatically, click play. This will trigger HLS requests.

6. **Locate the M3U8 File**
   - Look for a URL ending in `.m3u8`. It may appear as `example.m3u8` or similar.
   - Right-click the URL and choose **Copy > Copy URL**.

7. **Paste into the Downloader**
   - Use this link as the input URL in your Colab notebook.
     
![image](https://github.com/user-attachments/assets/8765c436-15f3-470f-8b5d-08f3197aa8cc)


---

### 📌 Tips

- **Use Chrome or Firefox**: These browsers provide the best developer tools for tracking network requests.
- **Check Permissions**: Some sites use tokenized or protected streams. These may not be downloadable using `ffmpeg`.


---

## 🧠 About the Project

M3U8 playlists are commonly used for HLS (HTTP Live Streaming). This project provides a user-friendly interface inside a Google Colab notebook to:
- Add multiple video URLs
- Specify custom output filenames
- Download them efficiently using `ffmpeg` in parallel

---

## ✨ Features

- 📥 Add and manage a queue of videos with M3U8 links
- 🧾 Specify output filenames (auto-named if omitted)
- 🧵 Download multiple videos in parallel using Python threads
- 🔁 Real-time progress bars with `tqdm`
- 🧩 Intuitive widget-based UI

![image](https://github.com/user-attachments/assets/50ac104b-bdfb-40b1-a2d3-8e8ef4ee4109)

---

## ⚙️ Installation

No installation is required other than opening the Colab notebook. However, the notebook handles installing `ffmpeg` if it's not already available:

```python
!apt-get update
!apt-get install ffmpeg -y
```

---

## 🚀 Usage

- Open the notebook in Google Colab.
- Enter the M3U8 URL and output file name.
- Click **"Add Video"** to queue it for downloading.
- Once all URLs are added, click **"Download All"** to begin downloading.
- Use the **"Clear All"** button to reset the list.
- You can also adjust the **Max Parallel** downloads using a slider (1–5 workers).

---

## ▶️ Example Run

```python
# Example M3U8
URL: https://bitdash-a.akamaihd.net/content/sintel/hls/playlist.m3u8
Output: sintel_video.mp4
```

Click **Add Video**, then **Download All**.

---

## 📦 Dependencies

- `ffmpeg` (installed in notebook)
- `ipywidgets`
- `tqdm`
- `concurrent.futures` *(standard lib)*
- `subprocess`, `os`, `time`, `IPython.display`

All dependencies are included or automatically handled by Google Colab.

---

## ⚙️ Configuration

| Parameter         | Description                        | Default        |
|------------------|------------------------------------|----------------|
| **URL**           | M3U8 playlist URL                  | —              |
| **Output Filename** | Custom MP4 filename             | `video_N.mp4`  |
| **Max Parallel**   | Number of parallel downloads       | `3` (1–5 range) |

---

## 🧪 Examples

| Input URL                      | Output Filename     |
|--------------------------------|---------------------|
| `https://test-stream.m3u8`     | `my_video.mp4`      |
| `https://demo/video.m3u8`      | *auto: `video_1.mp4`* |

---

## 🛠️ Troubleshooting

- **ffmpeg not found**: The script auto-installs it using `apt-get`.
- **Invalid M3U8**: Make sure your link is accessible and not DRM-protected.
- **Failed downloads**: Check URL validity and ensure it doesn’t require tokens or authentication.
- **Stuck progress bar**: Sometimes `ffprobe` can’t retrieve duration. In such cases, the downloader uses an estimated time-based fallback.

---

## 🪪 License

This project is licensed under the **MIT License**.
