---
image: https://gizn.goatcounter.com/count?p=/RSS-updated-zotero-integration-template
type: blog-post
layout: post
title: "Updated Zotero Integration Template"
category: til
tags: zotero obsidian zoterointegration template
render_with_liquid: false
---
After my [blogpost](http://gizn.org/notes/2023/01/20/how-to-connect-zotero-with-obsidian.html) about how to connect Zotero with Obsidian, I have had readers reach out to me with suggestions on improvements to my template. Thank you for this. The template is available in an updated form on my [github](https://github.com/georgnaver/Templates/blob/main/ZoteroNote.md), but here is a quick explanation.

### 1.

The template now imports selected areas. This allow you to make a selection in Zotero and import that as an image to your note. This is great for figures.

The following chunk...

{% raw %}
    {% for annotation in annotations %}
    {% if annotation.annotatedText %}
    > <mark style="background-color: {{annotation.color}};color: black">Highlight</mark> 
    > {{annotation.annotatedText}}
    > [Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}})
    {% endif %}
    {% if annotation.comment %}
    > <mark style="background-color: {{annotation.color}};color: black">Comment</mark>
    > {{annotation.comment}}
    > [Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}})
    {% endfor %}
{% endraw %}

...has been replaced with (or rather have gotten the addition of) this:

{% raw %}
    {% for annotation in annotations %}
    {% if annotation.annotatedText %}
    > <mark style="background-color: {{annotation.color}};color: black">Highlight</mark> 
    > {{annotation.annotatedText}}
    > [Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}})
    {% endif %}
    {% if annotation.comment %}
    > <mark style="background-color: {{annotation.color}};color: black">Comment</mark>
    > {{annotation.comment}}
    > [Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}})
    {% endif %}
    {% if annotation.imageRelativePath %}
    ![[{{annotation.imageRelativePath}}]]
    {% endif %}
    {% endfor %}
{% endraw %}

### 2.

In the previous version, the "take aways", "related" and "tags" sections were overwritten everytime you reimported. This is fixed by adding {% persist %}:

{% raw %}
    {% persist "notes" %}
    ### Take-aways
    
    -  
    
    ### Related
    
    - 
    
    ### Tags 
    
    #wip #literature-note #medicin #zotero 
    {% endpersist %}
{% endraw %}

### 3.

The template now includes a table with basic information and links associated with the article.

{% raw %}
    | |
    |------------ | ------------|
    | Title | {{title}} |
    | Authors | {{authors}} |
    | Publication | {{publicationTitle}} |
    | Zotero link | {{pdfZoteroLink}} |
    | Web link | {{url}} |
{% endraw %}

### Comment

Disagree with something? Anything you want to discuss? Please comment on [twitter](https://twitter.com/giznse/status/1618935063735058439) or [mastodon](https://mstdn.science/@gizn/109760964411701464).
