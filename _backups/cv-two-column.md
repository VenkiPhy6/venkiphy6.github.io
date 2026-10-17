---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

<style>
  .cv-documents {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1.5rem;
  }

  .cv-document iframe {
    display: block;
    width: 100%;
    height: 900px;
    border: none;
  }

  @media (max-width: 768px) {
    .cv-documents {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="cv-documents">
  <section class="cv-document">
    <h2>Resume</h2>
    <p>
      <a href="/files/Venkatesh_Resume.pdf" target="_blank" rel="noopener">
        Download Resume
      </a>
    </p>
    <iframe
      src="/files/Venkatesh_Resume.pdf"
      title="Resume">
    </iframe>
  </section>

  <section class="cv-document">
    <h2>CV</h2>
    <p>
      <a href="/files/Venkatesh_acadCV.pdf" target="_blank" rel="noopener">
        Download CV
      </a>
    </p>
    <iframe
      src="/files/Venkatesh_acadCV.pdf"
      title="CV">
    </iframe>
  </section>
</div>

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
