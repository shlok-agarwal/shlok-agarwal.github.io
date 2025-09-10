# Shlok Agarwal - Personal Website

This is the source code for Shlok Agarwal's personal website, built with Jekyll and hosted on GitHub Pages.

## Quick Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/shlok-agarwal/shlok-agarwal.github.io.git
   cd shlok-agarwal.github.io
   ```

2. **Install dependencies**:
   ```bash
   bundle install
   ```

3. **Run locally**:
   ```bash
   bundle exec jekyll serve
   ```
   
   The site will be available at `http://localhost:4000`

## File Structure

```
├── _config.yml          # Site configuration
├── _posts/              # Blog posts
├── _projects/           # Project collection
├── index.md             # Home page
├── about.md             # About page
├── blog.md              # Blog listing
├── resume.md            # Professional resume
├── CNAME                # Custom domain configuration
└── README.md            # This file
```

## Customization

### Update Personal Information
Edit `_config.yml` to update:
- Contact information
- Social media links
- Site description
- Skills and interests

### Add Blog Posts
Create new files in `_posts/` directory with format:
```
YYYY-MM-DD-title.md
```

### Add Projects
Create files in `_projects/` directory with project details.

### Customize Theme
The site uses the default Minima theme. You can customize:
- Layouts in `_layouts/`
- Stylesheets in `_sass/`
- Includes in `_includes/`

## Deployment

The site is automatically deployed to GitHub Pages when you push to the main branch.

### Custom Domain Setup
1. Add your domain to the `CNAME` file
2. Configure DNS settings with your domain provider
3. Enable HTTPS in GitHub Pages settings

## Local Development

### Prerequisites
- Ruby 2.7+
- Bundler gem
- Git

### Development Workflow
1. Make changes to content files
2. Test locally with `bundle exec jekyll serve`
3. Commit and push changes
4. GitHub Pages will automatically rebuild the site

## Content Management

### Blog Posts
- Write in Markdown format
- Include front matter with title, date, categories, and tags
- Use the sample post as a template

### Research Publications
- Update `research.md` with new publications
- Include proper citations and links
- Update citation metrics regularly

### Projects
- Use clear project descriptions
- Include technical details and outcomes
- Add images and demos when possible

## SEO Optimization

The site includes:
- Structured data for better search engine understanding
- Meta descriptions and social media tags
- XML sitemap generation
- Google Analytics support (optional)

## Performance

- Jekyll generates static files for fast loading
- Minified CSS and optimized images
- CDN-ready for global distribution

## Security

- HTTPS enabled by default
- No server-side code execution
- Regular dependency updates

## Support

For technical issues with the website:
1. Check Jekyll documentation
2. Review GitHub Pages documentation
3. Contact via the website contact form

---

**Live Site**: [https://shlok-agarwal.github.io](https://shlok-agarwal.github.io)  
**Repository**: [https://github.com/shlok-agarwal/shlok-agarwal.github.io](https://github.com/shlok-agarwal/shlok-agarwal.github.io)