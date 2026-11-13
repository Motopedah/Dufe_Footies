# Dufe_Footies storefront

The portable website is in `dist/`. It is plain HTML, CSS, JavaScript, and local images. Netlify can host it without a build step.

## Preview on your computer

From this project folder, run:

```powershell
node -e 'const h=require("http"),f=require("fs"),p=require("path"),r=p.resolve("dist");h.createServer((q,s)=>{const u=decodeURIComponent(q.url.split("?")[0]),x=p.join(r,u==="/"?"index.html":u);f.readFile(x,(e,d)=>{if(e){s.statusCode=404;s.end("not found");return}s.setHeader("Content-Type",x.endsWith(".css")?"text/css":x.endsWith(".js")?"text/javascript":x.endsWith(".png")?"image/png":x.endsWith(".jpg")?"image/jpeg":"text/html");s.end(d)})}).listen(4173,"127.0.0.1")'
```

Open http://127.0.0.1:4173/.

## Publish or update on Netlify

For a simple manual publish, sign in to Netlify, create a site using its manual deploy / drag-and-drop option, and upload the **`dist` folder**. To publish an update, upload the changed `dist` folder again. Keep this project folder as your master copy.

For easier ongoing updates, put this project in a GitHub repository and connect that repository to Netlify. Set the publish directory to `dist` and leave the build command empty. After that, publishing a saved change to the connected repository triggers a new deploy. Do not share Netlify or GitHub passwords in chat.

You can also continue the same design with another LLM: give it this project folder (or a ZIP of it), especially `dist/index.html`, `dist/styles.css`, `dist/app.js`, `dist/assets/`, and this README. Ask it to preserve the existing brand decisions and edit the files in place. The site is not tied to ChatGPT, Netlify, or a particular framework; the files can be moved to another static host or rebuilt as a WordPress theme later.

## Where to edit

- Products and testimonials load from `dist/content/catalog.json` and `dist/content/testimonials.json`. For the visual editor setup, see `CMS_SETUP.md`; it requires the Netlify site to be connected to GitHub.
- Page content and links are in `dist/index.html` and `dist/returns.html`.
- Visual styling is in `dist/styles.css`.
- Optimized product and testimonial photos are in `dist/assets/optimized/`. Original photo backups are in the separate `image-source-backups/` folder and are not included in the Netlify upload. The logo, sizing video (`size-guide.mp4`), and optimized Pelumi hero are also in `dist/assets/`.

## Current order flow and limits

- The product catalogue, colour/size choices and cart run in the visitor’s browser; the cart is saved in that browser.
- On the order page, Nigerian customers see the OPay details and can open a WhatsApp message containing their selected items. The message asks them to send screenshots of the order and transfer receipt for confirmation. Delivery is quoted by location.
- Women’s EU sizes 44–50 and men’s EU sizes 45–50 show “DM for price”; the customer should confirm that price on WhatsApp before transferring. Kids sizing is custom and confirmed on WhatsApp.
- Men’s products with a ₦15,000 regular price show a ₦13,500 sale price. Women’s slides with a ₦9,000 regular price show an ₦8,000 sale price. Other price groups remain at their regular price until their sale prices are supplied.
- International customers use WhatsApp to confirm shipping and payment.
- This static version does not store orders on a server, send automatic email receipts, create customer accounts, or process card payments. Testimonials are managed in `dist/content/testimonials.json`; only approved items appear publicly. The visual editor requires GitHub-backed Netlify deploys as explained in `CMS_SETUP.md`.
- Photos supplied so far are sample catalogue images. Their optimized copies load from `dist/assets/optimized/`; originals remain as backups. Background replacement still needs a suitable image-editing tool.

## Holiday order schedule

- First batch: orders November 16–30, 2026; production ready before Christmas.
- Second batch: orders December 1–13, 2026; production ready in the last week of December or first week of January 2027.

The deployable site is in `dist/`; no package install or build process is required.
