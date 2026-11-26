# nancy_cake

Website for **Nancy Cake House**, a patisserie in Madhavaram, Chennai: *Baked with love*.

- `index.html`: the single-page site (menu & price list, gallery, Instagram reels, WhatsApp order form, map)
- `content/gallery.json`: "Our Creations" photos (newest first; the site shows the first 24)
- `content/reels.json`: Instagram reels section (newest first; the site shows the first 6)
- `admin/`: the admin page where the client updates the gallery and reels without code
- `images/`: logo and cake photos (see `images/README.txt`). Photos uploaded from the admin page go in `images/uploads/`.

## Preview locally
The gallery and reels load from `content/*.json`, so double-clicking `index.html` won't show them.
Run a tiny local server instead:

    python -m http.server 8000      # then open http://localhost:8000

## Hosting on Netlify (one-time setup, about 10 minutes)
1. On netlify.com, choose **Add new site → Import from Git → GitHub**, then pick `Jothiselvi11/nancy_cake`.
   Leave the build command empty and set the publish directory to `.` (the repo root).
2. Admin login (GitHub OAuth):
   - On GitHub, go to **Settings → Developer settings → OAuth Apps → New OAuth App**.
     Homepage URL: your Netlify site URL. Callback URL: `https://api.netlify.com/auth/done`.
   - Copy the Client ID, create a Client Secret, and copy that too.
   - In Netlify, go to **Site configuration → Access & security → OAuth → Install provider → GitHub**
     and paste the ID and secret.
3. The client needs a free GitHub account. Add it as a collaborator on the repo
   (**GitHub repo → Settings → Collaborators → Add people**, with write access).
4. Optional: connect a custom domain in Netlify.

On Netlify, photos are automatically resized for fast loading (Netlify Image CDN), so the client can upload full-size phone photos.

## For the client: updating the website
1. Open **yoursite/admin** on your phone or computer and tap **Login with GitHub**.
2. **🎂 Our Creations**: tap **Add cake photo**, upload the photo, type a caption, choose a category, then tap **Publish → Publish now**.
   New photos appear first. Once there are more than 24, the oldest are hidden automatically.
3. **🎬 Instagram reels**: on Instagram, open the reel and tap **Share → Copy link**.
   In the admin page, tap **Add reel** and paste the link. A cover photo is optional: without one, the site shows the reel's own Instagram player.
   Then tap **Publish → Publish now**. The site shows the newest 6 reels.
4. The live website updates about a minute after you publish.
