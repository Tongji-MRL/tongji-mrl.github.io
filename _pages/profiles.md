---
layout: page
permalink: /people/
title: About Us
description: Meet the students and supervisor behind Tongji MRL.
nav: true
nav_order: 7
---

<main class="team-about-page">
  <section class="team-intro-section{% unless site.data.about.team_photo %} team-intro-section--compact{% endunless %} about-section-reveal">
    <div class="team-intro__content">
      <p class="section-label">About Tongji MRL</p>
      <h1>About Us</h1>
      <p>Tongji MRL is a multidisciplinary student team from Tongji University developing autonomous marine robotic systems for the 2026 Maritime RobotX Challenge.</p>
      <p>Our current development spans surface and aerial platforms.</p>
    </div>

    {% if site.data.about.team_photo %}
      <figure class="team-photo-slot">
        <img
          src="{{ site.data.about.team_photo | relative_url }}"
          alt="{{ site.data.about.team_photo_alt }}"
          width="1600"
          height="1000"
          loading="eager"
        >
      </figure>
    {% endif %}

  </section>

  <section class="section-panel leadership-section about-section-reveal" aria-labelledby="leadership-title">
    <header class="section-heading">
      <p class="section-label">Team Structure</p>
      <h2 id="leadership-title">Leadership</h2>
      <p class="team-interaction-note">Select a member card to view confirmed profile details. Names shown with a muted background indicate auxiliary participation in that subgroup.</p>
    </header>
    <div class="team-leadership leadership-grid">
      {% for member in site.data.team.members %}
        {% if member.leadership %}
          {% include team-member-trigger.liquid member=member variant="leadership" %}
        {% endif %}
      {% endfor %}
    </div>
  </section>

  <section class="section-panel hardware-section about-section-reveal" aria-labelledby="hardware-title">
    <header class="section-heading">
      <p class="section-label">Engineering</p>
      <h2 id="hardware-title">Hardware Group</h2>
    </header>
    <ul class="member-list">
      {% for member in site.data.team.members %}
        {% assign show_hardware_member = false %}
        {% for assignment in member.assignments %}
          {% if assignment.auxiliary != true %}
            {% if assignment.subgroup == "Control" or assignment.subgroup == "Mechanics" %}
              {% assign show_hardware_member = true %}
            {% endif %}
          {% endif %}
        {% endfor %}
        {% if show_hardware_member %}
          <li>
            {% include team-member-trigger.liquid member=member variant="list" %}
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </section>

  <section class="section-panel software-section about-section-reveal" aria-labelledby="software-title">
    <header class="section-heading">
      <p class="section-label">Autonomy</p>
      <h2 id="software-title">Software Group</h2>
    </header>
    <div class="subgroup-stack">
      {% include team-subgroup.liquid subgroup="Perception" title="Software — Perception" %}
      {% include team-subgroup.liquid subgroup="Planning" title="Software — Planning" %}
    </div>
  </section>

  <section class="section-panel publicity-section about-section-reveal" aria-labelledby="publicity-title">
    <header class="section-heading">
      <p class="section-label">Communication</p>
      <h2 id="publicity-title">Publicity Group</h2>
    </header>
    <div class="subgroup-stack">
      {% include team-subgroup.liquid subgroup="Publicity" %}
    </div>
  </section>

  <section class="section-panel video-section about-section-reveal" aria-labelledby="video-title">
    <header class="section-heading">
      <p class="section-label">Media</p>
      <h2 id="video-title">Video Showcase</h2>
    </header>
    <div class="video-showcase">
      <h3>Team Intro Video</h3>
      <p>Meet the people, platforms and preparation behind Tongji MRL.</p>
      <div class="responsive-video team-intro-video">
        {% include video.liquid path="assets/media/team-intro-video.mp4" poster="assets/media/team-intro-video-poster.jpg" alt="Tongji MRL team introduction video" controls=true preload="metadata" playsinline=true %}
      </div>
    </div>
  </section>

{% for member in site.data.team.members %}
{% include member-dialog.liquid member=member %}
{% endfor %}

</main>
