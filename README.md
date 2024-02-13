# obsidian-wordpress

[<img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="BuyMeACoffee" width="100">](https://www.buymeacoffee.com/devbean)

This plugin makes you publish Obsidian documents to WordPress.

There are some introduction videos you can watch:
* [YouTube (Chinese) by 简睿学堂-emisjerry](https://youtu.be/7YECfr_W1WM)
* [Bilibili (Chinese) by 简睿学堂-emisjerry](https://www.bilibili.com/video/BV1FT411A77m/?vd_source=8d3e1ef8cd3aab146af84cfad2f5076f)

## Usages

Set your WordPress URL in settings as well as username if you want.

Put cursor in a MarkDown editor, then use **Publish to WordPress** in
[Command Palette](https://help.obsidian.md/Plugins/Command+palette)
or you could show a button in side in settings.
The document will be published to the WordPress URL that you set.

You could add YAML front matter in front of notes. The plugin will read
meta-data from front matter such as override title or tags.
Also, WordPress post ID and categories will be added to this front matter
if the note published successfully in order to support edit.

For example, you could add as following:

```markdown
---
title: Post title which will override note title, not required
tags:
  - any tag you want
  - not required
---
Note content here.
```

### All properties

A list of all supported front matter properties. All properties are optional, but some properties are automatically inserted after the post was published.

| Property         | Type     | Description                                                                                                                          |
|------------------|----------|--------------------------------------------------------------------------------------------------------------------------------------|
| `profileName`    | string   | Name of the WordPress profile that is used to publish the note. If omitted, the profile must be selected before publishing the post. |
| `postId`         | int      | If defined, the given post will be updated. If omitted, a new post is created.                                                       |
| `title`          | string   | The post title. If omitted, the note-name (filename) is used.                                                                        |
| `slug`           | string   | The post slug, which is part of the URL. If omitted, the title is used to generate the slug.                                         |
| `excerpt`        | string   | The post excerpt. If omitted, WordPress will auto generate the excerpt from the post content.                                        |
| `postType`       | string   | Post type slug. If omitted, the publish modal dialog will ask for the post type.                                                     |

Properties only supported by post type `post`:

| Property         | Type     | Description                                                                              |
|------------------|----------|------------------------------------------------------------------------------------------|
| `postCategories` | int[]    | List of one or more numeric post categories. Always queried by the publish modal dialog. |
| `categories`     | int[]    | Alias for `postCategories` (only used if `postCategories` is not defined).               |
| `postTags`       | string[] | List of WordPress tags to assign to the post -                                           |
| `tags`           | string[] | Alias for `postTags` (only used if `postTags` is not defined).                           |

## Limits

This plugin uses XML-RPC or REST protocol to publish to WordPress.

XML-RPC is enabled by default but some sites may disable it because of
security problems. While some shared hosts might disable XML-RPC by default
which you have no way to enable it. So this won't work if XML-RPC is disabled.

REST API is enabled since WordPress 4.7 by default. Some REST API
need extra actions in order to protect writable APIs.
Traditionally, it is done by installing plugins. WordPress 5.6 was introduced
application passwords to do similar things. So if you are OK with WordPress 5.6,
application passwords is preferred as no plugin in needed.

Read [this page](https://devbean.github.io/obsidian-wordpress) for more information.
