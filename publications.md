---
layout: page
title: Publications
---

{% assign total = site.data.publications | size %}
{% assign accepted_count = site.data.publications | where_exp: "p", "p.tags contains 'accepted'" | size %}
{% assign first_author_count = site.data.publications | where_exp: "p", "p.tags contains 'first-author'" | size %}

*{{ total }} papers &middot; {{ accepted_count }} accepted &middot; {{ first_author_count }} first-author. <sup>✱</sup> denotes equal contribution. See also: [Public Writing](#public-writing).*

<div class="blog-filters" style="margin: 1.5rem 0 1rem;">
  <button class="filter-btn active" data-filter="all">All</button>
  <button class="filter-btn" data-filter="accepted">Accepted</button>
  <button class="filter-btn" data-filter="first-author">First Author</button>
  <button class="filter-btn" data-filter="preprint">Preprint</button>
</div>

<div class="pub-list" id="pub-list">
  {% for pub in site.data.publications %}
  <div class="pub-item" data-tags="{{ pub.tags | join: ' ' }}">
    <div class="pub-year">{{ pub.year }}</div>
    <div class="pub-details">
      <p class="pub-title">{{ pub.title }}</p>
      <p class="pub-authors">{{ pub.authors_html }}</p>
      <p class="pub-venue">{{ pub.venue }}{% for link in pub.links %} &middot; <a href="{{ link.url }}" target="_blank" rel="noopener">{{ link.label }}</a>{% endfor %}</p>
    </div>
  </div>
  {% endfor %}
</div>

<p id="no-pubs" style="display:none; text-align:center; color:var(--color-text-muted); font-style:italic; padding:2rem 0;">No publications match this filter.</p>

<script>
(function () {
  var btns  = document.querySelectorAll('.blog-filters .filter-btn');
  var items = document.querySelectorAll('#pub-list .pub-item');
  var empty = document.getElementById('no-pubs');

  function apply(filter) {
    btns.forEach(function (b) {
      b.classList.toggle('active', b.dataset.filter === filter);
    });
    var visible = 0;
    items.forEach(function (item) {
      var tags = (item.dataset.tags || '').split(' ');
      var show = filter === 'all' || tags.indexOf(filter) !== -1;
      item.style.display = show ? '' : 'none';
      if (show) visible++;
    });
    empty.style.display = visible === 0 ? '' : 'none';
    if (filter === 'all') {
      history.replaceState(null, '', window.location.pathname);
    } else {
      history.replaceState(null, '', '#' + filter);
    }
  }

  btns.forEach(function (btn) {
    btn.addEventListener('click', function () { apply(btn.dataset.filter); });
  });

  var hash = window.location.hash.slice(1);
  if (['accepted', 'first-author', 'preprint'].indexOf(hash) !== -1) {
    apply(hash);
  }
})();
</script>

---

## Public Writing

Essays, blog posts, and other writing outside the academic publication pipeline.

---

**From Diamond Mining to Open-World Survival: Alignment and Misalignment in RL Agents**  
Daniel Zhang, Melvin Huang, Hassan Dawy, **Veda Duddu**, Kevin Zhu, Sean O'Brien, Vasu Sharma, Sunishchal Dev  
*LessWrong · 2025* · [Blog post](https://www.lesswrong.com/posts/GSuoKJYTQYPktBp8A/from-diamond-mining-to-open-world-survival-alignment-and-1)
