---
title: "Publications"
permalink: /publications/
author_profile: true
---

<p class="pub-legend"><span class="pub-legend__star">*</span> Corresponding author &nbsp;·&nbsp; † Joint first authorship</p>


{% include base_path %}

<div class="pub-controls">
<input type="text" id="pubSearch" class="pub-search" placeholder="Search title, author, journal, year…" autocomplete="off" />
<div class="pub-yearchips" id="pubYearChips"></div>
</div>
<p class="pub-noresults" id="pubNoResults" style="display:none;">No matching papers.</p>

{% assign pubs = site.publications | sort: 'slug' | reverse %}
{% assign of_list = pubs | where: "online_first", true %}
{% if of_list and of_list.size > 0 %}
<div class="pub-year-block" data-year="press">
<h2 class="pub-year pub-year--press">In press</h2>
<div class="pub-year-group">
{% for post in of_list %}{% include publication-card.html %}{% endfor %}
</div>
</div>
{% endif %}
{% assign current_year = "" %}
{% for post in pubs %}{% unless post.online_first %}{% assign fname = post.path | split: "/" | last %}{% assign post_year = fname | slice: 0, 4 %}{% if post_year != current_year %}{% unless current_year == "" %}</div></div>{% endunless %}
<div class="pub-year-block" data-year="{{ post_year }}">
<h2 class="pub-year" id="year-{{ post_year }}">{{ post_year }}</h2>
<div class="pub-year-group">
{% assign current_year = post_year %}{% endif %}{% include publication-card.html %}{% endunless %}{% endfor %}
{% unless current_year == "" %}</div></div>{% endunless %}

<script>
(function(){
  function normalize(s){
    s = (s || '').toLowerCase();
    s = s.replace(/is(e|ed|es|ing|ation)/g, function(m,p){ return 'iz'+p; });
    s = s.replace(/(behavi|col|fav|hon|hum|lab|neighb|harb|flav|rum|val|vap|od|vig|rig)our/g, '$1or');
    s = s.replace(/yse/g,'yze');
    s = s.replace(/(catal|dial|analog|monol|prol)ogue/g,'$1og');
    s = s.replace(/modelling/g,'modeling').replace(/modelled/g,'modeled').replace(/labelling/g,'labeling').replace(/labelled/g,'labeled').replace(/travelling/g,'traveling').replace(/travelled/g,'traveled');
    s = s.replace(/ae/g,'e').replace(/oe/g,'e');
    s = s.replace(/centre/g,'center').replace(/theatre/g,'theater').replace(/metre/g,'meter');
    s = s.replace(/defence/g,'defense').replace(/offence/g,'offense').replace(/licence/g,'license');
    s = s.replace(/grey/g,'gray');
    return s;
  }
  function initPubFilter(){
    var search = document.getElementById('pubSearch');
    var chipsBox = document.getElementById('pubYearChips');
    var noResults = document.getElementById('pubNoResults');
    if(!search || !chipsBox){ return; }
    if(chipsBox.getAttribute('data-ready')){ return; }
    chipsBox.setAttribute('data-ready','1');

    var blocks = Array.prototype.slice.call(document.querySelectorAll('.pub-year-block'));
    var cards = Array.prototype.slice.call(document.querySelectorAll('.pub-card'));
    cards.forEach(function(card){
      card.setAttribute('data-search', normalize(card.textContent || ''));
    });

    var years = [];
    blocks.forEach(function(b){
      var y = b.getAttribute('data-year');
      if(y !== 'press' && years.indexOf(y) === -1){ years.push(y); }
    });

    var activeYear = 'all';

    function makeChip(label, val){
      var c = document.createElement('span');
      c.className = 'pub-chip' + (val==='all' ? ' pub-chip--active' : '');
      c.textContent = label;
      c.setAttribute('data-val', val);
      c.addEventListener('click', function(){
        activeYear = val;
        Array.prototype.forEach.call(chipsBox.children, function(ch){
          ch.classList.toggle('pub-chip--active', ch.getAttribute('data-val')===val);
        });
        apply();
      });
      return c;
    }
    chipsBox.appendChild(makeChip('All years','all'));
    years.forEach(function(y){ chipsBox.appendChild(makeChip(y, y)); });

    function apply(){
      var q = normalize(search.value || '').trim();
      var anyVisible = false;
      blocks.forEach(function(block){
        var by = block.getAttribute('data-year');
        var yearOk = (activeYear === 'all') ? true : (by === activeYear);
        if(by === 'press' && activeYear !== 'all'){ yearOk = false; }
        var blockCards = Array.prototype.slice.call(block.querySelectorAll('.pub-card'));
        var visibleInBlock = 0;
        blockCards.forEach(function(card){
          var text = card.getAttribute('data-search') || '';
          var match = yearOk && (q === '' || text.indexOf(q) !== -1);
          card.style.display = match ? '' : 'none';
          if(match){ visibleInBlock++; anyVisible = true; }
        });
        block.style.display = (yearOk && visibleInBlock > 0) ? '' : 'none';
      });
      noResults.style.display = anyVisible ? 'none' : '';
    }

    search.addEventListener('input', apply);
    search.addEventListener('keyup', apply);
    apply();
  }

  if(document.readyState === 'loading'){
    document.addEventListener('DOMContentLoaded', initPubFilter);
  } else {
    initPubFilter();
  }
  window.addEventListener('load', initPubFilter);
})();
</script>
