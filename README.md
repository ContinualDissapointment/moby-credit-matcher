# MobyGames Credit Matcher

Compare the credits of two games and find the people who worked on both.

**Live: https://continualdissapointment.github.io/moby-credit-matcher/**

## How it works

MobyGames is behind Cloudflare, so a static page can't fetch credits for you —
public CORS proxies get challenged or blocked, and the [official API doesn't
expose credits](https://www.mobygames.com/info/api/), only companies.

So your own browser does the scraping:

1. Drag the **Grab Moby Credits** button to your bookmarks bar.
2. Open a MobyGames `/credits/` page and click the bookmark. The credits are
   copied to your clipboard as JSON.
3. Paste into the comparator, once per game, and hit Compare.

If your browser's CSP blocks the bookmarklet, you can paste the raw HTML of a
credits page instead — the app detects which one you gave it.

## Notes

- One role row can list dozens of people (`Artists: A, B, C, …`), so every
  `/person/` link in the row is captured, not just the first.
- Matching is keyed on the MobyGames **person ID**, not the display name.
- The summary counts **unique people**, so someone credited under three roles
  counts once.
- Overlap percentage is reported in both directions, since it's asymmetric:
  20 shared people is most of a small indie team but a rounding error on a
  300-person production.
