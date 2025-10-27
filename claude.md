# Migration Plan: Squarespace to Jekyll GitHub Pages

## Project Overview
Migrate jacksonriso.com from Squarespace to Jekyll static site hosted on GitHub Pages. The site is a business process consulting portfolio showcasing services, case studies, and insights.

## Current Site Analysis

### Site Structure
- **Homepage** (index.html) - Hero section, services overview, value proposition
- **About** (about.html) - Personal background and expertise
- **Services**
  - Design and Build (design-and-build.html)
  - Document and Review (document-and-review.html)
- **Case Studies**
  - CoastFI Case Study (coastfi-case-study.html)
  - Storecaster Case Study (storecaster-case-study.html)
- **Insights** (Blog)
  - Main listing page (insights.html)
  - 6 blog posts in /insights/ directory:
    - How to Scale a Marketplace
    - Business Process Analysis
    - How to Turn Your Business Into a Digital Factory
    - The Goal: Enjoy Growing Your Business
    - How to Enjoy Growing Your Business
    - How to Vet Business Process Consultants
- **Work With Me** (work-with-me.html) - Services & contact
- **Contact** (contact.html) - Contact form
- **404** (404.html) - Custom error page

### Current Tech Stack
- **Platform**: Squarespace
- **Fonts**:
  - Adobe Typekit (dbIkN8Q...)
  - Google Fonts (Rubik: 300, 400, 500, 700)
- **Analytics**:
  - Google Analytics (G-TJZRMQJ69C)
  - Facebook Pixel (666475158867004)
  - Hotjar (3726510)

### Key SEO Elements to Preserve
- Meta descriptions
- Open Graph tags
- Twitter cards
- Canonical URLs
- Image alt text
- Structured data (Schema.org)

## Migration Plan

### Phase 1: Setup and Configuration (30 min)

#### 1.1 Jekyll Installation
```bash
# Install Jekyll and bundler
gem install jekyll bundler

# Create Gemfile
bundle init
# Add jekyll and github-pages gem
```

#### 1.2 Basic Configuration
- [x] Create _config.yml with site metadata
- [ ] Set up Gemfile with github-pages gem
- [ ] Configure permalink structure to match current URLs
- [ ] Set up collections for case studies

#### 1.3 Repository Setup
- [ ] Create GitHub repository: jacksonriso.github.io
- [ ] Configure GitHub Pages settings
- [ ] Set up custom domain (jacksonriso.com)
- [ ] Configure DNS records

### Phase 2: Design & Layout (2-3 hours)

#### 2.1 Layout Templates
Create Jekyll layouts in `_layouts/`:
- [ ] `default.html` - Base template with header/footer
- [ ] `page.html` - Standard pages
- [ ] `post.html` - Blog posts
- [ ] `case-study.html` - Case study pages
- [ ] `home.html` - Homepage specific layout

#### 2.2 Includes
Create reusable components in `_includes/`:
- [ ] `header.html` - Navigation bar
- [ ] `footer.html` - Footer with links
- [ ] `head.html` - Meta tags, stylesheets
- [ ] `analytics.html` - GA, FB Pixel, Hotjar
- [ ] `seo.html` - SEO meta tags

#### 2.3 Styling
- [ ] Extract and adapt CSS from Squarespace
- [ ] Create responsive grid system
- [ ] Implement mobile-first design
- [ ] Set up Sass/SCSS structure
- [ ] Configure fonts (Rubik from Google Fonts)
- [ ] Recreate color scheme and branding

### Phase 3: Content Migration (3-4 hours)

#### 3.1 Extract Content from HTML
For each page, extract:
- [ ] Main content body
- [ ] Headings and structure
- [ ] Images and assets
- [ ] Meta descriptions
- [ ] Page titles

#### 3.2 Convert to Markdown
- [ ] Homepage content → index.md
- [ ] About page → about.md
- [ ] Services pages → service pages
- [ ] Work with me → work-with-me.md
- [ ] Contact → contact.md
- [ ] 404 → 404.md

#### 3.3 Blog Posts
Create `_posts/` with proper naming (YYYY-MM-DD-title.md):
- [ ] Extract publication dates from meta tags
- [ ] Convert HTML to Markdown
- [ ] Add frontmatter (title, date, excerpt, image)
- [ ] Preserve SEO metadata

#### 3.4 Case Studies
Create `_case_studies/` collection:
- [ ] coastfi-case-study.md
- [ ] storecaster-case-study.md
- [ ] Add frontmatter (client, date, services, results)

### Phase 4: Asset Migration (1-2 hours)

#### 4.1 Images
- [ ] Download all images from Squarespace CDN
- [ ] Optimize images (compress, resize)
- [ ] Organize in `/assets/images/`
- [ ] Update image paths in content
- [ ] Create responsive image variants

