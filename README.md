# Eric Ho — Portfolio

Plain HTML/CSS. No build step and nothing to install.

```
index.html              main page (all resume sections)
style.css               styling (auto light/dark mode)
projects/osu-robot.html osu! Robot project page
projects/radar.html     Arduino Radar project page
assets/                 put photos and videos here
Eric_Ho_Resume.pdf      your resume (linked from the "Resume" button)
```

## 1. Put it online with GitHub Pages (free)

1. Sign in to GitHub as **ericho235**.
2. Create a new **public** repository named exactly `ericho235.github.io`.
3. Click **uploading an existing file**, drag in everything from this folder (including the `projects` and `assets` folders), and click **Commit changes**.
4. Go to **Settings → Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, Branch to **main** and folder to **/ (root)**, then click **Save**.
5. After a minute or two, the site is live at `https://ericho235.github.io`.

## 2. Connect a custom domain

### Buy a domain
Use any registrar, for example Cloudflare Registrar, Porkbun or Namecheap. Something like `ericho.dev` or `ericho.com` costs roughly $10–15 a year.

### Add DNS records at your registrar
In your registrar's DNS settings, add these records. If you're using Cloudflare, set each one to **DNS only** (grey cloud).

| Type  | Name / Host | Value |
|-------|-------------|-------|
| A     | `@`         | `185.199.108.153` |
| A     | `@`         | `185.199.109.153` |
| A     | `@`         | `185.199.110.153` |
| A     | `@`         | `185.199.111.153` |
| AAAA  | `@`         | `2606:50c0:8000::153` |
| AAAA  | `@`         | `2606:50c0:8001::153` |
| AAAA  | `@`         | `2606:50c0:8002::153` |
| AAAA  | `@`         | `2606:50c0:8003::153` |
| CNAME | `www`       | `ericho235.github.io` |

Delete any default "parking" A or CNAME records the registrar added for `@` or `www`.

### Tell GitHub about it
1. In the repository, go to **Settings → Pages → Custom domain**, enter your domain (for example `ericho.dev`) and click **Save**. GitHub creates a `CNAME` file in the repository for you.
2. Wait for the DNS check to pass. This is usually a few minutes but can take up to 24 hours.
3. Tick **Enforce HTTPS**. If it's greyed out, wait a bit longer for the certificate to be issued.

### Recommended: verify the domain
Go to **GitHub → your profile Settings → Pages → Add a domain**. GitHub gives you a TXT record to add at your registrar. This stops anyone else from claiming your domain on GitHub.

### Check it's working
- `https://yourdomain` and `https://www.yourdomain` should both load the site.
- On Mac, running `dig yourdomain +short` in Terminal should list the four `185.199.x.153` addresses.

## 3. Editing later

- Edit a file directly on GitHub (pencil icon) and commit. The site updates in about a minute.
- Or clone the repository, edit it in VS Code, then `git push`.
- **Add a demo video:** put `osu-demo.mp4` in `assets/`, then in `projects/osu-robot.html` replace the `media-placeholder` div with:
  `<video src="../assets/osu-demo.mp4" controls muted playsinline></video>`
  GitHub rejects files over 100 MB and warns above 50 MB. For long videos, upload to YouTube and embed them instead.
- Boxes with an orange left border are **TODO notes** to fill in. Remove them once each section is written.
- **Add a new project:** copy `projects/radar.html`, edit it, and add a `<article class="card">` for it in the Projects section of `index.html`.
