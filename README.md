<div align="center">
CHRISTO

Crafted for the unforgettable.

A cinematic single-page site for a womenswear house — handwoven sarees, lehengas, tailoring, and objects.

Show Image Show Image Show Image Show Image

View live · Editing · Deploying

</div>
Overview

The entire site is one file. No build step, no npm install, no framework — open index.html in a browser and it runs.

CHRISTO/
├── index.html    the complete site: markup, styles, animation
└── README.md
	
Scroll engine	GSAP 3.12.5 + ScrollTrigger (CDN)
Smooth scroll	Lenis 1.1.14, falling back to native scroll if the CDN is unreachable
Typography	Bodoni Moda (display) · Inter (UI)
Imagery	Unsplash CDN, with hand-drawn SVG figures as fallbacks
Dependencies	None installed
The scroll

Seven scenes, each handing off to the next without a visible seam.

#	Scene	What happens
1	Loader	CHRISTO staggers up over a progress line, then the curtain lifts
2	Hero	Pinned for 280vh — the wordmark recedes in Z, a sculptural object rotates 66° as the camera pushes in, then clears right while a second frame enters from the left
3	The Art of Detail	Oversized type drifts horizontally against two images parallaxing at different speeds
4	Made to Be Seen	A small frame scales from 26% to fullscreen, headline revealing in masked lines
5	Collection	Seven pieces; on hover a campaign frame tracks the cursor
6	Horizontal	Vertical scroll drives lateral travel across four frames, type moving the opposite way
7	Footer	The closing frame, with contact details

Background morphing. One ScrollTrigger samples a six-stop colour ramp — cream, ivory, sand, brown, chocolate, espresso — and interpolates it every frame. A second ramp drives --ink, so all text and the navigation flip from dark to cream around the halfway point. Nothing changes at section boundaries.

Also throughout: a custom cursor that expands to VIEW over collection rows, magnetic buttons, film grain, a scroll progress bar, and full prefers-reduced-motion support.

Editing

Everything lives in index.html. Three places cover almost every change.

Photography

Near the top of the <script> tag:

js
var SHOTS = {
  hero:    "images/hero.jpg",   // frame entering from the left in the hero
  detailA: "",                  // large image in The Art of Detail
  detailB: "",                  // smaller parallax image beside it
  reveal:  "",                  // the fullscreen frame
  "01": "",   // Veil & Drape
  "02": "",   // Mehfil
  "03": "",   // Courtyard
  "04": "",   // Essential Form
  "05": "",   // Noir
  "06": "",   // The Carry
  "07": "",   // Heirloom
  h1: "", h2: "", h3: "", h4: ""   // horizontal campaign frames
};

Local paths or full URLs both work. Shoot vertical, roughly 3:4.

If a slot is empty or an image fails to load, the drawn SVG figure shows instead — the layout never breaks and you never get a blank box.

Photographs are graded warm so they sit inside the palette. Remove this line for full saturation:

css
.plate .shot { filter: saturate(.72) sepia(.16) contrast(1.06) brightness(.97); }
Colour

Brand tokens live in :root:

css
--cream:#F5EBDD;   --ivory:#FFF9F0;   --sand:#C49A7A;   --caramel:#A87958;
--brown:#6F4937;   --choc:#3A2118;    --espresso:#1D100B;

The scroll journey is separate — the BG and INK arrays in the script. Each entry pairs a scroll position (p, 0 to 1) with a colour. Change those to retime it.

Products

Collection items are plain <a class="item"> blocks. Copy one, change the number, name, and data-slot, and it inherits every animation automatically. Contact details sit in the <footer>.

Deploying

Static, so any host works.

Vercel — push to GitHub, then vercel.com → Add New → Project → import the repo. Leave all build settings blank and deploy. Later edits to index.html redeploy automatically within a minute.

Netlify Drop — drag index.html onto netlify.com/drop for an instant URL, no account needed.

GitHub Pages — Settings → Pages → deploy from main, root folder.

Browser support

Modern Chrome, Safari, Firefox, and Edge. Tested at 1440px, 1024px, 768px, and 390px.

Mobile is recomposed rather than shrunk: the custom cursor and magnetic buttons switch off, collection frames drop inline since there's no hover, and the heavier 3D is reduced. prefers-reduced-motion skips the loader and scrubbed animation entirely.

Notes on the imagery

Photography is currently hotlinked from the Unsplash CDN under the Unsplash License — free for commercial use, no attribution required, though the footer credits contributors anyway.

The licence covers the photographer's copyright but does not guarantee a model release, so using a recognisable face to sell a garment is worth checking per photo before this trades commercially. Replacing them is one line per slot in SHOTS.

<div align="center">

CHRISTO · Hitech City, Mancherial, Telangana 504208, India

By appointment

© 2026 CHRISTO

</div>
