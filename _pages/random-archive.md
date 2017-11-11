---
title: "Archive of Randomness"
layout: splash
permalink: /random/
date: 2016-03-23T11:48:41-04:00
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/wiiu-1.jpg
  cta_label: "Go To Randomic Archive"
  cta_url: "/random/#rand_archive"
  caption: "Photo credit: [**Me**](/)"
excerpt: "Welcome to the **Archive of Randomness**, the only **_crazy_** archive of this site."
intro: 
  - excerpt: 'Are you really sure you want to continue? The content below is not suitable for babies under `9999` years of age.'
vid_pcs:
  - title: "Placeholder: PCS"
    excerpt: "Placeholder: PCS descr"
    id: "imtheid"
feature_row2:
  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
    title: "Placeholder Image Left Aligned"
    excerpt: 'This is some sample content that goes here with **Markdown** formatting. Left aligned with `type="left"`'
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
feature_row3:
  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
    title: "Placeholder Image Right Aligned"
    excerpt: 'This is some sample content that goes here with **Markdown** formatting. Right aligned with `type="right"`'
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
feature_row4:
  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
    title: "Placeholder Image Center Aligned"
    excerpt: 'This is some sample content that goes here with **Markdown** formatting. Centered with `type="center"`'
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
---

{% include feature_row id="intro" type="center" %}

<h2 id="rand_archive">Randomic Archive <small>(or Archive of Randomness)</small></h2>

    <div class="feature__item">
      <div class="archive__item">

<!-- Courtesy of embedresponsively.com //-->
<div class="responsive-video-container">
  <iframe src="https://www.youtube.com/embed/{{ page.vid_pcs.id }}" frameborder="0" allowfullscreen></iframe>
</div>
          </div>
        {% endif %}

        <div class="archive__item-body">
          {% if page.vid_pcs.title %}
            <h2 class="archive__item-title">{{ page.vid_pcs.title }}</h2>
          {% endif %}

          {% if page.vid_pcs.excerpt %}
            <div class="archive__item-excerpt">
              {{ f.excerpt | markdownify }}
            </div>
          {% endif %}

          {% if page.vid_pcs.url %}
            <p><a href="{{ f_url }}" class="btn {{ f.btn_class }}">{{ f.btn_label | default: site.data.ui-text[site.locale].more_label | default: "Learn More" }}</a></p>
          {% endif %}
        </div>
      </div>

{% include feature_row id="feature_row2" type="left" %}

{% include feature_row id="feature_row3" type="right" %}

{% include feature_row id="feature_row4" type="center" %}