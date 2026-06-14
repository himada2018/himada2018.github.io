================================================================================
================================================================================
  UPDATE ROUTINES — what to add/edit, and where, for each section
================================================================================
================================================================================

--------------------------------------------------------------------------------
  GIGS  ("What's on")
--------------------------------------------------------------------------------
WHERE: _data/gigs.yml
HOW:   add a block per gig, soonest first; delete past ones anytime.

    - date: "Sep 22"          # badge top line
      year: "2026"            # badge bottom line
      title: "Stevie Wonder Night"
      venue: "Hersham Music Club · 21:30"
      link: "https://..."     # optional; delete the line if none

If you delete ALL gigs, the page automatically shows
"No gigs scheduled at the moment — check back soon." — so it's never blank/TBA.

--------------------------------------------------------------------------------
  NEWS FEED  (the right-hand column)
--------------------------------------------------------------------------------
WHERE: _data/lab_news.yml  (lab page)   and/or   _data/news.yml  (homepage)
HOW:   add a block at the TOP (newest first). `link` is optional.

    - date: "Jul 2026"
      text: "Our paper on X was accepted at **Journal Name**."
      link: "https://doi.org/..."        # optional; delete the line if none

  - date = free text (type any date you like; nothing is auto-dated)
  - text = supports **bold**, *italic*, [links](https://...)
  Order in the file = order shown. ~5 show, rest scroll inside the column.
  (Or build it visually with tools/news-generator.html, then paste back.)

--------------------------------------------------------------------------------
  CORE MEMBERS  (the photo cards)
--------------------------------------------------------------------------------
WHERE: _pages/lab.md, inside <div class="member-grid"> ... </div>
PHOTOS: upload to images/members/ (square-ish; cropped to a circle)

  WITH a photo:
    <div class="member-card">
      <img class="member-card__photo" src="/images/members/their-name.jpg" alt="Full Name" />
      <div class="member-card__name"><a href="PROFILE-URL">Full Name</a></div>
      <div class="member-card__role">Role</div>
    </div>

  WITHOUT a photo (initials circle):
    <div class="member-card">
      <div class="member-card__initials">FN</div>
      <div class="member-card__name">Full Name</div>
      <div class="member-card__role">Role</div>
    </div>

  - Drop the <a href> to leave a name unlinked.
  - "FN" = the person's initials.
  - To REMOVE a member, delete their whole <div class="member-card"> block
    (or move them to the alumni table).

--------------------------------------------------------------------------------
  UNDERGRADUATE MEMBERS  (table)
--------------------------------------------------------------------------------
WHERE: _pages/lab.md, in the Undergraduate members <table> <tbody>
ADD/EDIT a row:
    <tr><td>Full Name</td><td>Role title</td></tr>
LINK a name:
    <tr><td><a href="URL">Full Name</a></td><td>Role title</td></tr>
REMOVE / GRADUATED: delete the row, or move it to Lab alumni (add Years cell).

--------------------------------------------------------------------------------
  LAB ALUMNI  (table)
--------------------------------------------------------------------------------
WHERE: _pages/lab.md, in the Lab alumni <table> <tbody>
ADD a row (3 cells: name, role, years):
    <tr><td>Full Name</td><td>Role title</td><td>2024-2025</td></tr>
LINK a name:
    <tr><td><a href="URL">Full Name</a></td><td>Role</td><td>2024-2025</td></tr>

--------------------------------------------------------------------------------
  RECENT PAPERS  (auto-updating grid)
--------------------------------------------------------------------------------
WHERE: nothing to edit on the lab page — it pulls from _publications/.
TO ADD A PAPER: create the publication file as usual (tools/pub-generator.html),
  drop it in _publications/. The grid shows the 6 newest by filename, so name
  new files with a higher number (e.g. 2026-02.md) to keep recency correct.
TO SHOW A JOURNAL COVER on a paper:
  1. put ONE image in images/journals/<slug>.jpg
       e.g. images/journals/cognition-and-emotion.jpg
  2. add this line to that paper's front matter in _publications/:
       journal: cognition-and-emotion
  Every paper in that journal reuses the same cover. No journal: line = a clean
  citation-only card (always safe). Only add the line once the image exists.
  (The pub-generator now has a "Journal slug" field that writes this for you.)
TO CHANGE HOW MANY SHOW: in _pages/lab.md edit the number in
       {% include recent-papers.html count=6 %}

--------------------------------------------------------------------------------
  PROJECTS  (rails) — see section (2) above for the card snippets
--------------------------------------------------------------------------------
WHERE: _pages/lab.md, inside the relevant <div class="project-rail">
Each project card links to a page in _projects/. To make the actual project
page, copy _projects/_TEMPLATE.md (see your earlier project guide) and match
its permalink to the card's href.

================================================================================
  AFTER ANY EDIT
================================================================================
Commit (and push). GitHub Pages rebuilds in ~1 min. Hard-refresh the page to
clear cached CSS (Ctrl+Shift+R / Cmd+Shift+R). If a build goes red in the
repo's Actions tab, the usual cause is a stray character in YAML (_data files
or front matter) or a missing </tr>/</div> in an edited block.
