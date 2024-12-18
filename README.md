# audio_files_organizer_for_iphone
Organize audio files and update their metadata to maintain the original folder structure. Perfect for syncing music to iTunes and Apple Music while preserving album organization. Automates tedious metadata edits, saving time and effort for large audio collections.



# Audio File Metadata Organizer 

### Introduction

#### What is this Script?
This Python script automates the organization and metadata updating of audio files. It helps users who have large audio collections stored in various folder structures maintain those structures when syncing to Apple Music or other music players. The script ensures that albums and songs appear organized, as per the folder hierarchy, on devices like iPhones.

#### Why is it Needed?
Manually editing metadata (like album names, contributing artists, etc.) for large music collections is tedious and error-prone. This script:
- Updates the metadata to match the parent folder's name for each audio file.
- Moves processed files to a single consolidated folder.
- Ensures compatibility with Apple Music/iTunes, maintaining the folder structure on synced devices.
- Saves time by automating repetitive tasks.

#### When to Use It?
Use this script when:
1. You have a large number of audio files organized in a folder structure on your hard disk.
2. You want to maintain the folder hierarchy for albums and tracks on devices like iPhones or iPads.
3. You need metadata corrected without manually editing each file.

#### Who is it For?
- Music enthusiasts with large audio libraries.
- iPhone users syncing music via iTunes/Apple Music.
- Anyone wanting to save time on organizing music collections.

---

### How the Script Works

#### Workflow

1. **Select Base Folder**:
    - The script prompts you to choose a folder containing your audio files. This is the source directory for processing.
    
2. **Scan for Audio Files**:
    - The script recursively scans the base folder for supported audio file formats (.mp3, .wav, .flac, .m4a, etc.).
    - Files shorter than 1 minute in length are skipped.
    
3. **Update Metadata**:
    - For each audio file, the script updates the Album and Artist metadata to match the name of the parent folder.
    - It uses the `mutagen` library to make these changes.
    
4. **Retry Failed Files with Re-Encoding**:
    - If updating metadata fails, the script tries to re-encode the audio file using FFmpeg, ensuring compatibility.
    
5. **Move Processed Files**:
    - Successfully processed files are moved to a folder named `audio songs`, preserving the folder structure, if user prompt's yes then all files will move to target location.
    
6. **Generate Logs**:
    - The script generates logs for:
        - Successfully processed files.
        - Files that failed metadata updates.
        - Files that failed even after re-encoding.
    
7. **Sync to iTunes**:
    - Once all files are moved to the `audio songs` folder, simply drag this folder into iTunes to sync with your iPhone.

---

### Key Features

#### Supported Audio Formats
The script supports a variety of audio formats, including:
- MP3
- WAV
- FLAC
- M4A
- AAC
- OGG
- WMA

#### Folder Structure Preservation
The script ensures that the folder structure in the `audio songs` directory matches the original hierarchy. This guarantees that albums appear grouped correctly in the Apple Music app.

#### Metadata Updates
- **Album Name**: Set to the parent folder name.
- **Contributing Artist**: Also set to the parent folder name, ensuring uniformity across tracks in an album.

#### Error Handling and Re-Encoding
- Files that fail during metadata updates are re-encoded using FFmpeg to resolve compatibility issues.
- A separate log is generated for files that still fail after re-encoding.

#### Size Calculation
The total size of successfully processed files is calculated and displayed, helping ensure there is enough space in the target directory.

---

### Script Components

#### Functions

1. **normalize_path(path)**:
    - Normalizes file paths for cross-platform compatibility.

2. **get_audio_files(base_directory)**:
    - Recursively scans the base directory for audio files in supported formats.

3. **calculate_total_size(file_paths)**:
    - Computes the total size of all successfully processed files.

4. **update_album_metadata(file_path)**:
    - Updates the metadata (Album, Artist) of an audio file.

5. **reencode_audio(file_path, temp_path)**:
    - Re-encodes an audio file using FFmpeg to resolve compatibility issues.

6. **move_audio_files(audio_files, target_folder)**:
    - Moves processed files to the target directory while preserving folder hierarchy.

7. **save_log(file_path, log_data, file_count)**:
    - Saves logs of processed files with timestamps.

8. **process_files(base_directory, target_directory)**:
    - Orchestrates the workflow of scanning, processing, and moving files.

9. **processit()**:
    - Handles user interaction and starts the processing workflow.

---

### Example Usage

#### Scenario
You have a folder structure on your hard drive like this:



Music/ ├── Album1/ │ ├── song1.mp3 │ ├── song2.mp3 ├── Album2/ │ ├── track1.m4a │ ├── track2.wav



You want to:
- Update all metadata so that **Album1's** tracks have the same album name and artist: **Album1**.
- Consolidate everything into a single directory named `audio songs`, while retaining the folder structure.


## Steps to Use the Package

### 1. Install the Package
Install the following packages, run the following commands:

```bash
pip install mutagen
```

```bash
pip install audio-files-organizer-iphone
```

### 2. Run the Script by Importing the Package
After installation, run the script by importing the package and calling the `processit()` function:

```python
from  Audio_files_organizer_for_iphone import Audio_organizer
Audio_organizer.processit()
```

### 3. Select the Base Directory
When prompted, select the `Music/` directory as the base directory.

### 4. Choose the Target Directory
Next, choose a target directory where the `audio songs` folder will be created.

### 5. Once Processing is Complete
After processing is finished:
- Drag the `audio songs` folder into **iTunes**.
- Sync your iPhone to reflect the updated folder structure.

---

### Limitations
- **Album Art**: The script does not handle album artwork. Apple Music may download artwork automatically.
- **File Length Check**: Files shorter than 1 minute are ignored.
- **FFmpeg Dependency**: Ensure FFmpeg is installed and added to your system’s PATH.

---

### System Requirements

- **Python 3.7+**
- Libraries: `os`, `shutil`, `mutagen`, `subprocess`, `datetime`, `tkinter`
- **FFmpeg** for audio re-encoding (optional for re-encoding failed files)

---

### Developer Statement

I am David Sandeep, and I created this script to address my own challenges with organizing and syncing a vast library of audio files. Editing metadata manually was too tedious, so this script became my solution. It processed **34.57 GB** of files, organized them into a folder called `audio songs`, and saved me countless hours. By simply dragging this folder into iTunes, I was able to sync the files to my iPhone 14 Pro Max while maintaining the original folder structure.

If you have a similar need, this script can save you time and ensure your music library stays organized when synced to Apple devices.

