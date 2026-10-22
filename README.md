# Awesome-PDF-Generation-Manipulation

# Top PDF Generation & Manipulation Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Programmatic Drawing, HTML-to-PDF Rendering & Server-Side Generation*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **PDF Generation & Manipulation**. These tools create PDF documents from scratch — drawing text, shapes, and tables programmatically, or converting HTML/CSS into print-ready pages — and then manipulate them through merging, splitting, and page-level operations.

**Examples** include PDFKit, jsPDF, pdfmake, Puppeteer, WeasyPrint, fpdf2, TCPDF, Aspose.PDF, IronPDF, and DocRaptor (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, programmatic layout control, and transparent rendering engines — ideal for backend engineers generating invoices at scale, frontend developers producing client-side PDFs, and teams avoiding per-document commercial API costs.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Aspose.PDF](https://products.aspose.com/pdf/)**  
  **The most feature-complete commercial PDF API** for .NET, Java, Python, and other platforms. Native APIs for creating, editing, converting, and rendering PDFs with full fidelity. Supports form fields, digital signatures, PDF/A compliance, and OCR. **Family pack from $1,199**. **Best for enterprise applications** requiring maximum format compatibility and broad platform support.

- **[IronPDF](https://ironsoftware.com/)**  
  **.NET PDF library with HTML-to-PDF conversion**, editing, and form handling. Simple API for common operations. **Best for .NET developers** wanting straightforward PDF generation without complex setup.

- **[DocRaptor](https://docraptor.com/)**  
  **Hosted HTML-to-PDF API powered by Prince XML** — the highest-fidelity HTML-to-PDF engine available. **Best for teams needing pixel-perfect print CSS** without running Prince locally. Usage-based pricing per document.

- **[Prince XML](https://www.princexml.com/)**  
  **The reference HTML-to-PDF engine** with the best CSS Paged Media support. Commercial licensing; **server licenses start around $3,800** for a single CPU. **Best for publishing workflows** requiring advanced typography and print-specific CSS.

## Open-Source GitHub Projects

- **[PDFKit](https://github.com/foliojs/pdfkit)**  
  **The high-performance server-side PDF generation library for Node.js** — MIT licensed . **Pure JavaScript with no Chromium dependency** — generates PDFs in **~8ms per document** for simple invoices, making it viable for high-volume generation without special infrastructure . **Stream-based API**: the `PDFDocument` object is a Node.js Readable stream, so pages can be piped to a write stream or HTTP response without holding the entire document in memory . **Programmatic drawing API** for text, paths, vector graphics, images, and tables. **Font handling**: loads TTF/OTF files directly and **subsets embedded fonts** — only glyphs actually used are included . **Trade-offs**: **no HTML/CSS rendering** — you draw everything with coordinates, which is prohibitively expensive if you need to replicate a web design . **Best for data-driven PDFs** (invoices, receipts, statements, certificates) where structure is defined by business logic rather than design iteration.

- **[jsPDF](https://github.com/parallax/jsPDF)**  
  **The most widely used client-side PDF library** — MIT licensed . **Generates PDFs entirely in the browser** without server involvement — ideal for "download receipt" buttons and client-side exports . **`html()` method** converts HTML content to PDF, though it depends on **html2canvas** and **dompurify** for rendering and sanitization . **UTF-8 support requires custom font embedding** — the 14 standard PDF fonts are ASCII-only, so non-Latin text requires converting TTF files via the fontconverter tool . **Two API modes**: "compat" mode matches the original MrRio version for plugin compatibility, while "advanced" mode (from the yWorks fork) enables patterns, FormObjects, and transformation matrices . **Security note**: jsPDF strongly advises sanitizing user input before passing it to the library . **Best for browser-side PDF generation** where you need simple documents without a server round-trip.

- **[pdfmake](https://github.com/bpampuch/pdfmake)**  
  **The declarative JSON-based PDF generator for client and server** — MIT licensed . **Define documents as JSON structures** rather than imperative drawing commands — excellent for standard business documents like invoices and reports where **layout consistency matters more than custom graphics** . **Built-in support for tables, columns, lists, images, and styling** with automatic page breaks. **Self-contained with VFS fonts** — font files embedded directly in the document definition . **Runs in both browser and Node.js** with the same document definition. **Trade-offs**: **less flexible for arbitrary graphics** than PDFKit's drawing API — the declarative model constrains what you can express . **Best for data-heavy reports** with dynamic tables and complex grids where consistency beats customization.

- **[Puppeteer](https://github.com/puppeteer/puppeteer)**  
  **The headless Chrome PDF renderer** — Apache 2.0 licensed . **`page.pdf()` renders any HTML/CSS to PDF** with modern CSS support (flexbox, grid, web fonts) via Chromium's print pipeline . **The correct tool when your PDF must faithfully render an existing web design** — dashboards, report pages, marketing material — where implementing the design twice (HTML/CSS plus a coordinate-based drawing API) is prohibitively expensive . **Trade-offs**: **browser startup costs ~800ms** — amortized with a persistent browser instance, per-page time drops to **~25ms** . **Chromium adds hundreds of MB install size and significant RAM per browser instance** . **Print pipeline edge cases can differ from on-screen CSS** . **Best for low-to-medium frequency generation** (a few hundred PDFs per day) where design fidelity matters more than raw throughput .

- **[WeasyPrint](https://github.com/Kozea/WeasyPrint)**  
  **The Python HTML/CSS-to-PDF rendering engine** — BSD licensed . **Turns simple HTML pages into statistical reports, invoices, and tickets** with a CSS layout engine written in Python, **designed for pagination** and meant to be easy to hack on . **Not based on a full rendering engine** like WebKit or Gecko — it's a dedicated print renderer . **Supports CSS Paged Media**, page breaks, running headers/footers, and complex layouts. **Python 3.9+**, tested on CPython and PyPy . **Trade-offs**: **not a pixel-perfect browser renderer** — complex CSS may render differently than Chrome . **Best for Python backends** generating styled reports from HTML templates without a browser dependency.

- **[fpdf2](https://github.com/py-pdf/fpdf2)**  
  **The simple and fast PDF generation library for Python** — LGPL-3.0 licensed . **Fork and successor of PyFPDF** with a user-friendly API and easy extensibility . **Unicode (UTF-8) TrueType font subset embedding** supporting almost any language including Chinese, Japanese, Korean, Hindi, and Arabic . **Features**: tables with automatic page breaks and text justification, images with transparency, barcodes and charts, internal/external links, document encryption and signing, annotations, table of contents, and basic Markdown-like styling . **Minimal dependencies**: Pillow, defusedxml, and fonttools . **Can embed Matplotlib, Pandas, and Plotly charts** as images . **Used by Harvard University in CS50** and in production projects like OpenDroneMap and Concordia . **Best for Python developers** wanting simple, dependency-light PDF generation with broad Unicode support.

- **[TCPDF](https://github.com/tecnickcom/TCPDF)**  
  **The long-standing PHP PDF generation library** — LGPL-3.0 licensed . **Single-class library with full Unicode support, font embedding and subsetting, barcodes (73 formats including QR and DataMatrix), and PDF/A parts 1-3 compliance** . **Supports bidirectional text (UAX #9)** and complex-script shaping for Arabic and Devanagari . **Deprecated in favor of tc-lib-pdf** — still maintained for legacy projects but not recommended for new development . **Best for existing PHP applications** already using TCPDF.

- **[mPDF](https://github.com/mpdf/mPDF)**  
  **The PHP HTML-to-PDF library with wide CSS support** — GPL-2.0 licensed . **FPDF-derived core** with HTML and CSS rendering, font embedding and subsetting, and Unicode support . **Wide subset of CSS3** including floats, positioning, and table layout . **Best for PHP applications** needing HTML-to-PDF conversion with more CSS support than FPDF's primitives offer.

- **[Dompdf](https://github.com/dompdf/dompdf)**  
  **The CSS 2.1 layout engine in PHP** — LGPL-2.1 licensed . **Renders HTML/CSS to PDF** with CSS 2.1 support and parts of CSS3 . **Font embedding and subsetting** (unreliable for OpenType CFF outlines) . **Best for PHP projects** needing straightforward HTML-to-PDF without mPDF's larger footprint.

- **[FPDF](https://github.com/Setasign/FPDF)**  
  **The minimal primitive drawing library for PHP** — permissive license with no attribution clause . **Basic text and primitive drawing** with core fonts and single-byte encodings . **Unicode only through the tFPDF fork** . **Best for legacy PHP projects** needing the simplest possible PDF generation.

### Additional Strong Open-Source Options

- **pdf-lib** — JavaScript library for creating and modifying PDFs in any environment. MIT licensed. Strong for PDF manipulation (merge, split, form filling) rather than generation from scratch .
- **borb** — Python library for reading, creating, and manipulating PDFs with a focus on layout and typography.
- **pypdf** — Pure Python PDF library for splitting, merging, cropping, and transforming pages.
- **wkhtmltopdf** — Command-line HTML-to-PDF converter using WebKit. Historically popular but **limited by its Qt dependency** — the patched Qt build is needed for headers, footers, and outlines [citation:4][citation:10].

**Frameworks for building custom systems**: Combine **PDFKit** for high-volume data-driven PDFs with minimal memory footprint, **pdfmake** for declarative JSON-defined reports with consistent layout, **jsPDF** for client-side generation without server round-trips, **Puppeteer** for design-faithful HTML-to-PDF when your PDF must match a web page, **WeasyPrint** or **fpdf2** for Python backends, and **TCPDF** or **mPDF** for PHP applications — to build a PDF generation stack tailored to your language ecosystem, throughput requirements, and design fidelity needs.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- PDF generation tools differ significantly in rendering approach, performance profile, and language ecosystem. **PDFKit generates at ~8ms per PDF** for simple invoices and streams pages without holding the document in memory — the right choice for high-volume data-driven generation . **Puppeteer's ~800ms browser startup** makes it unsuitable for per-request generation at scale, but amortized with a persistent browser it reaches ~25ms per page and is the correct tool when your PDF must faithfully render an existing web design . **jsPDF generates in the browser** but UTF-8 requires custom font embedding, and the `html()` method depends on html2canvas and dompurify . **pdfmake's declarative JSON model** is excellent for consistent report layouts but constrains arbitrary graphics . **TCPDF is deprecated** in favor of tc-lib-pdf — use for legacy projects only . **Aspose.PDF and IronPDF are commercial** with per-developer licensing costs.
- Self-hosted open-source solutions require proper font subsetting for non-Latin scripts, memory management for Chromium-based pipelines, and awareness that print CSS may render differently from screen CSS.

---

**Made for backend engineers, frontend developers, and teams generating PDFs programmatically or from HTML.**
Let's make PDF generation and manipulation more open, performant, and language-appropriate.
