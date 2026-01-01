# Deployment Guide

This site can be deployed to various hosting platforms. Here are recommended options:

## Netlify (Recommended)

1. Push your code to GitHub
2. Go to [Netlify](https://www.netlify.com/)
3. Click "Add new site" > "Import an existing project"
4. Connect your GitHub repository
5. Build settings:
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Click "Deploy site"

Your site will be live at a Netlify URL (e.g., `your-site.netlify.app`). You can add a custom domain in the site settings.

## Vercel

1. Push your code to GitHub
2. Go to [Vercel](https://vercel.com/)
3. Click "Add New" > "Project"
4. Import your GitHub repository
5. Vercel will auto-detect Astro and configure build settings
6. Click "Deploy"

## GitHub Pages

1. Install the Astro GitHub Pages adapter:
```bash
npm install @astrojs/github-pages
```

2. Update `astro.config.mjs`:
```javascript
import { defineConfig } from 'astro/config';

export default defineConfig({
  site: 'https://yourusername.github.io',
  base: '/repository-name',
});
```

3. Add to `.github/workflows/deploy.yml`:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm install
      - run: npm run build
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

4. Push to GitHub and enable GitHub Pages in repository settings

## Custom Domain

After deployment, you can connect a custom domain (e.g., `amnaceramics.com`):

1. Purchase a domain from a registrar (Namecheap, Google Domains, etc.)
2. In your hosting platform (Netlify/Vercel), go to Domain Settings
3. Follow the platform's instructions to add your custom domain
4. Update DNS records at your registrar to point to the hosting platform

## Environment Variables

If you add a backend service for form handling (Formspree, etc.), add environment variables in your hosting platform's dashboard:

- Netlify: Site settings > Build & deploy > Environment
- Vercel: Project settings > Environment Variables

## Performance Tips

Before deploying:

1. **Optimize images**: Use tools like TinyPNG to compress all images
2. **Test build locally**: Run `npm run build` to ensure it builds successfully
3. **Preview production**: Run `npm run preview` to test the built site locally

## Monitoring

After deployment, use these tools to monitor your site:

- **Google Analytics**: Track visitor statistics
- **Google Search Console**: Monitor SEO and search performance
- **Lighthouse**: Test performance, accessibility, and SEO scores

## Support

- [Astro Documentation](https://docs.astro.build/)
- [Netlify Documentation](https://docs.netlify.com/)
- [Vercel Documentation](https://vercel.com/docs)
