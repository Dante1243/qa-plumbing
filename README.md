# QA Plumbing, Gas & Drainage: website redesign mockup

> **Pitch points below were written when the site was built and most haven't been rechecked.** Confirmed 25 Nov 2026: WordPress 4.7.29, and the footer's "Emergency Plumbing" link is a 404. The dummy images are in the code, but visitors may not see them. Check each one on the live site, on a real phone, before saying it.

A modern rebuild of http://qaplumbing.com.au for QA Plumbing Pty Ltd, 8 Rafferty Rd, Mandurah WA, (08) 9582 8822.
It uses plain HTML, CSS and JS, with no framework or build step. All text, services, staff, licence numbers and photos come from their current site.

## Pages

| File | Page | Old site equivalent |
|---|---|---|
| `index.html` | Home: hero, stats, 6 service cards, why choose us, emergency band, recent work, partners | `/` |
| `about.html` | About, safety commitment, team numbers, Meet the Team | `/about-us/` |
| `residential.html` | Residential plumbing, full list of 27 services, hot water section | `/residential-plumbing/` |
| `commercial.html` | Commercial and industrial plumbing, 12 services | `/commercial-plumbing/` |
| `hot-water.html` | Hot water repairs and installs, 3 featured units | `/hot-water-units/` |
| `solar.html` | Solahart L Series and LCSD Series, install photos | `/solar-hot-water-units/` |
| `gallery.html` | "Our Work": 21 job photos with filters and a lightbox | `/gallery/` |
| `contact.html` | Contact details, map, Request a Quote/Job form | `/contact-us/` + `/request-quote/` |

Shared files: `css/style.css` and `js/main.js`.

## Pitch points: what's wrong with the old site and what we fixed

