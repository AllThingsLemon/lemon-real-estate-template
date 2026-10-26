# Client site content

This repo holds one website's content: text, images and settings. The design
and code come from [lemon-real-estate-engine](https://github.com/allthingslemon/lemon-real-estate-engine),
which is combined with this repo when the site builds.

**Editing the site?** Go to `https://<your-site>/admin/` and sign in with
GitHub. See [EDITING.md](EDITING.md).

## Layout

```
site.config.json            technical settings (repo, live URL). Don't edit in the CMS.
content/settings/
  general.json              branding, colors, fonts, menu, footer
  home.json                 home page text and FAQ
  publishing.json           how changes go live
content/listings/*.md       one file per listing
content/categories/*.json   one file per category
content/pages/*.md          About, Privacy Policy, Terms, ...
public/uploads/             every image and file
public/                     anything else served as-is (robots.txt, favicon.ico)
```

## New client setup (for the site manager)

1. Create this repo from the template in the client's GitHub organization.
2. Edit `site.config.json`: `repo` (`org/repo`) and `siteUrl`. `authUrl` is
   already set to the shared sign-in Worker (`lemon-cms-auth`).
3. Replace the demo content and images, or let the client do it in the CMS.
4. Create a Cloudflare Pages project connected to this repo:
   - Build command: `git clone --depth 1 https://github.com/allthingslemon/lemon-real-estate-engine.git engine && cd engine && npx -y pnpm@10.10.0 install --frozen-lockfile && CLIENT_DIR=.. npx -y pnpm@10.10.0 build`
   - Build output directory: `engine/dist`
   - Environment variable: `NODE_VERSION=24`
5. Add the live hostname to `ALLOWED_DOMAINS` in the sign-in Worker's
   `wrangler.toml` and redeploy it.
6. Invite editors to the GitHub org with Write access to this repo.
