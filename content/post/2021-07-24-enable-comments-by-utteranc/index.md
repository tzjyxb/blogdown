---
title: Enable comments by utteranc
author: Bin Xu
date: '2021-07-24'
slug: enable-comments-by-utteranc
categories:
  - blogdown
tags: []
---

本文主要参考[Add comments to your Hugo-Academic blog in 10 minutes, using Utteranc.es](https://mscipio.github.io/post/utterances-comment-engine/)

### 启用评论功能的步骤（基于`PaperMod`主题）

1. 在blog所在的repo[安装utteranc](https://github.com/apps/utterances)
2. 在[utterances web-app](https://utteranc.es/)进行参数配置，我的配置参数如下：

```html
<script src="https://utteranc.es/client.js"
        repo="tzjyxb/blogdown"
        issue-term="pathname"
        label="blogComment"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>
```

3. 配置***config.yaml***文件，在**params**中添加如下参数：

``` yaml
    comments:
        utteranc:
            enable: true
            repo: "tzjyxb/blogdown"
            label: "blogComment"
            issueTerm: "pathname"
            theme: "github-light"
```

4. 修改***themes/hugo-PaperMod/layouts/partials***中的***comments.html***文件如下（默认为所有的文章开启评论）：

``` html
{{- if .Site.Params.comments.utteranc.enable }}
<script src="https://utteranc.es/client.js"
        repo="{{ .Site.Params.comments.utteranc.repo }}"
        label="{{ .Site.Params.comments.utteranc.label }}"
        issue-term="{{ .Site.Params.comments.utteranc.issueTerm }}"
        theme="{{ .Site.Params.comments.utteranc.theme }}"
        crossorigin="anonymous"
        async>
</script>
{{- end }}
```

此处的格式和部分参数参考自***themes/hugo-PaperMod/layouts/_default/single.html***

``` html
  {{- if (.Param "comments") }}
  {{- partial "comments.html" . }}
  {{- end }}
```

因为在这个文件中，需要`.Param "comments" == true`才可以开启评论，因此在修***config.yaml***文件时，需要在**params**中添加**comments**参数

或者`.Param "comments"`可以修改为`.Param "utteranc"`，这样就不需要多添加`comments`层级

5. `commit` and `push` your blog.