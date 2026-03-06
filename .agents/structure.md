# Repository Structure

The HIRO Group website is built with Jekyll. Below is a map of the most important directories and files.

## Key Directories

### `_data/`
Contains the core structured data for the site:
- `people.yml`: List of group members with their roles, subteams, and social links.
- `publications.yml`: Comprehensive database of research papers.
- `README.md`: Contains schema documentation for the YAML files.

### `_includes/`
Reusable HTML snippets for various page components:
- `header.html`, `footer.html`: Global navigation and footer.
- `js.html`, `css/`: Scripts and styles.
- `article.html`, `pubs.html`: Templates for rendering news and publications.

### `_layouts/`
Main page layouts (e.g., `default.html`).

### `_posts/`
Content stored as Markdown files, categorized by subdirectories:
- `news/`: News updates and announcements.
- `research/`: Detailed research project pages and subteam overviews.
- `wiki/`: Miscellaneous internal or public wiki articles.

### `img/`, `papers/`, `fonts/`
Static assets including images, publication PDFs, and web fonts.

## Top-Level Files
- `index.html`: Homepage layout.
- `people.html`, `publications.html`, `research.html`: Main landing pages.
- `_config.yml`: Global site settings, plugin configuration, and color palettes.
- `Gemfile`: Ruby dependencies for Jekyll.
