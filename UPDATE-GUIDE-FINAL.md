================================================================================
  CIP LAB / HIROTAKA IMADA SITE — MASTER UPDATE GUIDE
  github.com/himada2018/himada2018.github.io
================================================================================

================================================================================
ADDING A NEW PAPER
================================================================================
1. Make the file with the publication generator (_publications/pub-generator.html).
2. Name it YYYY-NN.md with the NEXT number for that year (e.g. 2026-04.md).
   Higher number = newer within the year. Drop it in _publications/.
3. It appears automatically: in the right YEAR group on /publications/, and in
   the Recent papers grids on the home & lab pages.

Front-matter fields a paper can have:
  title:        "..."                 (required)
  collection:   publications          (required)
  permalink:    /publication/SLUG.pdf (required, unique)
  paperurl:     '/files/NAME.pdf'     (the PDF; omit if none)
  link:         'https://doi.org/...' (the DOI; shows the DOI button)
  journal:      slug                  (optional; shows the shared cover)
  online_first: true                  (optional; pins to In-press group, hides
                                        from Recent papers grids)
  citation:     '...'                 (the formatted citation)
  media:        (optional list — see D)
  blog:         (optional list — see E)

REMEMBER: inside single-quoted YAML, any apostrophe must be DOUBLED ('').
e.g. paperurl: '/files/D''Ottone (2025).pdf'

================================================================================
JOURNAL COVERS
================================================================================
One image per journal in images/journals/, named by slug, e.g.
  images/journals/cognition-and-emotion.jpg
Then add  journal: cognition-and-emotion  to each paper in that journal.
Covers can be jpg by default. For png/gif/webp, either:
  - use the journal: slug system only with .jpg, OR
  - set an explicit  cover: /images/journals/<name>.png  on the paper (any ext).

================================================================================
MEDIA COVERAGE ON A PAPER 
================================================================================
Add a `media:` list to the paper's front matter. Each entry = one outlet button
(e.g. BBC, The Guardian). Multiple allowed; they appear after PDF/DOI.

EXAMPLE (add inside the paper's --- front matter ---):

  media:
    - label: "BBC"
      url: "https://www.bbc.co.uk/news/..."
    - label: "The Guardian"
      url: "https://www.theguardian.com/..."

- label = the text on the button (the outlet name).
- url   = the article link.
- Delete the whole `media:` block if a paper has no coverage.
Buttons render in a subtle purple so they're distinct from PDF/DOI.

================================================================================
BLOG POSTS / SCIENCE COMMUNICATION  
================================================================================
Two parts: (1) create the blog post page, (2) link it from the paper card.

--- (1) CREATE THE BLOG POST ---
Copy blog_template/2026-01-01-example-blog-post.md to a new file. You can keep
all blog posts in a folder like  _blog/  (create it) or in _pages/. What matters
is the front matter, especially `permalink`.

Key front-matter fields (all set in the template):
  layout: blog                 (REQUIRED — gives the clean, no-sidebar layout)
  title / subtitle / eyebrow   headline area
  author / date / read_time    the small meta line
  permalink: /blog/your-slug/  THE URL of the post (make it unique)
  hero / hero_alt / hero_caption   optional top image (delete if unwanted)
  paper_title / paper_citation / paper_doi / paper_pdf
                               optional "Based on the paper" box at the bottom

Write the article body in plain Markdown below the front matter. Blog post pages
have NO right profile bar and NO news feed, and are width-limited and styled for
a lay audience (large readable text, subheads, pull quotes, images).

Put any images in images/blog/ and reference them like
  ![caption](/images/blog/your-image.jpg)

--- (2) LINK THE BLOG POST FROM THE PAPER CARD ---
Add a `blog:` list to the PAPER's front matter (in _publications/):

  blog:
    - label: "Plain-language summary"
      url: "/blog/your-slug/"

- label = button text (defaults to "Blog" if omitted).
- url   = the blog post's permalink (or any external sci-comm URL).
- Multiple allowed. Buttons render in a subtle green, after media buttons.
The blog button uses a ✎ pencil so it reads as "writing/blog".

================================================================================
LAB PAGE
================================================================================
File: _pages/lab.md

CORE MEMBERS (photo cards): edit inside <div class="member-grid">.
  WITH photo:
    <div class="member-card">
      <img class="member-card__photo" src="/images/members/name.jpg" alt="Full Name" />
      <div class="member-card__name"><a href="URL">Full Name</a></div>
      <div class="member-card__role">Role</div>
    </div>
  WITHOUT photo: swap the <img> line for
      <div class="member-card__initials">FN</div>
  Card size: edit $member-card-width / $member-photo-size at the top of _lab.scss.

PROJECTS (scrolling rails, 2 visible): add an <a class="project-card"> (research)
  or <a class="project-card project-card--impact"> (impact) inside the relevant
  <div class="project-rail">. Newest first stays visible; rest scroll right.

UNDERGRADUATE MEMBERS (table): edit rows
    <tr><td>Name</td><td>Role</td></tr>
  Link a name: <td><a href="URL">Name</a></td>

LAB ALUMNI (table, now ordered + scrolls):
  - Order: most recent graduate (higher end-year) at TOP; if two share a
    graduation year, the one who spent LONGER in the lab comes first.
  - The table shows about 5 people, then SCROLLS — visitors scroll within the
    table to see the rest. (This is the lab-table-wrap--scroll wrapper.)
  - Add a row (keep the order rule in mind):
      <tr><td>Name</td><td>Role</td><td>2024-2026</td></tr>
  - When someone leaves: move their row from Undergraduate members to here and
    add the Years-in-lab cell, placing it in the correct sorted position.

================================================================================
NEWS FEED
================================================================================
File: _data/news.yml.
Add at the top (newest first):
  - date: "Jul 2026"
    text: "Our paper on X is out in **Journal**."
    link: "https://..."        # optional

================================================================================
GIGS (HOMEPAGE "What's on")
================================================================================
File: _data/gigs.yml. Add soonest first:
  - date: "Sep 22"
    year: "2026"
    title: "Stevie Wonder Night"
    venue: "Hersham Music Club · 21:30"
    link: "https://..."         # optional
Empty file -> a friendly "no gigs scheduled" line shows automatically.


