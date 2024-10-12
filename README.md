# Daily Random xkcd

## About
This repository generates a daily random xkcd comic and serves it as an RSS feed. Each day, a new comic is fetched, formatted, and made available for subscription. Users can configure RSS.app to send email notifications whenever a new comic is available in the RSS feed. The application also keeps track of seen comics in a JSON file to ensure uniqueness in the feed.

## Features
- Automatically fetches a random xkcd comic daily.
- Generates an RSS feed that updates with new comic details.
- Tracks seen comics in `seen_comics.json` to avoid duplication.
- Sends email notifications via RSS.app whenever a new comic is published.

## How It Works
1. A GitHub Actions workflow is triggered daily at 8:00 AM UTC+3 to run a Python script (`generate_rss.py`).
2. The script fetches a random comic from the xkcd API, ensuring that it hasn't been seen before.
3. The comic details are formatted in an XML structure and saved to `xkcd_feed.xml`.
4. The seen comics are tracked in `seen_comics.json`, allowing the script to remember which comics have already been shown.
5. The RSS feed is hosted on GitHub, allowing easy access for RSS.app.
6. An RSS.app service monitors the RSS feed and sends an email whenever a new comic is detected.

## Setup Instructions
1. **Fork this repository** to your own GitHub account.
2. **Enable GitHub Actions** in your forked repository.
3. **Set up RSS.app**:
   - Create a new RSS feed alert for the URL: `https://raw.githubusercontent.com/{your_username}/daily-random-xkcd/main/xkcd_feed.xml`
   - Configure the email notifications according to your preferences.
4. **Watch for daily emails** containing the latest xkcd comic!

## Files
- `generate_rss.py`: Python script that fetches a random xkcd comic, tracks seen comics in `seen_comics.json`, and generates the RSS feed.
- `seen_comics.json`: JSON file that stores the IDs of comics that have already been fetched to ensure they are not repeated.
- `.github/workflows/main.yaml`: GitHub Actions workflow configuration that schedules the daily comic update and ensures persistence of seen comics.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements
- [xkcd](https://xkcd.com/) for providing a wealth of comics.
- [GitHub Actions](https://docs.github.com/en/actions) for enabling automated workflows.
- [RSS.app](https://rss.app/) for allowing simple automation of tasks based on web triggers.

## Contact
For questions or suggestions, feel free to open an issue in this repository.
