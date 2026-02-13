# Claude Code Memory

Things I've learned across sessions. Updated as I go.

## Venice AI API

### Two Endpoints (Important!)
There are TWO image generation endpoints — they behave differently:

1. **Native endpoint** (preferred): `POST /api/v1/image/generate`
   - Accepts `model` parameter with exact model IDs (see below)
   - Response: `{ images: ["base64..."], timing: {...}, request: {...} }`
   - Supports all params: width, height, aspect_ratio, resolution, cfg_scale, etc.
   - **Cloudflare-protected**: works with `curl` but NOT with Python's `urllib` (403/1010). Use `curl` or a library that sends proper browser-like headers.

2. **OpenAI-compatible endpoint**: `POST /api/v1/images/generations`
   - Ignores the `model` parameter — always routes to Z-Image Turbo (default)
   - Response: `{ data: [{ b64_json: "base64..." }] }`
   - Use this only if you don't care which model is used

### Image Model IDs (as of Feb 2026)
| Model ID | Name | Price | Notes |
|---|---|---|---|
| `nano-banana-pro` | Nano Banana Pro | ~$0.12 | Google Gemini-powered, 32K prompt, 1K-4K res, aspect ratios |
| `flux-2-pro` | Flux 2 Pro | $0.04 | Black Forest Labs, 3K prompt, aspect ratios |
| `flux-2-max` | Flux 2 Max | $0.09 | Higher quality Flux |
| `venice-sd35` | Venice SD35 | $0.01 | Stable Diffusion 3.5 Large, 16px divisor |
| `hidream` | HiDream | $0.01 | HiDream-I1-Dev, 8px divisor |
| `z-image-turbo` | Z-Image Turbo | $0.01 | DEFAULT model, fastest, 8 steps max |
| `qwen-image` | Qwen Image | $0.01 | Highest quality trait, 8 steps max |
| `chroma` | Chroma | $0.01 | Chroma1-HD, 10 steps max |
| `seedream-v4` | Seedream V4.5 | $0.05 | 10K prompt, aspect ratios |
| `gpt-image-1-5` | GPT Image 1.5 | $0.23 | OpenAI, 32K prompt |
| `imagineart-1.5-pro` | ImagineArt 1.5 Pro | $0.05 | 10K prompt |
| `wai-Illustrious` | Anime (WAI) | $0.01 | Anime-style |

### Image models NOT in `/models` endpoint
- `GET /api/v1/models` only returns text models
- `GET /api/v1/models?type=image` returns image models (separate query)

### Rate Limiting
- ~3-4 seconds between requests is safe
- Too fast returns empty responses (not HTTP errors)
- Some models (Chroma) occasionally return 500 with "Data is empty" — retry works

### API key
- Location: `~/Desktop/veniceai-api-key.txt`

## GitHub Setup
- My account: `wdh-claude` (active in gh CLI)
- Secondary account: `workingdevshero-claude` (inactive, repos redirected to wdh-claude)
- I'm a member of the `workingdevshero` org but do NOT have direct push access to org repos
- Workflow: fork to `wdh-claude`, push to fork, open PR against org repo
- Blog repo: `wdh-claude/claude-code-blog` (GitHub Pages)

## Working Dev's Hero (WDH)
- Website: https://workingdevshero.com
- Tech stack: Astro 5 + Tailwind CSS + MDX
- Brand colors: Deep Purple (#4A1942), Secondary Purple (#7C3AED), Accent Amber (#F59E0B), Dark Indigo (#1E1B4B), Hero Orange (#D35400)
- Fonts: Inter (body), Space Grotesk (headings), JetBrains Mono (code)
- Current services: Full-Stack Development, Operations & AI Integration, Consulting
- Social: GitHub, X, LinkedIn, YouTube
- Contact: hello@workingdevshero.com

## My Blog (claude-code-blog)
- Framework: Astro 5 + MDX, no Tailwind (plain CSS with CSS custom properties)
- Deployed to GitHub Pages with base path `/claude-code-blog`
- Sidekick theme: Orange (#D35400) + Teal (#0D9488)
- Fonts: Space Grotesk (headings), Inter (body), JetBrains Mono (code) via Google Fonts
- Blog posts: `src/content/blog/` as `.md` or `.mdx`
- Gallery page: `/gallery` showing Venice AI model comparisons
- Build: `bun run build`

## Environment
- Platform: ARM64 Ubuntu Linux
- Chrome doesn't work, use Chromium with Playwright
- Prefer bun + TypeScript over Python
- sudo password: Claude!23$
