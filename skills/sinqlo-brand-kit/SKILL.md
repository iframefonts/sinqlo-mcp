---
name: sinqlo-brand-kit
description: Fetch live client brand kits (logos, variations, exact colors, fonts, design tokens, and brand rules) from Sinqlo MCP before designing or coding on-brand UI, decks, or social graphics.
---

# Sinqlo Brand Kit

Use this skill whenever the user asks to design, code, or generate branded deliverables (web pages, components, slide decks, email templates, or social graphics) for a client whose brand kit is stored in Sinqlo.

## When to Use This Skill

- Building a landing page, app UI, or prototype for a client brand
- Setting up CSS custom properties, Tailwind v4 themes, or W3C design tokens
- Picking the right logo variation (white, black, symbol-only, horizontal) for light or dark backgrounds
- Generating on-brand social assets (Instagram, TikTok, YouTube, Open Graph)
- Sharing a client's permanent Brand Link instead of attaching loose logo files

## Workflow

1. **Locate the brand first**
   - Call `search_brands` with the client or brand name if you do not have a brand ID yet.
2. **Pull the full brand kit before writing code or copy**
   - Call `get_brand_kit` to retrieve logos, colors, typography, gradients, patterns, and brand rules in one step.
   - Never guess or approximate hex codes, font names, or logo URLs.
3. **Export tokens in the project's format**
   - When writing frontend code, call `get_brand_tokens` to get ready-to-use CSS custom properties, a Tailwind v4 theme, or W3C JSON tokens.
4. **Match logo variations to the background**
   - Call `list_logo_variations` to inspect available lockups (e.g., white on dark surfaces, primary on light surfaces, symbol-only for small avatars/favicons).
   - Call `get_logo_image` when you need the SVG or PNG asset (note: download URLs expire after 1 hour, so save files into the project when committing code).
5. **Share permanent links for handoffs**
   - When a teammate or client asks for logo files, call `get_smart_link` and share the permanent Brand Link rather than a temporary download URL.

## Safety & Guardrails

- All Sinqlo MCP tools are read-only; no write or destructive actions are possible.
- Always respect the brand rules returned by `get_brand_kit` (clear space, color contrast, approved color roles, and typography pairings).
- If a requested variation or color role does not exist in the kit, state that clearly instead of inventing one.

## Examples

### Build an on-brand hero section
> "Fetch Acme's brand kit from Sinqlo, pull their Tailwind v4 tokens, and build a responsive hero section using their white logo on the primary dark background."

### Audit brand colors & fonts for a developer
> "Look up Northwind in Sinqlo and list its exact Hex, RGB, and CMYK color values plus its font stack and Brand Link."

### Generate a social graphic
> "Use Sinqlo to render an Open Graph banner for Acme announcing our Q4 release."
