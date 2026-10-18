---
layout: splash
title: "Slides Gallery"
permalink: /documents/
---

{% include base_path %}

<style>
  .slides-gallery {
    display: grid;
    grid-template-columns: minmax(250px, 300px) minmax(0, 1fr);
    gap: 2rem;
    align-items: start;
  }

  .slides-gallery__intro {
    margin-bottom: 2rem;
  }

  .slides-gallery__tabs {
    border-right: 1px solid var(--global-border-color);
    padding-right: 1rem;
  }

  .slides-gallery__tab {
    width: 100%;
    padding: 0.9rem 1rem;
    border: 0;
    border-left: 3px solid transparent;
    background: transparent;
    color: var(--global-text-color);
    text-align: left;
    font: inherit;
    cursor: pointer;
  }

  .slides-gallery__tab[aria-selected="true"] {
    border-left-color: var(--global-link-color);
    background: var(--global-border-color);
    color: var(--global-link-color);
    font-weight: 700;
  }

  .slides-gallery__content [hidden] {
    display: none !important;
  }

  .slides-gallery__grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(min(100%, 220px), 1fr));
    gap: 1.25rem;
  }

  .slide-image-link {
    display: block;
    overflow: hidden;
    border-radius: 0.25rem;
    background: #f5f5f5;
    transition: box-shadow 0.2s ease, transform 0.2s ease;
  }

  .slide-image-link:hover,
  .slide-image-link:focus-visible {
    transform: translateY(-2px);
    box-shadow: 0 0.4rem 1rem rgba(0, 0, 0, 0.18);
  }

  .slide-image-link img {
    display: block;
    width: 100%;
    aspect-ratio: 16 / 9;
    object-fit: contain;
  }

  @media (max-width: 768px) {
    .slides-gallery {
      grid-template-columns: 1fr;
      gap: 1rem;
    }

    .slides-gallery__tabs {
      border-right: 0;
      border-bottom: 1px solid var(--global-border-color);
      padding: 0 0 0.5rem;
    }

    .slides-gallery__tab {
      border-left: 0;
      border-bottom: 3px solid transparent;
      text-align: center;
    }

    .slides-gallery__tab[aria-selected="true"] {
      border-bottom-color: var(--global-link-color);
    }
  }
</style>

<section class="slides-gallery__intro" aria-label="About this gallery">
  <p>This page is a gallery of slide decks/posters I've made. The slides were used in talks as part of my teaching duties, and to present my research work at conferences. Click on the tabs on the left to see these slides.</p>
</section>

