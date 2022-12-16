---
layout: home
---


{% if site.conference.schoolphoto %}
![](./assets/{{ site.conference.schoolphoto }})
{% endif %}
{% if site.conference.hosturl %} [Hosts Local Page]({{ site.conference.hosturl }})<br>{% endif %}
{% if site.conference.chairs %}{% for chair in site.conference.chairs %}{% if chair.type=="Organizers" %} organized by {% for person in chair.people %}{% include listperson.html%}{%endfor%}{%endif%}{%endfor%}{% endif %}

{% if site.conference.hosts %}hosted by {% for person in site.conference.hosts %}[{{ person.name }}]({{ person.url }}){% if site.conference.hosts | size > 1 %}, {% endif %}{% endfor %}{% endif %}

{% for date in site.conference.dates %}
## {{ date | date: '%A %d %B'}}
{% for slot in site.data.lectures %}
{% assign thedate = slot.date | date: '%Y-%m-%d' %}
{% assign otherdate = date | date: '%Y-%m-%d' %}
{% if otherdate == otherdate %}
{% if slot.start %}{{ slot.start }} {% if slot.end %}- {{ slot.end }} {% endif %}{% endif %}{% if slot.pdf %}[{{ slot.title }}]({{ slot.pdf }}){% else %}{{ slot.title }}{% endif %}{% if slot.speaker %}, {{ slot.speaker }}{% endif %}{% if slot.institution %}, {{ slot.institution }}{% endif %}{% if slot.ipynb %} [[jupyter notebook]({{ slot.ipynb }})]{% endif %}{% if slot.dataset %} [[dataset]({{ slot.dataset }})]{% endif %}
{% if slot.youtube %}
<iframe width="{{ site.youtube.width }}" height="{{ site.youtube.height }}" src="https://www.youtube.com/embed/{{ slot.youtube }}" frameborder="0" allowfullscreen></iframe>
{% endif %}
{% endif %}
{% endfor %}
{% endfor %}

