---
title: Online gehostete Anweisungen
permalink: index.html
layout: home
---

# <a name="content-directory"></a>Inhaltsverzeichnis

Hyperlinks to each of the walkthroughs. Instructors may choose to use the walkthrough as a demonstration or a student lab. 

## <a name="walkthroughs"></a>Exemplarische Vorgehensweisen

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| Modul | Exemplarische Vorgehensweise |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

