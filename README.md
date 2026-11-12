# chelseapennick.com: how this site works and how to put it on GitHub

This folder is a complete website. It is plain HTML and CSS, so there is no build step and nothing to install. GitHub Pages hosts it for free, and you can edit everything in your web browser.

```
index.html          Home page: intro, research areas, recent publications, news
research.html       Current and past projects, funding, recognition, service
publications.html   Every publication from your CV, with search and filters
talks.html          Presentations and media coverage
style.css           All colors, fonts and spacing (change them at the top)
files/              PDFs: your CV, plus any reports you want to host
images/             Your photo goes here as portrait.jpg
.nojekyll           Tells GitHub to serve the files as-is (leave it)
```

---

## Part 1: Put the site online (about 20 minutes)

### 1. Create a GitHub account
Go to <https://github.com/signup>. Your username becomes part of your free web address. For example, the username `chelseapennick` gives you `chelseapennick.github.io`.

### 2. Create a repository named after your username
1. Click **+** (top right), then **New repository**.
2. Name it exactly **`yourusername.github.io`**, for example `chelseapennick.github.io`.
3. Set it to **Public**. GitHub Pages is free for public repositories.
4. Click **Create repository**.

### 3. Upload the files
1. On the new repository page, click **uploading an existing file**.
2. Unzip the site folder on your computer. Drag in **everything inside it**: the `.html` files, `style.css`, and the `files` and `images` folders.
   - On a Mac, `.nojekyll` is a hidden file. Press `Cmd + Shift + .` in Finder to show it. If you skip it, the site still works.
3. Add your photo as `images/portrait.jpg` (square works best). Until you do, the site shows your initials.
4. Click **Commit changes**.

### 4. Turn on GitHub Pages
1. In the repository, go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to *Deploy from a branch*.
3. Set **Branch** to `main` and the folder to `/ (root)`. Click **Save**.
4. After a minute or two, your site is live at `https://yourusername.github.io`.

You can now look it over before changing anything about your domain.

---

## Part 2: Move chelseapennick.com from Wix to GitHub

Do this only after you're happy with the GitHub version.

### 5. Tell GitHub about your domain
In **Settings → Pages → Custom domain**, enter `chelseapennick.com` and click **Save**. GitHub adds a file named `CNAME` to your repository. Leave that file in place.

### 6. Point the domain at GitHub
How you do this depends on where you bought the domain.

- **If you bought it through Wix:** go to Wix → *Domains* → your domain → *Manage DNS records*. You may first need to disconnect the domain from your Wix site. You can also transfer the domain to a registrar such as Namecheap, Cloudflare or Porkbun, which makes DNS easier to manage.
- **If you bought it elsewhere** (GoDaddy, Google/Squarespace Domains, etc.): open that registrar's DNS settings.

Then set these records, replacing any existing A records for the root domain:

| Type  | Host / Name | Value                    |
|-------|-------------|--------------------------|
| A     | @           | 185.199.108.153          |
| A     | @           | 185.199.109.153          |
| A     | @           | 185.199.110.153          |
| A     | @           | 185.199.111.153          |
| CNAME | www         | yourusername.github.io   |

DNS changes can take from a few minutes to 24 hours to spread.

### 7. Turn on HTTPS
Back in **Settings → Pages**, check **Enforce HTTPS** once the option becomes available. That can take up to a day after the DNS change.

### 8. Wrap up Wix
- Before you cancel your Wix plan, download any PDFs you still want from your old Projects page (final reports, presentations, monitoring reports). Put them in `files/` and link to them from `research.html`. Links to files hosted on Wix stop working once you cancel.
- If the domain renews through Wix, check that canceling the website plan doesn't also cancel the domain.

> **Search engines:** your current Wix site is set to `noindex`, which tells Google not to list it. This is likely why the site is hard to find. The new site has no such setting. To speed things up, you can add it to [Google Search Console](https://search.google.com/search-console).

---

## Part 3: Everyday updates (all in the browser)

To edit any file on GitHub, open it and click the **pencil icon**, make your change, then click **Commit changes**. The live site updates in about a minute.

### Add a new publication
Open `publications.html`, find the right section, and copy an existing entry, which runs from `<li class="pub"` to `</li>`. Paste it at the top of that list, newest first, and change the details:

```html
      <li class="pub" id="J9" data-type="article" data-search="pennick 2027 new title journal name">
        <div class="yr">2027</div>
        <div>
          <div class="title">Your new article title</div>
          <div class="authors"><strong>Pennick, Chelsea S.</strong>; Coauthor, Name A.</div>
          <div class="venue">Journal Name 12(3): 45-67</div>
          <div class="actions"><a href="https://doi.org/10.xxxx/xxxxx">DOI</a></div>
        </div>
      </li>
```

- **`id`** must be unique. Other pages link to it, for example `publications.html#J9`.
- **`data-type`** is one of `article`, `technical`, `report` or `writing`. It controls the filter buttons.
- **`data-search`** holds the words the search box matches. Lowercase is fine.
- For a paper under review, use `<div class="yr">—</div>` and add `<span class="status">Under review</span>` after the title.
- To link a PDF you host yourself, upload it to `files/` and use `<a href="files/your-report.pdf">PDF</a>`.

Also update the counts in the filter buttons, for example `Articles (8)`, and on the home page stats.

### Add a news item
In `index.html`, copy a `<li>` in the **News** list and edit it.

### Update your CV
Upload a new PDF to `files/` with the same name, `Pennick_CV.pdf`. GitHub replaces the old one.

### Change colors or fonts
Edit the values at the top of `style.css`. For example, `--accent` is the forest green.

### Preview before publishing (optional)
Double-click any `.html` file on your computer and it opens in your browser exactly as it will look online.

---

## Want more automation later?
If you find yourself adding publications often, you can move to a GitHub Pages template that builds the publication list from a BibTeX file. Two popular ones are [al-folio](https://github.com/alshedivat/al-folio) and [academicpages](https://github.com/academicpages/academicpages.github.io). They take more setup. This plain-HTML version is easier to learn on and has no moving parts.
