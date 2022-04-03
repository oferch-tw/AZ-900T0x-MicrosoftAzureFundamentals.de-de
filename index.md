---
title: Online gehostete Anweisungen
permalink: index.html
layout: home
ms.openlocfilehash: c8816b7d9de9c19fbd4c6b3f373d6e4336c6ca5a
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908175"
---
# <a name="content-directory"></a>Inhaltsverzeichnis

Hyperlinks zu den einzelnen exemplarischen Vorgehensweisen. Die Kursleiter können die exemplarische Vorgehensweise als Demonstration oder als Kursteilnehmer-Lab verwenden. 

## <a name="walkthroughs"></a>Exemplarische Vorgehensweisen

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| Modul | Exemplarische Vorgehensweise |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

