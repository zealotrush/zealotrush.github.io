---
layout: post
title: "Rime 输入法五笔86配置"
date: 2014-11-12 20:53:49
category: essay
excerpt: <p></p>
---

## 添加五笔

打开 `default.custom.yaml` 文件（若不存在则新建，下同），添加如下代码。

```yaml
patch:
  schema_list:
    - schema: wubi86
```

「重新部署」后生效。

## 定制外观

### 候选项个数

打开 `default.custom.yaml` 文件，添加如下代码。

```yaml
patch:
  menu:
    page_size: 3
```

「重新部署」后生效。

### 字号及横排

打开 `weasel.custom.yaml` 文件（如使用 OSX 系统，文件名为 `squirrel.custom.yaml`，下同），添加如下代码。

```yaml
patch:
  style:
    font_point: 16
    horizontal: true
```

「重新部署」后生效。

## 造词

### 短词

按照普通方式，逐步输入该词，然后再按五笔词组打法输入，新词应该就已经出现在候选窗，并且后面有「八卦符号」（☯），表示它是新造词。选择一次之后，就成为固定词组。

### 长词

特别长的词组，可能不会自动记忆。可以通过分号（;）分隔符，一次性输入长词组，上屏后会记忆。例如，想造词「衣带渐宽终不悔」，可输入：

    ye;gkp;il;pa;xtu;i;ntx

然后，再次输入 `ygin` 时，就已出现自动造词。选中一次后成为固定词组。

## 输入特殊符号

打开 `wubi86.schema.yaml` 文件，找到如下片段：

```yaml
punctuator:
  import_preset: default
```

将 `default` 改为 `symbols`，结果如下：

```yaml
punctuator:
  import_preset: symbols
```

在文件末尾，找到如下片段：

```yaml
recognizer:
  import_preset: default
  patterns:
    reverse_lookup: "^z[a-z]*'?$"
```

在最下面添加一行，使之最终成为：

```yaml
recognizer:
  import_preset: default
  patterns:
    reverse_lookup: "^z[a-z]*'?$"
    punct: "^/[a-z]+$"     # <-- Add this line
```

「重新部署」后生效。

## 用户词典

在用户目录下添加 `custom_phrase.txt` 文件，编码格式需选择 **UTF-8**. 输入类似以下内容：

```txt
zealotrush@gmail.com    mail   10
beibeiwang@msn.com  mail    9
```

注意，必须用 Tab 分隔，不能用空格。

再打开 `wubi86.schema.yaml` 文件，找到如下片段，并按提示添加新行：

```yaml
translators:
  - punct_translator
  - reverse_lookup_translator
  - table_translator@custom_phrase  # <-- Add this line
  - table_translator
```

再在文件末尾添加一段新的代码，如下：

```yaml
custom_phrase:
  dictionary: ""
  user_dict: custom_phrase
  db_class: stabledb
  enable_completion: false
  enable_sentence: false
  initial_quality: 1
```

「重新部署」后生效。

## 关闭编码提示

在文件 `wubi86.schema.yaml` 中，找到如下片段，并按提示添加新行：

```yaml
translator:
  dictionary: wubi86
  enable_charset_filter: true
  enable_sentence: true
  enable_encoder: true
  enable_completion: false      # <-- Add this line
  encode_commit_history: true
  max_phrase_length: 4
  disable_user_dict_for_patterns:
    - "^z.*$"
```

「重新部署」后生效。
