# Publish “A Universe of Reasons — For My Devi”

This is a single-page site: the styling and JavaScript live inside `index.html`. The five songs and the 37 numbered photos are supporting files beside it.

## Create a separate GitHub repository

1. Sign in to GitHub and choose **New repository** from the **+** menu.
2. Give the repository a new name, such as `a-universe-for-devi`. Choose **Public** so GitHub Pages and the photo-reading endpoint work without sign-in. You can initialize it with a README.
3. Create this repository as a new, empty project. Do not choose **Import repository**, and do not open or change any of your existing repositories.
4. In the new repository, choose **Add file → Upload files**. Upload the contents of the delivered `outputs` folder so `index.html` and `song1.mp3` through `song5.mp3` are at the repository root, and the 37 images are inside `photos/`.
5. Commit those files to the new repository's `main` branch.

The folder layout should look like this:

```text
index.html
song1.mp3
song2.mp3
song3.mp3
song4.mp3
song5.mp3
photos/
  1.jpeg
  2.jpeg
  ...
  37.jpeg
```

## Turn on GitHub Pages

1. Open **Settings → Pages** in the new repository.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Select branch **main** and folder **/(root)**, then click **Save**.
4. Wait for GitHub to finish its first deployment. The Pages address appears on the same settings page. A project site normally uses `https://YOUR-USERNAME.github.io/REPOSITORY-NAME/`.
5. Open that address on a phone or computer. Enter the page password to fade into the sky and start a randomly selected song. A play/pause button is available if the browser still blocks automatic playback.

## Add photos later

The constellation automatically lists image files in the repository's `photos/` folder through GitHub's public Contents API. When that request is unavailable, it looks for numbered files such as `photos/1.jpg`, `photos/2.jpg`, or the matching `.jpeg`, `.png`, `.webp`, and `.gif` versions. The viewer fits the complete photo inside the frame instead of cropping it. Six bundled images had black video bars trimmed from the delivered copies so those bars do not hide the pictures. It assigns a different built-in love note to each photo star.

To use **Add stars** from the page:

1. Open **Add stars** and unlock the keeper panel with the page password.
2. Enter the GitHub username and the new repository name. These are filled in automatically for a standard `github.io` address; enter them yourself if you use a custom domain.
3. Create a **fine-grained personal access token** on GitHub. Limit it to this new repository and grant **Contents: Read and write**. Set an expiration date that suits you.
4. Paste the token into the page, select multiple image files, and choose **Add to the sky**. Each photo is committed into `/photos` in the new repository.

The token is stored in `sessionStorage` for that browser tab only. Use a token limited to this one repository; remove it from the tab with **Lock** and close the tab when finished. To revoke it, use GitHub's personal access token settings.

## Personalize the notes

The page includes 365 built-in reasons. To supply your own, add a `reasons.json` file beside `index.html`, then commit it to `main`:

```json
{
  "reasons": [
    "I love how you make the quiet feel like company.",
    "You remember the little things, and that makes me feel cared for."
  ]
}
```

You can also use a plain JSON array of strings. If the file is absent or invalid, the 365 built-in notes are used. With a custom list, notes repeat as needed to pair with the photos.

## Preview before publishing

You can open `index.html` directly in a browser. If the browser restricts local files, run a small local web server from the delivered folder instead:

```powershell
py -m http.server 8000
```

Then visit `http://localhost:8000`. On macOS or Linux, use `python3 -m http.server 8000`.

## A note about the password

GitHub Pages is a static host. The password screen is a sweet front-end gate; anyone can inspect its page source or request its public photos and songs without entering the password. Do not put private or sensitive images in a public Pages repository. The password also appears in the page's JavaScript so the browser can check it. True private access requires a server or an authentication service that protects the files themselves.
