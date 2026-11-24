HIZWAY INVESTMENTS LIMITED - Cloudflare deployment (Wrangler)
=============================================================

What is in this folder
- public/          the app (this is what gets uploaded)
- wrangler.jsonc   Cloudflare settings: the name and the folder to upload
- package.json     installs Wrangler, Cloudflare's upload tool
- public/_headers  security settings Cloudflare adds to every file

What you need
1. A free Cloudflare account: https://dash.cloudflare.com/sign-up
2. Node.js (the LTS version): https://nodejs.org   (this also installs npm)

Deploy (about 5 minutes)
1. Unzip this folder. Open a terminal inside it.
   Windows: open the folder, click the address bar, type cmd, press Enter.
   Mac: right-click the folder, choose "New Terminal at Folder".
2. Run:   npm install
3. Run:   npx wrangler login
   A browser window opens. Log in to Cloudflare and click Allow.
4. Run:   npx wrangler deploy
   The first time, Cloudflare may ask you to choose a "workers.dev" subdomain.
   Choose a name you will keep, because it becomes part of the address.
5. Wrangler prints the address of your app:
   https://hizway-investments.<your-subdomain>.workers.dev
   On the Android phone, open it in Chrome, tap the menu (three dots), then
   "Install app". Open the app once while online so it saves itself, then it
   works without internet.

Try it on this computer first (optional)
   npm run dev
   Then open the http://localhost address it shows.

Keep the address the same
- Receipts, numbering and the security code are saved in each browser for one
  exact address. A different address opens empty with a new security code.
- Do not change "name" in wrangler.jsonc after the first deploy. Choose it
  now. If you want a different name, change it BEFORE step 4.
- Your own domain is optional. If you add one later, add it in the Cloudflare
  dashboard under this Worker's settings and use it from the very start, so the
  address never changes.

Updating the app later
1. Replace the files in public/ with the new version.
2. In public/sw.js change the version on the CACHE line
   (hizway-receipts-v7 becomes hizway-receipts-v8).
3. Run:   npx wrangler deploy
4. Open the app once online on each phone and computer to get the update.

Security code and receipts
- The app makes a security code the first time it opens (Business details).
  It locks the QR code on every receipt. Write it down and use the same code on
  every device.
- Receipts are saved only on the device that issued them. Cloudflare only
  delivers the app files and never receives receipt details.

Copyright
- Copyright (c) 2026 Hizway Investments Limited. All rights reserved.
  See public/LICENSE.txt.
- Open-source parts (QR code, scanner, fonts) keep their own licences:
  public/THIRD-PARTY-NOTICES.txt. Keep that file with the app.
