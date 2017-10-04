# Markdown

Markdownとは、マークアップ言語のひとつ。  
githubで使われ、はてなブログでもMarkdownで記事が書けるようになった。  
あとは技術系の共有サービスQiitaでも使われており、最近なじみ深いものになった（主観）。  

## 書き方

Markdownの例について書く


### 表の作成

```
| col1 | col2 | col3 | col4 |
|:----:|:----:|:-----|-----:|
|row1  |a     |a     |a     |
|row2  |a     |a     |a     |
|row3  |a     |a     |a     |
```

| col1 | col2 | col3 | col4 |
|:----:|:----:|:-----|-----:|
|row1  |a     |a     |a     |
|row2  |a     |a     |a     |
|row3  |a     |a     |a     |


!!! note
    表作成はSphinxと比べてだいぶ楽。

### 画像の挿入

```
![ham](img/ham.png)
```

![ham](img/ham.png)

!!! warning
    画像の大きさを変えたいときはHTMLタグを使う


<img src="img/ham.png" alt="ham" title="ham">



```
backports-abc==0.5
backports.ssl-match-hostname==3.5.0.1
certifi==2017.7.27.1
click==6.7
Jinja2==2.9.6
livereload==2.5.1
Markdown==2.6.9
MarkupSafe==1.0
mkdocs==0.16.3
mkdocs-material==1.10.1
Pygments==2.2.0
pymdown-extensions==4.0
PyYAML==3.12
singledispatch==3.4.0.3
six==1.11.0
tornado==4.5.2
```
