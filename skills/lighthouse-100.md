---
name: lighthouse-100
description: "Automated audit-fix-verify loop until every Lighthouse category hits 100/100/100 on Accessibility, Best Practices, and SEO"
---

# /lighthouse-100 — Perfect Lighthouse Scores

Automated audit-fix-verify loop until every Lighthouse category hits 100.

```
/lighthouse-100 [url-or-file]
```

---

## Step 0: Browser Check

This skill requires Chrome DevTools MCP for Lighthouse audits:

1. **Check for Chrome DevTools MCP** — look for tools like `mcp__chrome-devtools__lighthouse_audit`

**If not available**, stop and guide the user:

```
This skill needs Chrome DevTools MCP for Lighthouse auditing:

   Install the superpowers-chrome plugin:
   claude plugin add superpowers-chrome

Install it, then re-run /lighthouse-100.
```

**If available**, proceed.

---

## Step 1: Navigate & Audit

1. Navigate to the page: `mcp__chrome-devtools__new_page` or `navigate_page`
2. Run: `mcp__chrome-devtools__lighthouse_audit` (device: mobile, mode: navigation)
3. Parse the JSON report to find ALL failed audits

Parse failures:
```bash
cat report.json | python3 -c "
import json, sys
data = json.load(sys.stdin)
for key, audit in data['audits'].items():
    if audit.get('score') == 0:
        print(f'FAIL: {key}')
        if 'details' in audit and 'items' in audit['details']:
            for item in audit['details']['items'][:5]:
                if 'node' in item:
                    print(f'  Element: {item[\"node\"].get(\"snippet\", \"\")[:200]}')
"
```

## Step 2: Fix Common Failures

### Accessibility Fixes

| Audit ID | Root Cause | Fix |
|----------|-----------|-----|
| `color-contrast` | Text/bg contrast < 4.5:1 | Darken text color or lighten background. Use WCAG contrast checker. |
| `image-alt` | `<img>` without `alt` | Add descriptive alt text. Decorative images: `alt=""` |
| `label` | Form input without label | Add `<label for="id">` or `aria-label` |
| `link-name` | `<a>` without text | Add visible text or `aria-label` |
| `button-name` | `<button>` without text | Add visible text or `aria-label` |
| `heading-order` | Skipped heading level (h1 -> h3) | Fix hierarchy: h1 > h2 > h3 |
| `html-has-lang` | Missing `lang` attribute | Add `<html lang="en">` |
| `meta-viewport` | Missing viewport meta | Add `<meta name="viewport" content="width=device-width, initial-scale=1.0">` |
| `document-title` | Missing `<title>` | Add descriptive `<title>` |
| `aria-allowed-attr` | Wrong ARIA attribute | Check MDN for valid attributes per role |
| `label-content-name-mismatch` | aria-label doesn't match visible text | Update aria-label to include visible text |
| `target-size` | Touch target < 24x24px | Increase padding/min-height to 44px |
| `tabindex` | tabindex > 0 | Use tabindex="0" or "-1" only |

### Best Practices Fixes

| Audit ID | Root Cause | Fix |
|----------|-----------|-----|
| `is-on-https` | HTTP not HTTPS | Configure SSL |
| `no-vulnerable-libraries` | Old JS library | Update dependency |
| `csp-xss` | No CSP header | Add Content-Security-Policy header |
| `errors-in-console` | JS errors | Fix the errors |
| `image-aspect-ratio` | Stretched images | Set correct width/height or use `object-fit` |

### SEO Fixes

| Audit ID | Root Cause | Fix |
|----------|-----------|-----|
| `meta-description` | Missing meta description | Add `<meta name="description" content="...">` |
| `http-status-code` | Non-200 status | Fix server config |
| `link-text` | Generic link text ("click here") | Use descriptive link text |
| `crawlable-anchors` | `href="#"` or `javascript:` | Use real URLs |
| `hreflang` | Missing hreflang for multilingual | Add `<link rel="alternate" hreflang="...">` |
| `canonical` | Missing canonical | Add `<link rel="canonical" href="...">` |
| `robots-txt` | Missing robots.txt | Create robots.txt |
| `structured-data` | Invalid schema | Fix JSON-LD errors |

## Step 3: Contrast-Specific Workflow

When `color-contrast` fails, for each element:

1. Get the computed foreground and background colors
2. Calculate contrast ratio
3. If < 4.5:1 for normal text (or < 3:1 for large text):
   - Darken the foreground color until ratio >= 4.5:1
   - Use CSS variable if one exists, update the variable
   - If hardcoded, replace with darker value

**Common contrast fixes:**
- Orange accent on white bg: use darker shade (#8f3b16 instead of #eb6a2c)
- Gray text on light bg: darken to at least #595959 on white
- Light text on colored bg: ensure sufficient darkness

## Step 4: Build & Re-verify

After fixing:
1. Run project build command (check CLAUDE.md, package.json, or Makefile)
2. Deploy/push changes
3. Wait for deployment
4. Re-run Lighthouse audit
5. If any score < 100, repeat from Step 2

## Step 5: Desktop Audit

After mobile hits 100/100/100:
1. Run: `mcp__chrome-devtools__lighthouse_audit` with `device: desktop`
2. Fix any desktop-specific failures
3. Re-verify both mobile and desktop

## Output Summary

When done, report:
```
Lighthouse 100/100/100 achieved!

Fixed N issues:
- [list each fix with audit ID and what was changed]

Mobile:  A11y 100 | BP 100 | SEO 100
Desktop: A11y 100 | BP 100 | SEO 100
```

---

## Common Mistakes

- **Fixing contrast by changing background instead of text** — prefer darkening text, less visual disruption
- **Adding aria-label when visible text would work** — visible text is always better than aria-label
- **Ignoring the JSON report details** — the `items` array tells you exactly which elements fail
- **Not re-running after fixes** — one fix can break another score
- **Skipping desktop after mobile passes** — desktop can have different failures
