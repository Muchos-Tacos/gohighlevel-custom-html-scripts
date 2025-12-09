# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository contains custom HTML/CSS/JavaScript snippets for extending GoHighLevel (GHL) survey functionality. Scripts are embedded directly into GHL survey slides via their "Custom HTML" block feature.

## Repository Structure

```
<ProjectName>/<SurveyName>/<scriptName>.html
```

- **Project folders** (PascalCase): Client or project identifiers (e.g., `MyFavoriteTherapist`, `CharityRecyclingService`)
- **Survey folders** (PascalCase): Match GHL survey names (e.g., `HiringSurvey2`)
- **Script files** (camelCase): Self-contained HTML files with embedded `<style>` and `<script>` tags

## Architecture

Each `.html` file is a complete, self-contained snippet designed to be pasted into a GHL survey slide. Scripts typically follow this pattern:

1. **HTML structure** - UI elements rendered inside GHL's sandboxed iframe
2. **Scoped CSS** - Prefixed selectors to avoid conflicts with GHL's styles (e.g., `.availability-container .day-card`)
3. **JavaScript logic** - Event handlers, DOM manipulation, and GHL field integration

### GHL Integration Patterns

**Hidden field binding**: Scripts interact with GHL form fields using:
- `data-q` attribute selectors: `document.querySelector('input[data-q="field_name"]')`
- Field ID selectors: `document.querySelector('[id^="partial_id"]')` for dynamically-suffixed IDs
- Hidden `<input>` elements with `name="custom_values[fieldId]"` for form submission

**Event dispatching**: After programmatically updating GHL fields, dispatch events to trigger GHL's internal handlers:
```javascript
element.dispatchEvent(new Event('input', { bubbles: true }));
element.dispatchEvent(new Event('change', { bubbles: true }));
```

## Development Guidelines

- Scripts must be **idempotent** - GHL may re-render slides, so avoid duplicate event bindings
- Use **scoped CSS** with unique container classes to prevent style conflicts
- Avoid **global variables** unless necessary; use IIFEs or module patterns
- GHL field IDs are often UUIDs - store mappings as constants at script top (see `fieldIdsStart`, `fieldIdsEnd` patterns in availability.html)
