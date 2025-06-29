## 🎙️ How This Private Podcast Feed Works

This repository hosts an **RSS feed** to turn audiobook MP3 files into a podcast you can subscribe to in Apple Podcasts or any other podcast app.

### ✅ **How it was set up**

1. **MP3 Files**

   * Hosted on Google Drive with direct download links (`https://drive.google.com/uc?export=download&id=...`).

2. **RSS Feed (`feed.xml`)**

   * Created a valid RSS 2.0 file with:

     * `<channel>` metadata (title, description, language).
     * `<item>` entries for each episode (title, enclosure, description, pubDate).
     * `<guid>` tags to uniquely identify episodes.
     * `<itunes:image>` tag to specify cover art.

3. **Cover Art**

   * Created a square PNG image (1536×1536 px, RGB color).
   * Hosted the image on GitHub Pages.
   * Added `<itunes:image href="..."/>` to ensure artwork displays in Apple Podcasts.

4. **Validation**

   * Tested the feed with [Cast Feed Validator](https://castfeedvalidator.com) and [Podba.se](https://podba.se/validate/) to confirm no errors.
   * Confirmed all MP3 and image URLs are publicly accessible and properly escaped (`&amp;`).

5. **Hosting**

   * Published `feed.xml` and the cover image via GitHub Pages.
   * The feed URL is:

     ```
     https://joaopcoelho.github.io/audiobooks-as-podcasts/feed.xml
     ```

6. **Subscribing**

   * In Apple Podcasts, used “Add a Show by URL” and pasted the feed link.
   * Artwork may take 24–48 hours to appear due to Apple’s caching.
   * To force a refresh, renaming the image file (e.g., `cover-v2.png`) and updating the `<itunes:image>` tag can help.

---

✅ **How to add new episodes**

* Download the audiobook using yt-dlp (e.g. `yt-dlp -x --audio-format mp3 <youtube-url>`)
* Upload the MP3 file to Google Drive.
    * If file is more than 100mb - split it using Audacity.
* Create a new `<item>` block in `feed.xml` with:
  * Title
  * Enclosure URL (Google Drive direct link)
  * Unique `<guid>`
  * Description
  * `pubDate`
* Re-upload `feed.xml`.
* Validate again if needed.