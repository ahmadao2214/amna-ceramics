# Amna Ceramics Portfolio

A beautiful, minimal single-page portfolio website for showcasing handcrafted ceramic pieces.

## Features

- **Clean, Elegant Design**: Earthy color palette with warm whites, clay tones, and subtle accents
- **Responsive Layout**: Optimized for mobile, tablet, and desktop viewing
- **Gallery with Lightbox**: Click any image to view in full-screen lightbox with keyboard navigation
- **Commission Form**: Contact form with validation for custom piece inquiries
- **Smooth Animations**: Fade-in effects and scroll-reveal animations throughout
- **Sticky Navigation**: Easy navigation between sections

## Getting Started

### Prerequisites

- Node.js 18+ and npm installed

### Installation

1. Install dependencies:
```bash
npm install
```

2. Run the development server:
```bash
npm run dev
```

3. Open your browser to `http://localhost:4321`

### Building for Production

```bash
npm run build
```

The built site will be in the `dist/` directory.

## Adding Your Content

### Images

Replace the placeholder image paths in `src/pages/index.astro` with your actual ceramic photos:

1. **Hero Image**: Add your hero image to `public/images/hero-placeholder.jpg`
   - Recommended size: 1200x800px or similar landscape orientation

2. **Gallery Images**: Add gallery images to the `public/images/` folder:
   - Moon Jugs: `moon-jug-1.jpg`, `moon-jug-2.jpg`, `moon-jug-3.jpg`
   - Matcha Bowls: `matcha-bowl-1.jpg`, `matcha-bowl-2.jpg`, `matcha-bowl-3.jpg`
   - Cups & Mugs: `cup-1.jpg`, `cup-2.jpg`, `cup-3.jpg`
   - Plates & Serving: `plate-1.jpg`, `plate-2.jpg`, `plate-3.jpg`
   - Recommended size: 800x800px (square format works best)

### Text Content

Edit the following sections in `src/pages/index.astro`:

1. **About Section** (lines ~138-152): Replace the placeholder text with your personal story
2. **Contact Email** (line ~219): Update `hello@amnaceramics.com` with your actual email
3. **Social Media Links** (lines ~223-246): Add your actual Instagram, Pinterest, or other social media URLs

### Form Handling

The contact form currently logs submissions to the browser console. To connect it to a backend:

1. Find the form submission handler (around line ~815)
2. Replace the `console.log` with your preferred form handling service:
   - [Formspree](https://formspree.io/)
   - [Netlify Forms](https://www.netlify.com/products/forms/)
   - Custom backend API

Example with Formspree:
```javascript
const response = await fetch('https://formspree.io/f/YOUR_FORM_ID', {
  method: 'POST',
  body: formData,
  headers: {
    'Accept': 'application/json'
  }
});
```

## Customization

### Colors

The color palette is defined in CSS variables at the top of the `<style>` section (around line ~257):

```css
:root {
  --color-primary: #F5F1EA;      /* Warm white */
  --color-secondary: #E8DED2;    /* Soft beige */
  --color-accent: #A67B5B;       /* Clay brown */
  --color-accent-dark: #6B5744;  /* Dark clay */
  --color-text: #3A3A3A;         /* Charcoal */
  --color-text-light: #6B6B6B;   /* Medium gray */
  --color-bg: #FEFCF8;           /* Off-white background */
}
```

Adjust these values to match your preferred color scheme.

### Typography

The site uses:
- **Headings**: Crimson Pro (serif) - elegant, artistic
- **Body Text**: Inter (sans-serif) - clean, readable

To change fonts, update the Google Fonts link in the `<head>` section and the CSS variables.

### Adding More Gallery Items

To add more pieces to a category, duplicate a gallery item block in the HTML:

```html
<div class="gallery-item" data-category="moon-jugs">
  <img src="/images/moon-jug-4.jpg" alt="Moon jug ceramic piece" class="gallery-image" />
</div>
```

You can add as many items as you like - the responsive grid will adjust automatically.

## Project Structure

```
amna-ceramics/
├── public/
│   └── images/          # Place your ceramic photos here
├── src/
│   └── pages/
│       └── index.astro  # Main portfolio page
├── astro.config.mjs     # Astro configuration
├── package.json         # Dependencies
└── README.md           # This file
```

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)

## License

© 2024 Amna Ceramics. All rights reserved.

## Support

For questions or issues with the site, please check the [Astro documentation](https://docs.astro.build/).
