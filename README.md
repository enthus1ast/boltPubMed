PubMed
======================

Fetches publications from the PubMed database.

Usage:
======

in your twig template you can use `pubmed_search("search term")`, which fetches all relevant
publications from PubMed


Example:
========

```twig
{% set term = "Muller S AND (SUMO OR PML OR Glycerolphosphate) NOT (Bachmair A OR Kögl M OR Heinzel T OR Kieffer Y)" %}
{% set publications = pubmed_search(term) %}
<p><strong>Publications from PubMed: {{publications | length}}</strong></p>

{% for entry in publications %}
  {{ entry.authors | join(", ") }}
  <i>{{entry.title}}</i>
  <strong>
    {{entry.journalabbrev}}
    {{entry.year}}
  </strong>

  {{entry.volume}}

  {%if entry.issue%}
    ({{entry.issue}})
  {% endif %}

  {{entry.pages}}

  <a target="_blank" href="http://www.ncbi.nlm.nih.gov/pubmed/{{entry.pmid}}">Link</a><br>

  <br>
{% endfor %}
```