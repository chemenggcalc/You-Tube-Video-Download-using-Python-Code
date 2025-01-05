

### How to Download YouTube Videos Using Python in Google Colab

Downloading YouTube videos is a common task for developers, researchers, and learners who want to save videos for offline use. Python provides a handy tool for this task called `yt-dlp`, a powerful fork of `youtube-dl`. You can easily use it in Google Colab to download videos from YouTube.

Here's a step-by-step guide to downloading YouTube videos using Python code in Google Colab:

#### 1. Install yt-dlp in Google Colab
The first step is to install the `yt-dlp` library, which can be done with the following command:

```python
!pip install yt-dlp
```

This command installs `yt-dlp` and its dependencies, allowing you to download videos and audio from YouTube.

#### 2. Python Code to Download a YouTube Video

```python
import yt_dlp

def download_youtube_video(video_url, save_path="downloads"):
    """
    Downloads a YouTube video in the best available video and audio quality.

    Args:
        video_url (str): URL of the YouTube video.
        save_path (str): Directory to save the downloaded video.
    """
    try:
        # Options for yt-dlp
        ydl_opts = {
            'format': 'bestvideo+bestaudio/best',  # Download best video and audio and merge
            'outtmpl': f'{save_path}/%(title)s.%(ext)s',  # Save file format
            'merge_output_format': 'mp4',  # Merge video and audio into MP4 format
        }

        # Downloading the video
        print("Downloading...")
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            ydl.download([video_url])
        print(f"Video downloaded successfully and saved in: {save_path}")

    except Exception as e:
        print(f"An error occurred: {e}")

if __name__ == "__main__":
    # Input YouTube video URL
    video_url = input("Enter the YouTube video URL: ").strip()

    # Input save directory (default is 'downloads')
    save_path = input("Enter the save path (or press Enter for default 'downloads'): ").strip() or "downloads"

    # Call the function to download the video
    download_youtube_video(video_url, save_path)
```

#### Explanation of the Code:
1. **Install the required library**: The `yt-dlp` library is installed using `pip install yt-dlp`.
2. **Define the download function**: The `download_youtube_video` function takes two arguments:
   - `video_url`: The URL of the YouTube video to download.
   - `save_path`: The directory to save the downloaded video (defaults to `downloads`).
3. **yt-dlp options**: The options specify that the best available video and audio will be selected and merged into an MP4 format.
4. **Download and Save**: The video is downloaded to the specified directory using the `yt_dlp.YoutubeDL` method.
5. **User Input**: The user is prompted to enter the YouTube video URL and an optional save path. If the save path is not provided, it defaults to the "downloads" folder.

#### How to Use:
1. Paste the above code into a Google Colab notebook.
2. Run the code cell.
3. Enter the URL of the YouTube video you want to download.
4. Optionally, specify a save path for the downloaded video. If you press Enter without providing a path, the video will be saved in a folder named `downloads` by default.
5. Wait for the download process to complete. The video will be downloaded in the best possible quality and saved in the specified directory.

#### Conclusion:
With this simple Python script in Google Colab, you can easily download YouTube videos. The `yt-dlp` library makes it straightforward to download videos in the best available quality while merging video and audio into a single MP4 file.
