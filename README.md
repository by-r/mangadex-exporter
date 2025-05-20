# MangaDex Library Exporter

A Python tool to export your MangaDex reading list to CSV format. Based on a script by [Sassy-Lily](https://github.com/sassy-lily/mangadex-follows-exporter), posted on [Reddit](https://www.reddit.com/r/mangadex/comments/1kq664i/update_i_created_a_scriptprogram_to_download_your/). 

I modified it with a couple of bug fixes and few new features to suit my needs/preferences.

## Description

This tool authenticates with your MangaDex account and exports your manga library including:
- Manga ID
- Type
- Reading status
- Main title (with language)
- Alternative titles (English, Romaji, Japanese)
- MangaDex URL

## Requirements

- Python 3.1x
- Required packages are listed in `requirements.txt`

## Setup 

1. Clone the repository

2. Create a `.env` file based on `.env.template` with your MangaDex credentials:

    ```sh
    username=your_username
    password=your_password
    client_id=your_client_id
    client_secret=your_client_secret
    ```

    Get the client ID and client secret from [here](https://mangadex.org/settings). 
    1. Go to the API Clients tab
    2. Click "Create"
    3. Fill in the name and description (Optional)
    4. Click "Create" and click on the newly created entry
    5. Copy the client ID (Besides `Active`) and client secret (By Clicking `Get Secrets`)

3. Install dependencies using either uv (recommended) or pip:

    Using `uv`:

    ```sh
    # Install uv if not already installed / linux / macOS
    curl -LsSf https://astral.sh/uv/install.sh | sh

    # Windows
    powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
    # Just follow the instructions
        
    # Install dependencies
    uv pip install -r requirements.txt
    ```

    Using `pip`:

    create and activate the virtual environment:

    ```sh
    python -m venv .venv
    source .venv/bin/activate
    ```

    ```sh
    pip install -r requirements.txt
    ```

## Usage

Run the script:

activate the virtual environment:
```sh
source .venv/bin/activate
```

using `uv`:
```sh 
uv run main.py
```

using `pip`:
```sh
python main.py
```

The script will:
1. Authenticate with MangaDex
2. Fetch your Mangadex Library List
3. Export all entries to `manga_{date_time}.csv`

## Output

The script generates a CSV file (`manga_{date_time}.csv`) with the following columns:
- ID
- Type
- Status
- Main Title Language
- Main Title
- Alternative English Title
- Alternative Romaji Title
- Alternative Japanese Title
- URL