---
layout: default
title: Home
---

{% assign numgrant = 0 %}
{% for grant in site.grants %}
  {% assign numgrant = numgrant | plus: 1 %}
{% endfor %}

An increasing number of researchers are sharing their grant proposals
openly. They do this to open up science so that all stages of the process can
benefit from better interaction and communication and to provide examples for
early career scientists writing grants. This is a list of {{ numgrant }} of
these proposals to help you find them.


{% include sort.html %}
<table id='sTable'>
  <tr>
    <th nowrap onclick="sort(0)"> Year <i class="fa fa-sort" aria-hidden="true"></i> </th>
    <th nowrap onclick="sort(1)"> Funder <i class="fa fa-sort" aria-hidden="true"></i></th>
    <th nowrap onclick="sort(2)"> Title <i class="fa fa-sort" aria-hidden="true"></i></th>
    <th nowrap onclick="sort(3)"> Funded <i class="fa fa-sort" aria-hidden="true"></i></th>
  </tr>

{% for grant in site.grants %}
  <tr>
    <td>{{ grant.year }}</td>
	<td>{{ grant.funder }}</td>
	<td><a href="{{ grant.link }}">{{ grant.title }}</a> <small> by {{ grant.author }}</small></td>
	{% if grant.status == 'funded' or grant.status == 'partially funded' %}
	  <td>Yes</td>
	{% elsif grant.status == 'unfunded' or grant.status == 'not funded' %}
	  <td>No</td>
	{% else %}
	  <td>?</td>
	{% endif %}
  </tr>
{% endfor %}
</table>
