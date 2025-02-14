# export_dropbox_paper_files_as_markdown

A Go tool to export Dropbox Paper documents to Markdown format while preserving their folder structure.

## Overview

This tool connects to your Dropbox account and exports all Paper documents within a specified folder to Markdown format. It maintains the original folder hierarchy in the exported files, making it ideal for migrating Paper documents to other platforms or maintaining local backups.

## Prerequisites

- Go 1.23 or higher
- A Dropbox account with Paper documents
- Dropbox API access token with the required permissions

## Setup

1. Clone the repository and navigate to the directory
2. Install dependencies:
```bash
go get github.com/dropbox/dropbox-sdk-go-unofficial/v6/dropbox
```

3. Set up your Dropbox access token:
    - Create an app in the [Dropbox App Console](https://www.dropbox.com/developers/apps)
    - Generate an access token with files.content.read permission
    - Set the token as an environment variable:
```bash
export DROPBOX_ACCESS_TOKEN='your_access_token_here'
```

## Usage

Run the program with optional debug mode:

```bash
# Normal mode
go run main.go

# Debug mode for verbose logging
go run main.go -debug
```

By default, the tool will:
- Look for Paper documents in the "/Migrated Paper Docs" folder in your Dropbox
- Export all files with `.paper` extension to Markdown format
- Save the exported files in an `output_paper_markdown` directory
- Preserve the original folder structure

## Output

The exported files will be organized as follows:
```
output_paper_markdown/
  ├── folder1/
  │   ├── doc1.md
  │   └── doc2.md
  └── folder2/
      └── doc3.md
```

## Error Handling

The tool includes robust error handling:
- Logs errors for individual file export failures but continues processing
- Creates necessary directories automatically
- Validates the access token before starting
- Provides detailed debug logging when enabled

## Limitations

- Only exports files with `.paper` extension
- Requires appropriate Dropbox API permissions
- Some Paper-specific formatting may not translate perfectly to Markdown

