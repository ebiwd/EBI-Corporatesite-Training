{% comment %}
We construct the site naviagion by loading a list of the site's pages
and filtering to just those with the front matter of:
  type: "half day"
{% endcomment %}
{% assign module_list = site.posts | sort:"order" %}
{% assign type = 'half day' %}
{% assign counter = 0 %}

<h2>Off-site half-day modules</h2>

<p class="small">This document gives a summary of the half-day modules made up of descriptions, audience / prerequisite knowledge, resources covered and expected learning outcomes.</p>

<p><a >Toggle Panel</a></p>


{% for node in module_list %}
  {% if type == node.type %}
    {% assign counter = counter | plus: 1 %}
    <span class="label">{{node.category}}</span>

    {% if "yes" == node.new %}
      <span class="tag">NEW</span>
    {% endif %}
    <h4 data-toggle="panel-{{counter}} teaser-{{counter}}">{{node.title}}</h4>
    <div class="" id="teaser-{{counter}}" data-toggler data-animate="hinge-in-from-top hide">
      {{node.content | strip_html | truncatewords: 30}}
    </div>
    <div class="row hidden" id="panel-{{counter}}" data-toggler data-animate="hinge-in-from-top">
      <div class="columns medium-7">
        {{node.content}}
        <a href="{{node.url}}" class="readmore">Learn more</a>
      </div>
      <div class="columns medium-5">
        <div><span class="tag">Resources</span><br/>{{node.resources | markdownify}}</div>
        <div><span class="tag">Outcomes</span> <br/>{{node.outcomes | markdownify}}</div>
        <div><span class="tag">Related</span>  <br/>{{node.related | markdownify}}</div>
      </div>
    </div>
    <hr/>

    {% if node.category == 'Cross-domain tools and resources' %}
    to do: group by category..
    {% endif %}
  {% endif %}
{% endfor %}

{% assign type = 'full day' %}

<h2>Off-site full day modules</h2>

<p class="small">This document gives a summary of the full-day modules made up of module descriptions, audience / prerequisite knowledge, resources covered and expected learning outcomes.</p>


{% for node in module_list %}
  {% if type == node.type %}
    {% assign counter = counter | plus: 1 %}
    <span class="label">{{node.category}}</span>

    {% if "yes" == node.new %}
      <span class="tag">NEW</span>
    {% endif %}
    <h4 data-toggle="panel-{{counter}} teaser-{{counter}}">{{node.title}}</h4>
    <div class="" id="teaser-{{counter}}" data-toggler data-animate="hinge-in-from-top hide">
      {{node.content | strip_html | truncatewords: 30}}
    </div>
    <div class="row hidden" id="panel-{{counter}}" data-toggler data-animate="hinge-in-from-top">
      <div class="columns medium-7">
        {{node.content}}
        <a href="{{node.url}}" class="readmore">Learn more</a>
      </div>
      <div class="columns medium-5">
        <div><span class="tag">Resources</span><br/>{{node.resources | markdownify}}</div>
        <div><span class="tag">Outcomes</span> <br/>{{node.outcomes | markdownify}}</div>
        <div><span class="tag">Related</span>  <br/>{{node.related | markdownify}}</div>
      </div>
    </div>
    <hr/>

    {% if node.category == 'Cross-domain tools and resources' %}
    to do: group by category..
    {% endif %}
  {% endif %}
{% endfor %}


{% assign pages_list = nil %}
{% assign group = nil %}
