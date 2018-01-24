---
layout: page
title: About
description: 今将下古道，祭酒而别秦
keywords: lei bai, 白磊
comments: true
menu: 关于
permalink: /about/
---

春种一粒粟，秋收万颗子。
四海无闲田，农夫犹饿死。
锄禾日当午，汗滴禾下土。
谁知盘中餐，粒粒皆辛苦。

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
