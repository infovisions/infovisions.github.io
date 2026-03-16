---
---

📊❤️ The **Information Visions Lab** is a research group led by [Evan Peck](https://evanpeck.github.io/) in the [Information Science Department](https://www.colorado.edu/cmci/infoscience) at the [University of Colorado Boulder](https://www.colorado.edu/). 

**What is does our group do?** We study how data profoundly affects people's lives—from everyday decisions about housing and healthcare to broader policies on climate change and pandemics. We believe **everyone** deserves the ability to see, use, and make decisions with data, empowering themselves and their communities.

Collectively, we envision a future of data communication that is accessible and equitable to all—regardless of culture, educational background, or ability to afford technology. Our research draws on information visualization tools and techniques to help diverse communities trust, create, and engage with data in meaningful ways.


{% include section.html %}

## Recent News

{% assign sorted_news = site.data.news | sort: "date" | reverse %}
<div class="news-list">
  {% for item in sorted_news limit:6 %}
  <div class="news-item">
    <div class="news-date">{{ item.date | date: "%b %Y" }}</div>
    <div class="news-text">
      {% if item.link and item.link != "#" %}
        <a href="{{ item.link }}">{{ item.text | markdownify | remove: "<p>" | remove: "</p>" }}</a>
      {% else %}
        {{ item.text | markdownify | remove: "<p>" | remove: "</p>" }}
      {% endif %}
    </div>
  </div>
  {% endfor %}
</div>

{% include section.html %}

<!-- ## Highlights

{% capture text %}

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

{%
  include button.html
  link="research"
  text="See our publications"
  icon="fa-solid fa-arrow-right"
  flip=true
  style="bare"
%}

{% endcapture %} 

{%
  include feature.html
  image="images/photo.jpg"
  link="research"
  title="Our Research"
  text=text
%}

{% capture text %}

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

{%
  include button.html
  link="projects"
  text="Browse our projects"
  icon="fa-solid fa-arrow-right"
  flip=true
  style="bare"
%}

{% endcapture %}

{%
  include feature.html
  image="images/photo.jpg"
  link="projects"
  title="Our Projects"
  flip=true
  style="bare"
  text=text
%}

{% capture text %}

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

{%
  include button.html
  link="team"
  text="Meet our team"
  icon="fa-solid fa-arrow-right"
  flip=true
  style="bare"
%}

{% endcapture %}

{%
  include feature.html
  image="images/photo.jpg"
  link="team"
  title="Our Team"
  text=text
%}
-->