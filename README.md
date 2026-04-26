# Draft Bench Website

The official website for [Draft Bench](https://github.com/banisterious/obsidian-draft-bench), n Obsidian plugin for writers. Manage projects, scenes, and manuscripts with a full creative writing workflow.

**Live site:** [https://draftbench.io](https://draftbench.io)

## Built With

- [Hugo](https://gohugo.io/) - Static site generator
- [Blowfish Theme](https://github.com/nunocoracao/blowfish) - Modern Hugo theme

## Local Development

### Prerequisites

- Hugo Extended v0.158.0 or later

### Running Locally

```bash
# Clone with submodules
git clone --recurse-submodules https://github.com/banisterious/draftbench.io

# Start dev server
hugo server -D
```

Visit `http://localhost:1313` to view the site.

### Building

```bash
hugo --minify
```

Output will be in the `public/` directory.

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the `main` branch.

## License

MIT License - see [LICENSE](LICENSE) for details.
