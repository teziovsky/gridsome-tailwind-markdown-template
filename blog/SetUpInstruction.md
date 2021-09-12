---
title: Set Up instruction
published: true
description: This is a guide for everything to set up in the repository to make this place your own! Regardless of if you're new to Gridsome or just looking for the checklist of things to update when you clone this project, this post is for you!
tags: setup, guide, gridsome
date_published: "2021-09-12"
og_image: ./og/ogImage.png
---

## Files to change:

### Set your Site Name

```js{codeTitle: "gridsome.config.js"}
module.exports = {
  siteName: 'WriteYourNameHere',
  siteUrl: 'https://WriteYourDomainHere.com', //Used by the sitemap plugin to make your site searchable on Google.
  //...
};
```

### Set the Base URL for calculating Canonical URLs
> This is important because it will dictate what the canonical url is for your blog posts!

```js{codeTitle: "gridsome.server.js"}
module.exports = function(api) {
  api.loadSource(async (store) => {
    store.addMetadata("baseURL", "https://WriteYourDomainHere.com");
  });
  //...
};
```

### Reroute from my Twitter profile to yours for shared posts

```vue{codeTitle: "/src/templates/Post.vue"}
<script>
        {
          name: "twitter:creator",
          content: "@YourTwitterName",
        },
        {
          name: "twitter:site",
          content: "@YourTwitterName",
        },
</script>
```

### Update the Site Favicon

```js{codeTitle: "/src/favicon.png"}
// Replace this with an image to use as the favicon for your site!
```

> 🚨 If you use a file name other than favicon.png you need to update gridsome.config.js with the icon property: https://gridsome.org/docs/config/#icon

## Blog Posts

### Adding New Blog Posts

To add new blog posts, create `postTitle.md` files in the `/blog/` root level folder.

The first thing in each of your blog post markdown file should be the following information which is required for the site to build:

```md{codeTitle: "/blog/yourMarkdownFile.md"}
---
title: Set Up This Blog
published: true
description: This is a guide for everything to set up in the repository to make this place your own!
date_published: "2021-06-24"
og_image: ./path/to/og/image.png
---
```

> The `date_published` is in YYYY-MM-DD format so that the blog list on the home page can be sorted with the newest items at the top of the page.

> Note that the title of the post is automatically added as the h1 tag on the post page and all markdown content should start at the `##heading 2` level to prevent accessibility issues.

> `og_image` is the image that will show when the link is shared in places like Facebook or Twitter