#### 4.2 Other Assets
- [ ] Favicon
- [ ] Logo files
- [ ] Social sharing images
- [ ] Any PDFs or downloadables

### Phase 5: Features & Functionality (2-3 hours)

#### 5.1 Navigation
- [ ] Implement responsive navigation menu
- [ ] Mobile hamburger menu
- [ ] Active page highlighting

#### 5.2 Contact Form
Options:
- [ ] Formspree integration
- [ ] Netlify Forms (if using Netlify)
- [ ] Google Forms embed
- [ ] Custom solution with JavaScript

#### 5.3 Blog Features
- [ ] Blog listing page with excerpts
- [ ] Pagination (if needed)
- [ ] Categories/tags
- [ ] Related posts
- [ ] Social sharing buttons

#### 5.4 SEO & Analytics
- [ ] Jekyll SEO Tag plugin
- [ ] Sitemap.xml generation
- [ ] RSS feed
- [ ] Robots.txt
- [ ] Analytics tracking codes

### Phase 6: Testing & Optimization (1-2 hours)

#### 6.1 Cross-browser Testing
- [ ] Test on Chrome, Firefox, Safari, Edge
- [ ] Mobile responsive testing
- [ ] Tablet view testing

#### 6.2 Performance
- [ ] Image optimization
- [ ] CSS minification
- [ ] JavaScript minification
- [ ] Lazy loading images
- [ ] Check Lighthouse scores

#### 6.3 SEO Validation
- [ ] Verify all meta tags
- [ ] Check structured data
- [ ] Validate Open Graph tags
- [ ] Test social media previews
- [ ] Verify canonical URLs

#### 6.4 Content Review
- [ ] Proofread all content
- [ ] Check all internal links
- [ ] Verify external links
- [ ] Test contact form
- [ ] Check 404 page

### Phase 7: Deployment & Launch (1 hour)

#### 7.1 Pre-launch
- [ ] Final build test locally
- [ ] Review all pages
- [ ] Set up redirects (if URLs changed)
- [ ] Backup old Squarespace content

#### 7.2 Launch
- [ ] Push to GitHub
- [ ] Configure custom domain
- [ ] Update DNS records
- [ ] Enable HTTPS
- [ ] Submit sitemap to Google Search Console

#### 7.3 Post-launch
- [ ] Monitor analytics for issues
- [ ] Check Google Search Console for errors
- [ ] Set up uptime monitoring
- [ ] Create backup strategy

## Technical Considerations

### Jekyll Plugins
Add to Gemfile:
```ruby
gem "github-pages", group: :jekyll_plugins
gem "jekyll-seo-tag"
gem "jekyll-sitemap"
gem "jekyll-feed"
```

### URL Structure
Maintain current URL structure to preserve SEO:
- Blog posts: `/insights/post-title/`
- Case studies: `/case-study-name/`
- Pages: `/page-name/`

### Custom Domain Setup
1. Add CNAME file with: `jacksonriso.com`
2. Configure DNS:
   - A records pointing to GitHub Pages IPs
   - CNAME record for www subdomain

### Content Extraction Strategy
Use tools/scripts:
- BeautifulSoup (Python) to extract content from HTML
- Pandoc to convert HTML to Markdown
- Manual cleanup for formatting

## Timeline Estimate
- **Phase 1**: 30 minutes
- **Phase 2**: 2-3 hours
- **Phase 3**: 3-4 hours
- **Phase 4**: 1-2 hours
- **Phase 5**: 2-3 hours
- **Phase 6**: 1-2 hours
- **Phase 7**: 1 hour

**Total**: 11-16 hours

## Success Criteria
- [ ] All pages migrated with content intact
- [ ] Design closely matches Squarespace version
- [ ] Mobile responsive on all devices
- [ ] SEO metadata preserved
- [ ] Contact form functional
- [ ] Analytics tracking working
- [ ] Site loads in < 3 seconds
- [ ] Lighthouse score > 90
- [ ] Custom domain configured with HTTPS

## Resources Needed
- HTML content from old_jacksonriso.com folder
- Logo and brand assets
- Google Analytics account access
- Domain registrar access for DNS
- GitHub account

## Risks & Mitigation
1. **Content extraction complexity**: Manual review required
2. **Design recreation effort**: Use CSS framework to speed up
3. **Form functionality**: Use third-party service
4. **SEO ranking drop**: Maintain URLs, proper redirects, submit new sitemap quickly

## Next Steps
1. Review this plan
2. Set up development environment
3. Begin Phase 1: Setup and Configuration
4. Extract and convert content systematically
5. Test thoroughly before launch
