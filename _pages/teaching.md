---
layout: page
permalink: /photo/
title: My Photography
description: During my spare time, I like travel and taking photos along the way. I also claim myself as an amateur astrophotographer, and a dedicated eclipse chaser!
nav: true
nav_order: 5
images:
  photoswipe: true
photos:
  - file: meteor
    title: Meteor above the campsite
    alt: The Milky Way and a bright meteor over a nighttime campsite
    width: 1280
    height: 1920
    tile: portrait
  - file: hercules-cluster
    title: The Hercules Globular Cluster (M13)
    alt: A bright, dense globular cluster surrounded by a field of stars
    details: Colyer Lake, PA · July 7, 2024
    width: 1924
    height: 1956
    tile: square
  - file: lagoon-trifid
    title: Lagoon and Trifid Nebulae (M8, M20) and M21
    alt: Two colorful nebulae and a nearby open cluster in a dense star field
    details: Colyer Lake, PA · July 27, 2024
    width: 3200
    height: 2069
    tile: landscape
  - file: milky-way
    title: Beneath the Milky Way
    alt: A photographer holding a camera beneath the Milky Way and a dark mountain ridge
    width: 3200
    height: 2133
    tile: half
  - file: eastern-veil
    title: The Eastern Veil Nebula (NGC 6992)
    alt: A curved ribbon of red and blue filaments against a field of stars
    details: Colyer Lake, PA · July 7, 2024
    width: 3200
    height: 2103
    tile: half
  - file: total-solar-eclipse
    title: Total solar eclipse sequence
    alt: Successive phases of the solar eclipse arranged around the bright corona at totality
    details: Poplar Bluff, MO · April 8, 2024
    width: 3200
    height: 1100
    tile: panorama
_styles: |
  html:has(.photography-wall) {
    container-type: inline-size;
  }

  .photography-wall {
    display: grid;
    grid-template-columns: repeat(12, minmax(0, 1fr));
    gap: 4px;
    width: 100cqw;
    margin-inline: calc((100% - 100cqw) / 2);
  }

  .photography-tile {
    position: relative;
    display: block;
    min-width: 0;
    overflow: hidden;
    background: #0c1830;
  }

  .photography-tile:focus-visible {
    outline: 2px solid #fff;
    outline-offset: -3px;
    z-index: 1;
  }

  .photography-tile--portrait { grid-column: span 3; aspect-ratio: 3 / 4; }
  .photography-tile--square { grid-column: span 4; }
  .photography-tile--landscape { grid-column: span 5; }
  .photography-tile--half { grid-column: span 6; aspect-ratio: 3 / 2; }
  .photography-tile--panorama { grid-column: 1 / -1; aspect-ratio: 3200 / 1100; }

  .photography-tile img {
    display: block;
    width: 100%;
    height: 100%;
    position: absolute;
    inset: 0;
    object-fit: cover;
  }

  .photography-caption {
    position: absolute;
    inset: auto 0 0;
    padding: 28px 12px 12px;
    background: linear-gradient(transparent, #050c19ef 40%);
    color: #fff;
    font-size: 0.8rem;
    line-height: 1.3;
    opacity: 0;
  }

  .photography-caption strong { display: block; font-size: 1rem; }
  .photography-tile:hover .photography-caption,
  .photography-tile:focus .photography-caption { opacity: 1; }

  @media (prefers-reduced-motion: no-preference) {
    .photography-caption { transition: opacity 180ms ease; }
  }

  @media (max-width: 575.98px) {
    .photography-wall { grid-template-columns: repeat(2, minmax(0, 1fr)); }
    .photography-tile--portrait,
    .photography-tile--square,
    .photography-tile--half { grid-column: span 1; }
    .photography-tile--landscape { grid-column: 1 / -1; aspect-ratio: 3 / 2; }
    .photography-caption { padding: 20px 8px 8px; }
    .photography-caption strong { font-size: 0.875rem; }
  }

  @media (hover: none) {
    .photography-caption { opacity: 1; }
  }
---

<div class="photography-wall pswp-gallery" aria-label="Astrophotography gallery" role="region">
  {% for photo in page.photos %}
    {% assign image_path = '/assets/img/photography/' | append: photo.file %}
    <a
      class="photography-tile photography-tile--{{ photo.tile }}"
      href="{{ image_path | append: '.webp' | relative_url }}"
      data-pswp-width="{{ photo.width }}"
      data-pswp-height="{{ photo.height }}"
    >
      <img src="{{ image_path | append: '-preview.webp' | relative_url }}" alt="{{ photo.alt | escape }}" decoding="async" loading="lazy">
      <span class="photography-caption">
        <strong>{{ photo.title | escape }}</strong>
        {{ photo.details | escape }}
      </span>
    </a>
  {% endfor %}
</div>