- **Placeholder "dummy" images.** The home page slider loads `wp-content/plugins/revslider/admin/assets/images/dummy.png` as the `src` of all 3 slides, and the real photos only swap in via JavaScript. On a slow phone, or with JS blocked, visitors see blank placeholder slides. The new site has no placeholders, and every image is real.
- **Old slider plugin.** The site runs Slider Revolution 5.3 (2017) on WordPress 4.7.29 (released 2016, long out of support) with Visual Composer. That's slow, a security risk, and the slides rotate away before people can read them. We replaced it with one clean, static hero that puts the phone number and a quote button up front.
- **Empty links.** The home page has an image gallery whose 3 links have an empty `href=""` and no images. There's also a stray "." under the footer About text.
- **Broken footer link.** "Emergency Plumbing" in the footer menu goes to `/emergency-plumbing/`, which returns a **404**. The new site has a proper emergency section on the home page, linked from the footer.
- **Phone number hard to tap.** The new site has a tap-to-call button in the header plus a sticky Call / Get a quote bar at the bottom on phones.
- **Licence numbers hidden in tiny footer text.** PL 920 and GF 10607 now show in the hero, top bar and footer, because they build trust.
- **Dated look.** The site uses a generic "PlumberX" theme and doesn't match their own navy and light-blue logo. The new design uses the logo's navy (#004092) and light blue (#8DB9DE), keeps the old theme's orange (#F56600) for call-to-action buttons, and adds dark mode.
- **Contact forms were repeated on every service page.** There's now one clear quote form on the Contact page, using the same fields as their current form.
- **Content buried in shortcodes.** Their service lists (27 residential, 12 commercial) were plugin list widgets. They're now clean, scannable grids.

## Polish features

- Dark mode follows the system setting. A sun/moon toggle in the header remembers the choice in `localStorage` (wrapped in try/catch), and an inline script in `<head>` sets the theme before first paint so there's no flash. Every colour is a CSS variable.
- Sections and cards fade and slide up in a stagger as you scroll (IntersectionObserver). Content already on screen at load isn't hidden.
- Smooth hover states on buttons, cards, nav and lists. Images zoom slightly on hover.
- The mobile menu opens and closes smoothly, the hamburger animates to an X, and Esc closes it. On desktop, Services is a dropdown that also works with the keyboard.
- The sticky header gains a shadow and blur once you scroll. The blur sits on `::before` so it doesn't trap the fixed mobile menu.
- Smooth scrolling for in-page links, a back-to-top button, lazy-loaded images, a skip link and visible focus outlines.
- The gallery has category filters and a keyboard-friendly lightbox (arrow keys, Esc, focus trap).
- Motion stays at 150–400ms with ease-out, and it's all switched off under `prefers-reduced-motion`.
- Mobile: tested at 375px with no horizontal scroll, readable text and 44px+ tap targets.

## To confirm with the owner

- **"17+ years servicing Mandurah"**: taken from the Residential page ("over 17 years of experience"). That text may be old, so the real figure could be higher now.
- **Team**: are Phil Brown, Ian Smith, Rob Morgan and Glenn Brown still the current team? Are the head-count figures still right (4 licensed plumbers and gas fitters, 3 apprentices, 1 mature age apprentice)?
- **Hours**: Mon–Fri 8am–5pm, plus an emergency plumber 7 days (both from the old site). Do they want after-hours emergency call-out wording?
- **Featured hot water units** (Prodigy 135Z, Proflo, Dux 26L): are these still the models they push? The old Hot Water page also had a "DOWNLOAD" guide on choosing a system, but the link didn't point anywhere useful.
- **Partners**: Solahart, Dux, Energy House Mandurah, David's Tiling Services and Dimes Electrical were all on the old home page. Are they still current?
- **Quote form**: on this demo it opens the visitor's email app addressed to admin@qaplumbing.com.au. A live site would use a form service.
- **Blog**: the old site has a blog (2024 posts). It isn't rebuilt in this mockup. We could link to it or migrate it later.
- **Afterpay & ZipPay**: are they still offered?

## Image sources

Every image was downloaded from their own domain, `https://www.qaplumbing.com.au/wp-content/uploads/...`. Large phone photos were resized to a 1400px maximum and re-compressed (JPEG q80). Big PNG photos were converted to JPEG.

| Image(s) | Original path | Used on |
|---|---|---|
| `logo.jpg` | `/2017/02/logo.jpg` | Header, footer |
| `qa-plumbing-fav-icon.jpg` | `/2020/09/QA-Plumbing-Fav-Icon.jpg` | Favicon |
| `image2.jpg`, `image8.jpg`, `page01_background01.jpg` | `/revslider/home-slider-4/image2.jpg`, `/2016/04/image8.jpg`, `/2017/02/page01_background01.jpg` (the real slider photos) | Home, Contact and Residential heroes |
| `img_1631.jpg` | `/2016/01/img_1631.png` (team photo) | Home, About |
| `img_5114-1.jpg`, `img_5110-…jpg`, `img_5104-…jpg`, `img_5102.jpg` | `/2016/01/…` (staff photos) | About: Meet the Team |
| `residential-1.jpg` … `residential-21.jpg` | `/2017/03/Residential-1.jpg` … `-21.jpg` (their Gallery page) | Gallery, plus across pages |
| `burst-pipe.jpg`, `water-783355_640.jpg` | `/2017/02/burst-pipe.png`, `/2017/02/water-783355_640.jpg` | Home, Residential |
| `various_roof__piping.jpg`, `commerical-kitchen.jpg`, `fire_pipe.jpg` | `/2017/02/…` (Commercial page grid) | Commercial, Home |
| `135z.png`, `electrichotwater.png`, `dux-continous.png` | `/2017/02/…` (Hot Water page products) | Hot water |
| `302l-front.jpg`, `302lcs-front.jpg` | `/2017/02/…` (Solar page) | Solar |
| `solahart_energyfree_logo-1.png`, `dux.jpg`, `energyhousemandurah.png`, `davidstilingservices-1.png`, `dimes-1.jpg` | `/2017/03/…`, `/2023/11/…` (partner logos on home page) | Home: Partners |

**Not used:** `revslider/admin/assets/images/dummy.png`, the placeholder image left on the old home page slider (see pitch points). Some photos on the old site (e.g. `burst-pipe`, `water-783355_640`) look like stock images they uploaded rather than their own job photos. Where possible the mockup uses their real job photos instead.
