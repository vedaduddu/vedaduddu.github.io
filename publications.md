---
layout: page
title: Publications
---

*Papers, preprints, and workshop contributions. <sup>✱</sup> denotes equal contribution. See also: [Public Writing](#public-writing).*

<div class="blog-filters" style="margin: 1.5rem 0 1rem;">
  <button class="filter-btn active" data-filter="all">All</button>
  <button class="filter-btn" data-filter="accepted">Accepted</button>
  <button class="filter-btn" data-filter="first-author">First Author</button>
  <button class="filter-btn" data-filter="preprint">Preprint</button>
</div>

<div class="pub-list" id="pub-list">

  <div class="pub-item" data-tags="accepted">
    <div class="pub-year">2026</div>
    <div class="pub-details">
      <p class="pub-title">Do We Know What They Know We Know? Calibrating Student Trust in AI and Human Responses Through Mutual Theory of Mind</p>
      <p class="pub-authors">Olivia Pal<sup>✱</sup>, <strong>Veda Duddu</strong><sup>✱</sup>, Agam Goyal, Drishti Goel, Koustuv Saha</p>
      <p class="pub-venue">CHI 2026 Extended Abstracts &middot; <a href="https://dl.acm.org/doi/pdf/10.1145/3772363.3799386" target="_blank" rel="noopener">ACM</a></p>
    </div>
  </div>

  <div class="pub-item" data-tags="accepted first-author preprint">
    <div class="pub-year">2026</div>
    <div class="pub-details">
      <p class="pub-title">AI-Mediated Negotiation: Design Reflections and Lessons</p>
      <p class="pub-authors"><strong>Veda Duddu</strong>, Jash Rajesh Parekh, Andy Mao, Hanyi Min, Ziang Xiao, Vedant Das Swain, and Koustuv Saha</p>
      <p class="pub-venue">CSCW 2026 Poster &middot; <a href="https://arxiv.org/pdf/2606.21886" target="_blank" rel="noopener">Preprint</a></p>
    </div>
  </div>

  <div class="pub-item" data-tags="accepted">
    <div class="pub-year">2026</div>
    <div class="pub-details">
      <p class="pub-title">When AI Supports Emotionally Demanding Service Work: Experimental Evidence from Customer Service Interactions</p>
      <p class="pub-authors">Lei Wang, Hanyi Min, <strong>Veda Duddu</strong>, Koustuv Saha, Vedant Das Swain</p>
      <p class="pub-venue">AI and the Future of Work 2026 &middot; Wharton Human-AI Research</p>
    </div>
  </div>

  <div class="pub-item" data-tags="preprint">
    <div class="pub-year">2026</div>
    <div class="pub-details">
      <p class="pub-title">Inform, Coach, Relate, Listen: Auditing LLM Caregiving Support Roles</p>
      <p class="pub-authors">Drishti Goel, Agam Goyal, <strong>Veda Duddu</strong>, Olivia Pal, Jeongah Lee, Qiuyue Joy Zhong, Violeta J. Rodriguez, Daniel S. Brown, Dong Whi Yoo, Ravi Karkar, Koustuv Saha</p>
      <p class="pub-venue">Under review &middot; <a href="https://arxiv.org/abs/2605.29473" target="_blank" rel="noopener">Preprint</a></p>
    </div>
  </div>

  <div class="pub-item" data-tags="first-author preprint">
    <div class="pub-year">2026</div>
    <div class="pub-details">
      <p class="pub-title">Not My Truce: Personality Differences in AI-Mediated Workplace Negotiation</p>
      <p class="pub-authors"><strong>Veda Duddu</strong>, Jash Rajesh Parekh, Andy Mao, Hanyi Min, Ziang Xiao, Vedant Das Swain, Koustuv Saha</p>
      <p class="pub-venue">Under review &middot; <a href="https://arxiv.org/abs/2604.00464" target="_blank" rel="noopener">Preprint</a></p>
    </div>
  </div>

  <div class="pub-item" data-tags="first-author preprint">
    <div class="pub-year">2025</div>
    <div class="pub-details">
      <p class="pub-title">Does AI Coaching Prepare Us for Workplace Negotiations?</p>
      <p class="pub-authors"><strong>Veda Duddu</strong>, Jash Rajesh Parekh, Andy Mao, Hanyi Min, Ziang Xiao, Vedant Das Swain, Koustuv Saha</p>
      <p class="pub-venue">Under review &middot; <a href="https://arxiv.org/abs/2509.22545" target="_blank" rel="noopener">Preprint</a></p>
    </div>
  </div>

  <div class="pub-item" data-tags="preprint">
    <div class="pub-year">2025</div>
    <div class="pub-details">
      <p class="pub-title">The Social Gaze of LLMs: A Literature Review of Multimodal Approaches to Human Behavior Understanding</p>
      <p class="pub-authors">Zihan Liu, Parisa Rabbani, <strong>Veda Duddu</strong>, Kyle Fan, Madison Lee, Yun Huang</p>
      <p class="pub-venue">Under review &middot; <a href="https://arxiv.org/abs/2510.23947" target="_blank" rel="noopener">Preprint</a></p>
    </div>
  </div>

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
