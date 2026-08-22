---
layout: page
permalink: /publications/
title: publications
description: publications by categories in reversed chronological order.
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

<!-- {% include bib_search.liquid %} -->

<div class="publications">

<!-- 탭 버튼 -->
  <div class="pub-tabs">
    <button class="pub-tab-btn active" data-tab="international">International</button>
    <button class="pub-tab-btn" data-tab="domestic">Domestic (KCI)</button>
    <button class="pub-tab-btn" data-tab="workshop">Workshop/Poster/Demo</button>
  </div>

  <!-- 국제 논문 -->
  <div class="pub-tab-content" id="international" style="display: block;">
    {% bibliography -q @*[keywords=international]* %}
  </div>

  <!-- 국내 논문 -->
  <div class="pub-tab-content" id="domestic" style="display: none;">
    {% bibliography -q @*[keywords=domestic]* %}
  </div>

  <div class="pub-tab-content" id="workshop" style="display: none;">
    {% bibliography -q @*[keywords=workshop]* %}
  </div>


</div>

<script>
document.addEventListener('DOMContentLoaded', function () {
  const buttons = document.querySelectorAll('.pub-tab-btn');
  const contents = document.querySelectorAll('.pub-tab-content');

  buttons.forEach(btn => {
    btn.addEventListener('click', function () {
      buttons.forEach(b => b.classList.remove('active'));
      this.classList.add('active');

      const target = this.getAttribute('data-tab');
      contents.forEach(c => {
        c.style.display = (c.id === target) ? 'block' : 'none';
      });
    });
  });
});
</script>
    
<style>
.pub-tabs {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}
.pub-tab-btn {
  padding: 0.5rem 1.2rem;
  border: 1px solid #999;
  background: transparent;
  border-radius: 6px;
  cursor: pointer;
  font-size: 1rem;
  color: var(--global-text-color);
}
.pub-tab-btn.active {
  background: #56f33d;
  color: white;
  border-color: #f5f7f8;
}
</style>