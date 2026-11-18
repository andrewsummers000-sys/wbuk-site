# WBUK site: security and editing guide

## What's in the folder
- index.html – home page (black theme)
- procurement-services/index.html – procurement services page
- book-a-consultation/index.html – enquiry form
- _headers – security headers for Netlify / Cloudflare Pages
- .htaccess – same headers for Apache / cPanel hosting
- .well-known/security.txt – security contact (change the email to a real mailbox)

## Security checklist
1. Host on HTTPS only (free via Cloudflare, Netlify or your host's Let's Encrypt). The headers force this.
2. Upload ONE of `_headers` or `.htaccess` (whichever your host uses). They set HSTS, CSP, clickjacking protection, referrer and permissions policies.
3. Form: the form must post to a form service (Formspree, Web3Forms or Basin) or your own server. Add its web address to `connect-src` and `form-action` in the header file if it isn't already listed. Turn on the service's spam protection / reCAPTCHA.
4. Never put passwords or private API keys in the pages. Form-service public keys are fine.
5. Turn on two-factor sign-in for your hosting, domain registrar and form-service accounts.
6. If you ever add WordPress or a CMS, keep it updated and use a security plugin.
7. After going live, test at securityheaders.com and ssllabs.com.
8. Links on the pages currently point at the claude.ai preview addresses. Replace them with /, /procurement-services/ and /book-a-consultation/ once hosted.
9. Fonts load from Google Fonts. To remove that third party, download Newsreader and Inter and host them yourself.

## Editing
Open any index.html in a text editor, change the wording between the tags, save and re-upload. Do not edit the `<script>` or `<form>` parts unless you know what they do.

## SEO and AI search
- `robots.txt` welcomes search engines and AI answer engines (Google, Bing, ChatGPT, Claude, Perplexity). `llms.txt` is a plain summary for AI tools. Keep both in the site root.
- After going live: add the site to Google Search Console and Bing Webmaster Tools, submit sitemap.xml, and claim your Google Business Profile (Oakham, service area UK-wide).
- Keep the FAQ answers on the home and procurement pages up to date; they feed both Google and AI answers.
- Add a social/preview image (1200x630) and set og:image once hosted; list your LinkedIn page in the schema `sameAs` field.

## Enquiry form (Formspree)
The form posts to https://formspree.io/f/mqpqqozv. Enquiries arrive at the email on your Formspree account. In Formspree, add wbuk.net to the form's allowed domains, turn on spam filtering/reCAPTCHA, and send a test enquiry after going live. The endpoint is already allowed in the security headers.

## Photos, licences and sharing preview
- Photos live in `assets/img/` with descriptive file names; the alt text is in each page's HTML. Keep descriptive names when you replace a photo.
- The aged care, private hospital and catering photos are from Pexels (free commercial licence, credit optional; credits are in the page data). The other photos have no recorded source: add the credit or licence details in the page data once you confirm where they came from.
- `assets/img/wbuk-uk-hospitality-consultancy-og.jpg` (1200x630) is the picture shown when a page is shared on LinkedIn, Facebook, WhatsApp and similar.
- `sitemap.xml` lists the photos so Google Images can find them. Resubmit it in Search Console after any photo change.
