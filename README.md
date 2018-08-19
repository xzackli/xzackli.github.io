[![Build Status](https://travis-ci.org/xzackli/xzackli.github.io.svg?branch=master)]()

# Cheat sheet

## Dependency
* [Hugo](https://gohugo.io/)

## Creating a new post
`cd` into the project root folder and run

```
hugo new posts/your-post-title.mmark
```

Hugo will create a file in `content/posts` with the appropriate front matter (title and date).

Make sure to use the `.mmark` extension to force Hugo to use the [mmark](https://github.com/miekg/mmark) processor instead of the default. `.md` *works* but will break if you try to use latex. More info [here](https://gohugo.io/content-management/formats/#issues-with-markdown).

## Serving locally
```
hugo serve
```

## Images
Put images inside `static/images/`. Folders work the way you expect.

Reference them this way inside of your posts (note the lack of `static` in the URL).

```md
{{< figure src="/images/lin_large_l_p21.png" title="Large l Planck Figure 21 Linear Y" >}}
```

## Descriptions
Add a description to your post inside the front matter:
```yaml
description: "Did the space thing and wrote a paper"
```

## Long code blocks
Use my custom shortcode to add a button to expand the code block. See it in action [here](https://blog.jse.li/posts/marveloptics-malware/).

    {{% expander %}}
    ```python
    def do_stuff(s):
        print(s)
    ```
    {{% /expander %}}

## Drafts
To work on and commit a post that you don't want to show up on the site yet, add the following to the front matter:

```yaml
draft: true
```
