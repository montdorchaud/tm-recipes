# Thermomix recipe site

A tiny GitHub Pages site that turns short recipe files into pages Cookidoo can import
with "Created recipes → + → Import recipe".

## Files

- `_recipes/` – one `.md` file per recipe (this is your library; add as many as you like)
- `_layouts/recipe.html` – builds the recipe page and the schema.org Recipe data Cookidoo reads
- `_includes/settings.html` – turns time/temp/speed into Thermomix notation (`20 min/100°C/reverse/speed soft`)
- `_config.yml` – site title, `baseurl` and settings language
- `PROMPT.md` – instructions for the LLM that writes the recipe files

## One-time setup

1. Create a GitHub account and a new **public** repository named `tm-recipes`.
   (Free accounts can only publish Pages from public repos, so the recipes are visible to anyone with the link.)
2. Upload the files, keeping the folders:
   - Computer: unzip, then drag the whole folder content onto the repo page ("uploading an existing file").
   - Phone only: use *Add file → Create new file* for each file. Typing `_layouts/base.html`
     as the name creates the folder automatically. Paste the file content and commit.
3. Repo *Settings → Pages*: Source "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
4. After a minute or two the site is live at `https://YOUR-USERNAME.github.io/tm-recipes/`.
   If you named the repo differently, change `baseurl` in `_config.yml` to `"/your-repo-name"`.
5. Set `tm_lang` in `_config.yml` to the language of your Cookidoo account (`en` or `de`),
   and the same LANGUAGE in the LLM prompt.

## Test before anything else

Open the example curry page, tap "Copy link for Cookidoo", and import it in Cookidoo.
Check that the ingredients came through and that the steps show time, temperature and speed.
If the settings are not detected, try the other `tm_lang` value first; if the importer rejects the
URL altogether, it may not accept arbitrary sites, and you would edit the settings in Cookidoo by hand
or use a different import route.

## Adding a recipe from your phone

1. Ask the LLM (with PROMPT.md as its instructions) for a recipe.
2. Copy the filename and the code block.
3. In the repo, open `_recipes`, tap *Add file → Create new file*, type the filename, paste, *Commit changes*.
4. Wait 1–2 minutes (the *Actions* tab shows when the build is done).
5. Open the site, pick the recipe, tap "Copy link for Cookidoo", paste it into Cookidoo's import field,
   check the settings, save.
6. When you're done with it, delete it from Cookidoo. It stays in your library here.

Always supervise the first cook of a new recipe: the LLM can still get quantities or settings wrong.
