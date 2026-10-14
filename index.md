---
title: TotalLab security
---

# TotalLab security

## Report a vulnerability

Email **[security@totallab.com](mailto:security@totallab.com)** if you think
you have found a security vulnerability in a TotalLab product. Our
[vulnerability disclosure policy](policy) explains what to include and what
happens next.

## Security advisories

We publish an advisory for each vulnerability we have fixed in a TotalLab
product. Each advisory is available as a web page and as a machine-readable
[CSAF 2.0](https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html) document.

{% assign advisories = site.pages | where_exp: "p", "p.path contains 'advisories/'" | sort: "date" | reverse %}
{% if advisories.size == 0 %}
No advisories have been published yet.
{% else %}
| Advisory | Published | CSAF |
| --- | --- | --- |
{% for a in advisories %}| [{{ a.title }}]({{ a.url | relative_url }}) | {{ a.date | date: "%Y-%m-%d" }} | [JSON]({{ a.url | replace: ".html", ".json" | relative_url }}) |
{% endfor %}
{% endif %}
