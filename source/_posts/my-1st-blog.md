---
title: my 1st blog
date: 2021-11-03 00:00:45
categories:
- [编程, 博客]
- [新闻, 娱乐, 八卦]
tags:
- coding
- python
---

## My first blog

{% codeblock HTML lang:html mark:1-3,5 %}
<h1>Awesome People</h1>
<ul>
  <li class="first">Paul</li>
  <li>Jim</li>
  <li>Jane</li>
</ul>
<p>hello world!</p>
{% endcodeblock %}

```html
<h1>Awesome People</h1>
<ul>
  <li class="first">Paul</li>
  <li>Jim</li>
  <li>Jane</li>
</ul>
<p>hello world!</p>
```

### Translate HTML to Markdown with Python

```python
import html2text as ht

to_remove: list[str] = []
to_remove.append(
    '<img class="profile_avatar" id="js_profile_qrcode_img" src="" alt="">'
)
to_remove.append(
    '<div id="js_tags_preview_toast" class="article-tag__error-tips" style="display: none;">预览时标签不可点</div>'
)

text_maker = ht.HTML2Text()
# text_maker.ignore_links = True
text_maker.bypass_tables = False

fname = "1"
# 读取html格式文件
with open(f"html/{fname}.html", "r", encoding="UTF-8") as f:
    htmlpage = f.read()
# 处理html格式文件中的内容
text = text_maker.handle(htmlpage)
md = text.split("#")  # split post content
# 写入处理后的内容
with open(f"md/{fname}.md", "w") as f:
    f.write(md[1])
```