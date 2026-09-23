---
layout: page
permalink: /media/
title: Inside Tongji MRL
kicker: Field Notes / Workshop Views
description: Build, test, observe and iterate — selected moments from Tongji MRL's RobotX preparation.
---

{% assign showcase_media = site.data.media | where: 'verified', true | where: 'showcase', true %}
{% assign usv_media = showcase_media | where: 'showcase_group', 'usv' | sort: 'showcase_order' %}
{% assign uav_media = showcase_media | where: 'showcase_group', 'uav' | sort: 'showcase_order' %}
{% assign team_intro_media = site.data.media | where: "id", "team-intro-video" | first %}
{% assign supporting_media = site.data.media | where: 'verified', true | where: 'showcase', false | sort: 'gallery_order' %}
{% assign team_story_media = supporting_media | where: 'gallery_group', 'team-story' %}
{% assign field_test_media = supporting_media | where: 'gallery_group', 'field-tests' %}
{% assign aerial_media = supporting_media | where: 'gallery_group', 'aerial-platform' %}
{% assign identity_media = supporting_media | where: 'gallery_group', 'team-identity' %}

<div class="media-wall-page" data-media-wall>
  <nav class="media-section-nav" aria-label="Media page sections">
    <a href="#team-intro-media">Team Intro</a>
    <a href="#platforms">Platforms</a>
    <a href="#usv-media">USV Media</a>
    <a href="#uav-media">UAV Media</a>
    <a href="#team-story-media">Team Story</a>
    <a href="#field-test-media">Field Tests</a>
    <a href="#aerial-media">Aerial</a>
    <a href="#identity-media">Identity</a>
  </nav>

  <section class="media-feature" id="team-intro-media" aria-labelledby="team-intro-title">
    <div class="media-feature-visual" style="--media-position: center;">
      {% include figure.liquid path=team_intro_media.poster alt=team_intro_media.alt class="media-feature-image" avoid_scaling=true sizes="(max-width: 699px) 100vw, 1120px" %}
      <button
        type="button"
        class="media-showcase-play media-feature-play"
        aria-label="Play {{ team_intro_media.title }}"
        data-media-open
        data-video-src="{{ team_intro_media.video | relative_url }}"
        data-video-poster="{{ team_intro_media.poster | relative_url }}"
        data-video-title="{{ team_intro_media.title }}"
        data-video-category="{{ team_intro_media.category }}"
      >
        <span aria-hidden="true"><i class="fa-solid fa-play"></i></span>
      </button>
    </div>
    <div class="media-feature-copy">
      <p class="media-section-kicker">Featured / Team Story</p>
      <h2 id="team-intro-title">{{ team_intro_media.title }}</h2>
      <p>{{ team_intro_media.description }}</p>
    </div>
  </section>

  <section class="media-platforms" id="platforms" aria-labelledby="platforms-title">
    <header class="media-section-intro">
      <p class="media-section-kicker">Our Platforms</p>
      <h2 id="platforms-title">Meet the fleet</h2>
      <p>Two complementary robotic platforms anchor our work across water and air.</p>
    </header>

    <div class="media-platform-grid">
      {% for system in site.data.systems %}
        <article class="media-platform-card" data-media-reveal>
          <div class="media-platform-float">
            <div class="media-platform-surface">
              <div class="media-platform-visual" style="--platform-position: {{ system.media_object_position | default: 'center' }}; --platform-fit: {{ system.media_fit | default: 'cover' }};">
                {% include figure.liquid path=system.image alt=system.image_alt class="media-platform-image" sizes="(max-width: 699px) 100vw, 50vw" %}
              </div>
              <div class="media-platform-copy">
                <span>{{ system.abbreviation }}</span>
                <h3>{{ system.name }}</h3>
                <p>{{ system.media_description }}</p>
                <a href="{{ '/robot-x/' | relative_url }}#{{ system.id }}">{{ system.media_link_label }} <i class="fa-solid fa-arrow-right" aria-hidden="true"></i></a>
              </div>
            </div>
          </div>
        </article>
      {% endfor %}
    </div>

  </section>

{% include media-showcase.liquid id="usv-media" kicker="USV Field Notes" title="USV Media" description="Surface-platform testing, assembly and electronics preparation." items=usv_media %}
{% include media-showcase.liquid id="uav-media" kicker="UAV Field Notes" title="UAV Media" description="Aerial-platform testing and development records." items=uav_media %}
{% include media-gallery.liquid id="team-story-media" kicker="Team Story" title="People & Team Moments" description="Introduction footage and candid team records that show the working atmosphere behind the platforms." items=team_story_media %}
{% include media-gallery.liquid id="field-test-media" kicker="Field Tests" title="Water-Side Testing" description="USV runs, field setup views and outdoor debugging records from practical test days." items=field_test_media %}
{% include media-gallery.liquid id="aerial-media" kicker="Aerial Platform" title="UAV Development" description="UAV flight and debugging records for the aerial platform." items=aerial_media %}
{% include media-gallery.liquid id="identity-media" kicker="Team Identity" title="Brand & Title Clips" description="Public-facing identity materials for Tongji MRL and Tongji RobotX." items=identity_media %}

</div>

<dialog class="media-viewer" data-media-viewer aria-labelledby="media-viewer-title">
  <div class="media-viewer-panel">
    <button type="button" class="media-viewer-close" data-media-close aria-label="Close video"><i class="fa-solid fa-xmark" aria-hidden="true"></i></button>
    <div class="media-viewer-stage" data-media-stage></div>
    <div class="media-viewer-copy">
      <p data-media-viewer-category></p>
      <h2 id="media-viewer-title" data-media-viewer-title></h2>
    </div>
  </div>
</dialog>
