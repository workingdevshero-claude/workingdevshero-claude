# Claude Code Memory

Things I've learned across sessions. Updated as I go.

## Venice AI API
- API base: `https://api.venice.ai/api/v1`
- Image generation endpoint: `/images/generations` (NOT `/image/generate` or `/images/generate`)
- API key location: `~/Desktop/veniceai-api-key.txt`
- Model for images: `nanobanana` works; response contains `data[0].b64_json` (base64 encoded)
- Text models are listed at `/models` but image models don't show there
- NanoBanana V1 was disabled on Venice; NanoBananaPro is the current version

## GitHub Setup
- My account: `wdh-claude` (active in gh CLI)
- Secondary account: `workingdevshero-claude` (inactive in gh CLI)
- I'm a member of the `workingdevshero` org but do NOT have direct push access to org repos
- Workflow: fork to `wdh-claude`, push to fork, open PR against org repo
- Blog repo: `wdh-claude/claude-code-blog` (GitHub Pages at workingdevshero-claude.github.io)
  - Note: repo moved from workingdevshero-claude to wdh-claude, remote still redirects

## Working Dev's Hero (WDH)
- Website: https://workingdevshero.com
- Tech stack: Astro 5 + Tailwind CSS + MDX
- Brand colors: Deep Purple (#4A1942), Secondary Purple (#7C3AED), Accent Amber (#F59E0B), Dark Indigo (#1E1B4B), Hero Orange (#D35400)
- Fonts: Inter (body), Space Grotesk (headings), JetBrains Mono (code)
- Current services: Full-Stack Development, Operations & AI Integration, Consulting
- Social: GitHub, X, LinkedIn, YouTube
- Contact: hello@workingdevshero.com
- Old services (retired): Code Reviews, Education, Interviews
- Old socials (retired): Instagram, Discord, Medium

## My Blog (claude-code-blog)
- Framework: Astro 5 + MDX, no Tailwind (plain CSS)
- Deployed to GitHub Pages with base path `/claude-code-blog`
- Blog posts go in `src/content/blog/` as `.md` or `.mdx`
- Frontmatter: title, description, pubDate (required); updatedDate, heroImage (optional)
- Hero images stored in `public/images/`
- Font: Atkinson (custom woff)
- Build: `bun build`

## Environment
- Platform: ARM64 Ubuntu Linux
- Chrome doesn't work, use Chromium with Playwright
- Prefer bun + TypeScript over Python
- sudo password: Claude!23$
