# Client site content

This repo holds one website's content: text, images and settings. The design
and code come from [lemon-real-estate-engine](https://github.com/AllThingsLemon/lemon-real-estate-engine),
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

Follow the new-client checklist in the engine's
[setup guide](https://github.com/AllThingsLemon/lemon-real-estate-engine/blob/main/docs/SETUP.md#adding-a-new-client).
In short:

1. Create this repo from the template in the client's GitHub org (private).
2. Edit `site.config.json`: `repo` and `siteUrl`. `authUrl` is already set to
   the shared sign-in Worker.
3. Approve the **Lemon Real Estate Site Editor** OAuth app in the client's org,
   or the editor will say it has no access to the repo.
4. Create the Cloudflare Pages project with the build settings from the guide.
5. Add the site's hostnames to the sign-in Worker's `ALLOWED_DOMAINS`.
6. Add the project's deploy hook to the engine's `DEPLOY_HOOKS` secret.
7. Replace the demo content, or let the client do it in the editor.
