---
title: オンラインでホスティングされている手順
permalink: index.html
layout: home
---

# <a name="content-directory"></a>コンテンツ ディレクトリ

各チュートリアルへのハイパーリンク。 講師は、このチュートリアルをデモンストレーションまたは受講者用ラボとして使用できます。 

## <a name="walkthroughs"></a>チュートリアル

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| モジュール | チュートリアル |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

