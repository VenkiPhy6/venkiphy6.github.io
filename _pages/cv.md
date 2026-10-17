---
layout: archive
title: "Resume & CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

<style>
  .cv-viewer {
    width: 100%;
  }

  .cv-tabs {
    display: flex;
    justify-content: center;
    gap: 0.5rem;
    border-bottom: 1px solid var(--global-border-color);
  }

  .cv-tab {
    margin: 0;
    padding: 0.75rem 1rem;
    border: 0;
    border-bottom: 3px solid transparent;
    background: transparent;
    color: var(--global-text-color);
    cursor: pointer;
    font: inherit;
  }

  .cv-tab[aria-selected="true"] {
    border-bottom-color: var(--global-link-color);
    color: var(--global-link-color);
    font-weight: 700;
  }

  .cv-viewer__actions {
    margin: 1rem 0;
  }

  .cv-viewer iframe {
    display: block;
    width: 100%;
    height: 85vh;
    min-height: 640px;
    border: 0;
  }

  @media (max-width: 768px) {
    .cv-viewer iframe {
      height: 75vh;
      min-height: 500px;
    }
  }
</style>

<div class="cv-viewer">
  <div class="cv-tabs" role="tablist" aria-label="Choose a document">
    <button
      class="cv-tab"
      id="resume-tab"
      type="button"
      role="tab"
      aria-selected="true"
      aria-controls="cv-pdf-preview"
      tabindex="0"
      data-pdf="/files/Venkatesh_Resume.pdf"
      data-title="Resume">
      Resume
    </button>
    <button
      class="cv-tab"
      id="cv-tab"
      type="button"
      role="tab"
      aria-selected="false"
      aria-controls="cv-pdf-preview"
      tabindex="-1"
      data-pdf="/files/Venkatesh_acadCV.pdf"
      data-title="CV">
      CV
    </button>
  </div>

  <p class="cv-viewer__actions">
    <a id="cv-download-link" href="/files/Venkatesh_Resume.pdf" target="_blank" rel="noopener">
      Download Resume
    </a>
  </p>

  <iframe
    id="cv-pdf-preview"
    src="/files/Venkatesh_Resume.pdf"
    title="Resume preview">
  </iframe>
</div>

<script>
  (function () {
    var tabs = Array.prototype.slice.call(document.querySelectorAll('.cv-tab'));
    var preview = document.getElementById('cv-pdf-preview');
    var downloadLink = document.getElementById('cv-download-link');

    function selectTab(tab) {
      tabs.forEach(function (item) {
        var selected = item === tab;
        item.setAttribute('aria-selected', selected ? 'true' : 'false');
        item.setAttribute('tabindex', selected ? '0' : '-1');
      });

      preview.src = tab.dataset.pdf;
      preview.title = tab.dataset.title + ' preview';
      downloadLink.href = tab.dataset.pdf;
      downloadLink.textContent = 'Download ' + tab.dataset.title;
    }

    tabs.forEach(function (tab, index) {
      tab.addEventListener('click', function () {
        selectTab(tab);
      });

      tab.addEventListener('keydown', function (event) {
        var nextIndex = index;
        if (event.key === 'ArrowRight') nextIndex = (index + 1) % tabs.length;
        else if (event.key === 'ArrowLeft') nextIndex = (index - 1 + tabs.length) % tabs.length;
        else if (event.key === 'Home') nextIndex = 0;
        else if (event.key === 'End') nextIndex = tabs.length - 1;
        else return;

        event.preventDefault();
        tabs[nextIndex].focus();
        selectTab(tabs[nextIndex]);
      });
    });
  }());
</script>

<!-- Education
======
* Ph.D in Version Control Theory, GitHub University, 2018 (expected)
* M.S. in Jekyll, GitHub University, 2014
* B.S. in GitHub, GitHub University, 2012

Work experience
======
* Spring 2024: Academic Pages Collaborator
  * GitHub University
  * Duties includes: Updates and improvements to template
  * Supervisor: The Users

* Fall 2015: Research Assistant
  * GitHub University
  * Duties included: Merging pull requests
  * Supervisor: Professor Hub

* Summer 2015: Research Assistant
  * GitHub University
  * Duties included: Tagging issues
  * Supervisor: Professor Git
  
Skills
======
* Skill 1
* Skill 2
  * Sub-skill 2.1
  * Sub-skill 2.2
  * Sub-skill 2.3
* Skill 3

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Service and leadership
======
* Currently signed in to 43 different slack teams -->
