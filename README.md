# Task 6: YouTube Video Downloader
# Libraries Used: pytube, numpy, pandas, matplotlib

# Install pytube first in online compiler if needed:
# pip install pytube

import os
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from pytube import YouTube

# Function to download video
def download_video():
    try:
        # User input
        video_url = input("Enter YouTube Video URL: ")
        destination = input("Enter Destination Folder Path: ")

        # Create YouTube object
        yt = YouTube(video_url)

        print("\nVideo Title:", yt.title)
        print("Downloading...")

        # Get highest resolution stream
        stream = yt.streams.get_highest_resolution()

        # Download video
        stream.download(output_path=destination)

        print("\nDownload Completed Successfully!")

        # Example usage of numpy, pandas, matplotlib
        # (For learning purpose)

        # Create sample download statistics
        data = {
            "Metric": ["Video Length", "Views (Approx)"],
            "Value": [yt.length, yt.views]
        }

        # Create DataFrame
        df = pd.DataFrame(data)

        print("\nVideo Statistics:")
        print(df)

        # Convert values using numpy
        values = np.array(df["Value"])

        # Plot graph
        plt.figure(figsize=(6, 4))
        plt.bar(df["Metric"], values)
        plt.title("YouTube Video Statistics")
        plt.xlabel("Metrics")
        plt.ylabel("Values")
        plt.show()

    except Exception as e:
        print("\nError Occurred!")
        print("Reason:", e)
        print("Please check the YouTube link or folder path.")

# Run program
download_video()# youtube-video-downloader-