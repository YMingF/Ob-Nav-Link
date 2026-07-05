# Notion Obsidian Opener

A tiny static page for opening local Obsidian links from tools that only accept normal web URLs, such as Notion.

The page accepts an encoded `obsidian://...` URI in the `to` query parameter:

```text
https://<your-github-username>.github.io/notion-obsidian-opener/?to=<encoded-obsidian-uri>
```

When opened, it validates the target, tries to open Obsidian, and shows a manual fallback button.

## Use With Stable Obsidian Links

For links that survive note rename or move, use the Obsidian Advanced URI plugin with a `uid` stored in the note frontmatter:

```yaml
---
uid: 45ca8d03-a345-4053-b491-6ab1500e344a
---
```

The Obsidian URI can then use the UID instead of the file path:

```text
obsidian://advanced-uri?vault=ObRepo&uid=45ca8d03-a345-4053-b491-6ab1500e344a
```

After URL encoding, the Notion link looks like this:

```text
https://<your-github-username>.github.io/notion-obsidian-opener/?to=obsidian%3A%2F%2Fadvanced-uri%3Fvault%3DObRepo%26uid%3D45ca8d03-a345-4053-b491-6ab1500e344a
```

## Local Test

Open `index.html` directly, paste an `obsidian://...` URI into the form, and generate a Notion link.

To test through a local static server:

```bash
python3 -m http.server 8080
```

Then open:

```text
http://127.0.0.1:8080/?to=obsidian%3A%2F%2Fadvanced-uri%3Fvault%3DObRepo%26uid%3D45ca8d03-a345-4053-b491-6ab1500e344a
```

## Push To GitHub

This project directory is already initialized as a Git repository. If you create a fresh copy elsewhere, run `git init -b main` first.

```bash
git add index.html README.md .gitignore
git commit -m "Create Obsidian opener"
git remote add origin git@github.com:<your-github-username>/notion-obsidian-opener.git
git push -u origin main
```

## Enable GitHub Pages

1. Open the GitHub repository.
2. Go to `Settings` -> `Pages`.
3. Set `Source` to `Deploy from a branch`.
4. Select branch `main` and folder `/root`.
5. Save.

After GitHub Pages is live, use:

```text
https://<your-github-username>.github.io/notion-obsidian-opener/
```

## Privacy

The page has no backend and does not store links. The encoded Obsidian URI is still visible in the browser URL, so avoid putting sensitive note titles or vault names in shareable links when that matters.
