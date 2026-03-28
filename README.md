# iwwwanow / ui-kit

Minimal dark-first component library. Design language from [owo](https://github.com/iwwwanow/owo) + [xtc-toaster](https://github.com/iwwwanow/xtc-toaster).

**Preview →** https://iwwwanow.github.io/iwwwanow_ui-kit

---

## Usage

```html
<link rel="stylesheet" href="kit.css">
```

Then use CSS classes directly in your HTML — see `index.html` for all examples.

---

## Components

| Component | Classes |
|-----------|---------|
| Button | `.btn` + `.btn-primary` / `-secondary` / `-ghost` / `-outline` / `-danger` · `.btn-sm` `.btn-lg` |
| Input | `.input` · `.input--error` `.input--success` · `.input-sm` `.input-lg` |
| Textarea | `.textarea` |
| Select | `.select` |
| Checkbox | `.checkbox` wrapping `<input type="checkbox">` |
| Radio | `.radio` wrapping `<input type="radio">` |
| Toggle | `.toggle` · `.toggle__track` · `.toggle__thumb` |
| Card | `.card` · `.card-header` `.card-body` `.card-footer` · `.card-hover` |
| Badge | `.badge` + `.badge-accent` / `-success` / `-warning` / `-error` / `-info` · `.badge-dot` |
| Tag | `.tag` · `.tag-active` · `.tag-close` |
| Alert | `.alert` + `.alert-success` / `-warning` / `-error` / `-info` |
| Progress | `.progress` → `.progress-bar` · `.progress-success` / `-warning` / `-info` · `.progress-lg` |
| Range | `.range` |
| Table | `.table-wrapper` → `.table` |
| Tabs | `.tabs` → `.tab-item` + `.active` |
| Avatar | `.avatar` · `.avatar-sm` / `-md` / `-lg` / `-xl` · `.avatar-accent` |
| Toast | `.toast` + `.toast-accent` / `-success` / `-warning` / `-error` |
| Breadcrumbs | `.breadcrumbs` → `.breadcrumb-item` · `.breadcrumb-sep` |
| Tooltip | `.tooltip-wrapper` → `.tooltip` (pure CSS hover) |
| Spinner | `.spinner` · `.spinner-sm` · `.spinner-lg` |
| Code/Kbd | `<code>` `<pre>` `<kbd>` |
| Divider | `.divider` · `.divider-label` |

---

## Design tokens (CSS variables)

```css
/* Backgrounds */
--bg          #0d0d0d
--surface     #1a1a1a
--surface-2   #222222
--surface-3   #2a2a2a

/* Borders */
--border        #2e2e2e
--border-hover  #444444

/* Text */
--text        #e0e0e0
--text-muted  #a4a4a4
--text-dim    #535353

/* Accent */
--accent      #ff115c
--accent-dim  rgba(255,17,92,0.12)

/* Status */
--success  #00ff9b
--warning  #ff9b00
--error    #ff2c2c
--info     #009bff

/* Misc */
--font        'Roboto Condensed', sans-serif
--mono        'Roboto Mono', monospace
--transition  0.15s ease
--radius      4px
--radius-lg   8px
```

---

## Deploy to GitHub Pages

### Option A — автоматически через Actions (рекомендуется)

1. Пуш репозитория на GitHub.

2. Создай файл `.github/workflows/pages.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [master]

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: true

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v5
      - uses: actions/upload-pages-artifact@v3
        with:
          path: .
      - uses: actions/deploy-pages@v4
        id: deployment
```

3. В настройках репозитория (`Settings → Pages`):
   - **Source**: `GitHub Actions`

4. После первого пуша через ~30 секунд сайт доступен по адресу:
   `https://<username>.github.io/<repo-name>/`

---

### Option B — вручную через ветку `gh-pages`

```bash
# Один раз
git checkout --orphan gh-pages
git rm -rf .

# Скопируй файлы в ветку
git checkout master -- index.html kit.css
git add index.html kit.css
git commit -m "deploy"
git push origin gh-pages
```

В `Settings → Pages` выбери:
- **Source**: `Deploy from a branch`
- **Branch**: `gh-pages` / `/ (root)`

---

### Option C — из папки `/docs`

```bash
mkdir docs
cp index.html kit.css docs/
git add docs/
git commit -m "add docs"
git push
```

В `Settings → Pages`:
- **Source**: `Deploy from a branch`
- **Branch**: `master` / `/docs`

---

## Structure

```
iwwwanow_ui-kit/
├── index.html     # showcase / preview page
├── kit.css        # the UI kit — drop this into your project
└── README.md
```