<div class="slides-gallery">
  <div class="slides-gallery__tabs" role="tablist" aria-label="Slide collections" aria-orientation="vertical">
    <button class="slides-gallery__tab" id="dissertation-research-tab" type="button" role="tab" aria-selected="true" aria-controls="dissertation-research-panel" tabindex="0">
      Dissertation Research
    </button>
    <button class="slides-gallery__tab" id="ang-fall-2026-tab" type="button" role="tab" aria-selected="false" aria-controls="ang-fall-2026-panel" tabindex="-1">
      American National Government (Fall 2026)
    </button>
    <button class="slides-gallery__tab" id="research-design-ii-tab" type="button" role="tab" aria-selected="false" aria-controls="research-design-ii-panel" tabindex="-1">
      Research Design II
    </button>
    <button class="slides-gallery__tab" id="other-tab" type="button" role="tab" aria-selected="false" aria-controls="other-panel" tabindex="-1">
      Other
    </button>
  </div>

  <div class="slides-gallery__content">
    <section id="dissertation-research-panel" role="tabpanel" aria-labelledby="dissertation-research-tab" tabindex="0">
    <p>Below are decks/posters I made to discuss my dissertation work in different venues.</p>
      <div class="slides-gallery__grid">
        {% assign dissertation_images = site.static_files | where_exp: "file", "file.path contains 'images/dissertation/'" | sort: "path" %}
        {% for thumbnail in dissertation_images %}
          {% assign dissertation_file = thumbnail.path | split: '/' | last | remove: '.jpg' %}
          {% assign pdf_path = dissertation_file | prepend: '/files/dissertation/' | append: '.pdf' %}
          <a class="slide-image-link" href="{{ pdf_path | relative_url }}" target="_blank" rel="noopener" aria-label="Open {{ dissertation_file | replace: '_', ' ' }} PDF in a new tab">
            <img src="{{ thumbnail.path | relative_url }}" alt="First page of {{ dissertation_file | replace: '_', ' ' }}" loading="lazy" decoding="async">
          </a>
        {% endfor %}
      </div>
    </section>

    <section id="ang-fall-2026-panel" role="tabpanel" aria-labelledby="ang-fall-2026-tab" tabindex="0" hidden>
    <p>Below are some of the slide decks I made to teach weekly in American National Government, a core course for freshmen at UTD. The flow of content is heavily inspired by <a href="https://tophat.com/catalog/social-sciences/political-science/full-course/introduction-to-american-government/4538/">the course textbook</a> (Brunell et al. (2022)). I supplemented it with other material referenced in the deck.</p>
    <div class="slides-gallery__grid">
      {% assign slide_images = site.static_files | where_exp: "file", "file.path contains 'images/ANG_teaching/'" | sort: "path" %}
      {% for thumbnail in slide_images %}
        {% assign slide_file = thumbnail.path | split: '/' | last | remove: '.jpg' %}
        {% assign pdf_path = slide_file | prepend: '/files/ANG_teaching/' | append: '.pdf' %}
        <a class="slide-image-link" href="{{ pdf_path | relative_url }}" target="_blank" rel="noopener" aria-label="Open {{ slide_file | replace: '_', ' ' }} PDF in a new tab">
          <img src="{{ thumbnail.path | relative_url }}" alt="First page of {{ slide_file | replace: '_', ' ' }}" loading="lazy" decoding="async">
        </a>
      {% endfor %}
    </div>
    </section>

    <section id="research-design-ii-panel" role="tabpanel" aria-labelledby="research-design-ii-tab" tabindex="0" hidden>
    <p>These are slide decks I made, as a Teaching Assistant, to facilitate workshops for students in Research Design II, a graduate-level core course primarily for social scientists. The content was made under the direction of <a href="https://natalialamberova.com/">Dr. Natalia Lamberova</a>. These workshops are quick refreshers on concepts in statistics.</p>
      <div class="slides-gallery__grid">
        {% assign rd2_images = site.static_files | where_exp: "file", "file.path contains 'images/rd2/'" | sort: "path" %}
        {% for thumbnail in rd2_images %}
          {% assign rd2_file = thumbnail.path | split: '/' | last | remove: '.jpg' %}
          {% assign pdf_path = rd2_file | prepend: '/files/rd2/' | append: '.pdf' %}
          <a class="slide-image-link" href="{{ pdf_path | relative_url }}" target="_blank" rel="noopener" aria-label="Open {{ rd2_file | replace: '_', ' ' }} PDF in a new tab">
            <img src="{{ thumbnail.path | relative_url }}" alt="First page of {{ rd2_file | replace: '_', ' ' }}" loading="lazy" decoding="async">
          </a>
        {% endfor %}
      </div>
    </section>

    <section id="other-panel" role="tabpanel" aria-labelledby="other-tab" tabindex="0" hidden>
      <div class="slides-gallery__grid">
        {% assign other_images = site.static_files | where_exp: "file", "file.path contains 'images/oneoffs/'" | sort: "path" %}
        {% for thumbnail in other_images %}
          {% unless thumbnail.path contains 'custom-external-thumbnail.jpg' or thumbnail.path contains 'cnsd.jpg' %}
            {% assign other_file = thumbnail.path | split: '/' | last | remove: '.jpg' %}
            {% assign pdf_path = other_file | prepend: '/files/oneoffs/' | append: '.pdf' | relative_url | replace: ' ', '%20' %}
            {% assign image_path = thumbnail.path | relative_url | replace: ' ', '%20' %}
            <a class="slide-image-link" href="{{ pdf_path }}" target="_blank" rel="noopener" aria-label="Open {{ other_file | replace: '_', ' ' }} PDF in a new tab">
              <img src="{{ image_path }}" alt="First page of {{ other_file | replace: '_', ' ' }}" loading="lazy" decoding="async">
            </a>
            {% if forloop.first %}
              <!-- The custom external image lives at images/oneoffs/custom-external-thumbnail.jpg. -->
              <a class="slide-image-link" href="https://venkatsub.com/venkislides/inno_pol" target="_blank" rel="noopener" aria-label="Open custom external resource in a new tab">
                <img src="{{ '/images/oneoffs/custom-external-thumbnail.jpg' | relative_url }}" alt="Custom external resource thumbnail" loading="lazy" decoding="async">
              </a>
            {% endif %}
          {% endunless %}
        {% endfor %}
        <a class="slide-image-link" href="{{ '/files/oneoffs/cnsd.pdf' | relative_url }}" target="_blank" rel="noopener" aria-label="Open CNSD PDF in a new tab">
          <img src="{{ '/images/oneoffs/cnsd.jpg' | relative_url }}" alt="First page of CNSD" loading="lazy" decoding="async">
        </a>
      </div>
    </section>
  </div>
</div>

<script>
  (function () {
    var tabs = Array.prototype.slice.call(document.querySelectorAll('.slides-gallery__tab'));

    function selectTab(tab, updateHash) {
      tabs.forEach(function (item) {
        var selected = item === tab;
        item.setAttribute('aria-selected', selected ? 'true' : 'false');
        item.setAttribute('tabindex', selected ? '0' : '-1');
        document.getElementById(item.getAttribute('aria-controls')).hidden = !selected;
      });

      if (updateHash && window.location.hash !== '#' + tab.id) {
        window.history.replaceState(null, '', '#' + tab.id);
      }
    }

    function selectTabFromHash() {
      var tab = document.getElementById(window.location.hash.slice(1));
      if (tabs.indexOf(tab) !== -1) selectTab(tab, false);
    }

    tabs.forEach(function (tab, index) {
      tab.addEventListener('click', function () {
        selectTab(tab, true);
      });

      tab.addEventListener('keydown', function (event) {
        var nextIndex = index;
        if (event.key === 'ArrowDown' || event.key === 'ArrowRight') nextIndex = (index + 1) % tabs.length;
        else if (event.key === 'ArrowUp' || event.key === 'ArrowLeft') nextIndex = (index - 1 + tabs.length) % tabs.length;
        else if (event.key === 'Home') nextIndex = 0;
        else if (event.key === 'End') nextIndex = tabs.length - 1;
        else return;

        event.preventDefault();
        tabs[nextIndex].focus();
        selectTab(tabs[nextIndex], true);
      });
    });

    window.addEventListener('hashchange', selectTabFromHash);
    selectTabFromHash();
  }());
</script>
