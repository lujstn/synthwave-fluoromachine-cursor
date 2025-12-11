# Releasing Synthwave Fluoromachine (Cursor/VS Code)

This document explains how to cut a new release and publish it to:

- GitHub Releases (with a `.vsix` asset)
- VS Marketplace
- Open VSX

The goal: **build one `.vsix` file and reuse it everywhere** so GitHub, VS Marketplace, and OpenVSX always match.

---

## 0. Prerequisites (one-time setup)

### CLI tools (local)

```bash
npm install
npx vsce --version   # VS Marketplace CLI
npx ovsx --version   # Open VSX CLI
```

You don’t need them globally; `npx` will use the project-local versions if added, or a temporary one otherwise.

### Tokens

- **VS Marketplace**
  - Ensure you have a Personal Access Token (PAT) as per VS Code docs.
  - Set this as an environment variable when publishing:

    ```bash
    export VSCE_PAT="your-marketplace-token"
    ```

- **Open VSX**
  - Log in to `open-vsx.org` and generate an access token::

    ```bash
    export OVSX_PAT="your-openvsx-token"
    ```

---

## 1. Prepare `main`

Make sure `main` is clean and up to date:

```bash
git checkout main
git pull origin main
```

Commit all changes (README updates, docs, etc.) that should go into this release.

---

## 2. Bump the version

1. Open `package.json`.
2. Update the `version` field, e.g.:

   ```json
   "version": "0.2.1"
   ```

3. Commit the change:

   ```bash
   git add package.json
   git commit -m "chore: bump version to 0.2.1"
   ```

(For future releases, replace `0.2.1` with the new version number.)

---

## 3. Tag the release

Create a git tag that matches the version (recommended format: `vX.Y.Z`):

```bash
git tag v0.2.1
git push origin main --tags
```

For future releases, use the matching tag name, e.g. `v0.3.0`.

This tag will be used for the GitHub Release.

---

## 4. Build the VSIX

From the repo root:

```bash
npm install          # if not already done
npx vsce package
```

This will produce a file like:

```text
synthwave-fluoromachine-cursor-0.2.1.vsix
```

> Note: `.vsix` files are **ignored by git** via `.gitignore`. They are only temporary build artifacts.

---

## 5. Publish the exact same VSIX everywhere

### 5.1 VS Marketplace

Use `vsce publish` with `--packagePath` so it uploads the **same** `.vsix` you just built:

```bash
export VSCE_PAT="your-marketplace-token"

npx vsce publish --packagePath synthwave-fluoromachine-cursor-0.2.1.vsix
```

This uses the `version` from `package.json` and the contents of the `.vsix` file you built.

### 5.2 Open VSX

Use `ovsx` to publish the **same** file:

```bash
export OVSX_PAT="your-openvsx-token"

npx ovsx publish synthwave-fluoromachine-cursor-0.2.1.vsix -p "$OVSX_PAT"
```

---

## 6. Create the GitHub Release

1. Go to the GitHub repo’s **Releases** page.
2. Click **“Draft a new release”**.
3. Select the tag `v0.2.1` (created earlier).
4. Title it something like `v0.2.1`.
5. Add release notes (high-level summary of changes).
6. Upload `synthwave-fluoromachine-cursor-0.2.1.vsix` as a **release asset**.
7. Publish the release.

Now:

- `main` contains the source code at version `0.2.1`
- The git tag `v0.2.1` points to that commit
- VS Marketplace has `0.2.1`
- OpenVSX has `0.2.1`
- GitHub Release `v0.2.1` has the matching `.vsix` file

Everything is in sync.

---

## 7. README & docs consistency

After releasing, sanity-check:

- The **README** in this repo:
  - Any install snippet that referenced a specific `.vsix` filename should either:
    - Use a generic command, e.g.:

      ```bash
      code --install-extension lujstn.synthwave-fluoromachine-cursor
      cursor --install-extension lujstn.synthwave-fluoromachine-cursor
      ```

      (preferred), or

      ```bash
      # If installing manually from GitHub Releases
      code --install-extension synthwave-fluoromachine-cursor-0.2.1.vsix
      cursor --install-extension synthwave-fluoromachine-cursor-0.2.1.vsix
      ```

- VS Marketplace & OpenVSX pages:
  - Make sure descriptions roughly match the README, especially instructions mentioning version numbers.

---

## 8. Quick checklist (TL;DR)

For each new version `X.Y.Z`:

1. Update `package.json` → `"version": "X.Y.Z"`
2. `git commit -am "chore: bump version to X.Y.Z"`
3. `git tag vX.Y.Z` + `git push origin main --tags`
4. `npx vsce package` → generate `.vsix`
5. `npx vsce publish --packagePath <that .vsix>`
6. `npx ovsx publish <that .vsix> -p "$OVSX_PAT"`
7. Create GitHub Release for `vX.Y.Z` and attach the `.vsix`
8. Verify Marketplace/OpenVSX show version `X.Y.Z`
