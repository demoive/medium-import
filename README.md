# Medium Backdater

A lightweight tool to backdate Medium articles using Medium's "Import a Story" feature. Hosted entirely on GitHub Pages.

## How It Works
Medium's story importer reads the metadata of the external link you provide. This tool uses a static `article:published_time` meta tag (set to 12:00 PM Noon) within an HTML file to inject a past timestamp before Medium's scraper evaluates the page. 

Because Medium aggressively caches URLs you have imported in the past—saving both the content and the timestamp attached to that specific link—**changing the file name/URL is a strict requirement for every new post you want to import.**

## How to Setup
1. Enable GitHub Pages for this repository:
   * Go to **Settings** > **Pages**.
   * Set the deployment source branch to **main** (or `master`) and folder to **/(root)**.
   * Click **Save**.
2. Copy your base live deployment URL provided by GitHub.

## How to Use

To bypass Medium's permanent cache, you must use a unique file name for every single article you want to backdate.

1. Create a copy of your `index.html` file in this repository (e.g., duplicate it and name it something unique like `post-2021-04-18.html`).
2. Open the new file and manually edit the date value inside the content attribute of the meta tag to your desired past date (keep the `T12:00:00.000Z` suffix intact):
   ```html
   <meta id="medium-date" property="article:published_time" content="2021-04-18T12:00:00.000Z">
   ```
3. Commit and push the new file to your GitHub repository.
4. Navigate to your new unique live URL in your browser to ensure it resolves (e.g., `https://github.io`).
5. Go to your Medium profile dashboard and navigate to **Stories** > **Import a story**.
6. Paste your unique file URL and click **Import**.
7. Replace the placeholder text with your actual content and publish.
8. Highly recommended: in the Advanced Settings for you page, disable the **Customize Canonical Link**
