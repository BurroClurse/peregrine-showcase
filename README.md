# Peregrine: Dry Fire Trainer

An iPhone and iPad app that uses the camera to detect laser training shots on printed targets and score them live. Released on the App Store in September 2026.

[App Store](https://apps.apple.com/us/app/peregrine-dry-fire-trainer/id6773954254) | [peregrinedryfire.com](https://peregrinedryfire.com)

The source code is private. This repo shows what the project is and how it was built. I'm happy to walk through the code on request.

<p>
  <img src="images/press-live.webp" width="260" alt="Live scoring screen">
  <img src="images/press-drift.webp" width="260" alt="Drift Diagnosis screen">
  <img src="images/press-history.webp" width="260" alt="Session history screen">
</p>

## What it does

- Detects a red laser hit on a paper target at 60 frames per second and scores it live: points, points per minute, par and split times.
- Calibrates each target from printed QR codes and corner markers, so it knows the target's size, distance and scoring zones.
- Drift Diagnosis maps where the muzzle moved at each shot to 12 clock positions and prompts a correction when the same fault repeats.
- 25 built-in drills, custom drills, a par timer and session history for tracking trends.

## How I built it

I'm the sole developer. I designed the app and directed AI-assisted development with Claude Code, often with several agents working in parallel.

- Tuned the shot detector with hand-labeled shot data analyzed in SPSS. Red dominance and local contrast beat raw brightness.
- About 2,700 automated tests, TestFlight betas and on-device validation before each release.
- Published the privacy policy and terms, and ran the App Store release.

## The rest of the project (also private)

### Website

[peregrinedryfire.com](https://peregrinedryfire.com) is the app's public home. It has the walkthrough video, how it works, the gear you need, pricing, support, a press kit, the privacy policy and terms, and landing pages written for search.

- Plain HTML, CSS and JavaScript, hosted on Netlify.
- A publish script builds a clean public copy from the editing copy, so only the pages and images the site uses go live.
- An in-page editor lets me change text, fonts and layout without opening the code.
- Browser tests check the layout at phone and desktop sizes and guard the editor against regressions.

### Peregrine HQ

A private dashboard with every number for the business in one place: downloads, sales, search traffic, site visits, ads and social.

- Once a day GitHub Actions pulls the data from each source's API, with Appfigures read through its official MCP server, and writes one snapshot.
- A Claude routine republishes the dashboard from that snapshot, and I can ask Claude questions about any of it.
- Every Monday it rereads the API docs and changelogs the project depends on. If something changed, it opens a GitHub issue.

### Reddit Radar

Finds Reddit threads about dry fire training that are worth a reply.

- Twice a day GitHub Actions searches the watched subreddits in parallel jobs, filters on keyword matches, drops threads it has already seen and opens a GitHub issue with the rest.
- It keeps each subreddit's posting rules on file and refreshes them monthly, so I can check a sub's rules before replying.
- It never posts and holds no posting credential. I read every thread and reply by hand.
