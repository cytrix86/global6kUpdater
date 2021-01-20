## Table of contents
* [General info](#general-info)
* [Setup](#setup)
* [Usage](#usage)

## General info
GlobalUpdater is a Commandline tool to generate Update Media for the Rockwell Colins Fusion 
	

## Setup
To run this project, install it locally using homebrew.

If you don't have homebrew installed follow the [Homebrew Installation Guide](http://brew.sh).

### Installation
```
brew tap cytrix86/homebrew-tap
brew install global6kupdater
```

## Usage

The required flags are:
-s  Path to the Source floder containing the .exe files to be processed. <br />
    <span style="color:red">Note: All exe files in this folder will be processed.</span>

-d Path to destination Folder / Volume <br />
    <span style="color:red">Note: All files at the destination will be erased.</span>

```
globalupdater -s ~/Downloads/FilesToProcess -d /Volumes/MemoryStick
```