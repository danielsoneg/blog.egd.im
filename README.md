Site powering [blog.egd.im](https://blog.egd.im)

Powered by [Pelican](http://getpelican.com)

Usage
=====
Install requirements:
`pip install -r requirements`

Create Secrets:
```
SEC_PRODUCTION_SERVER = '$USER@$SERVER'
SEC_PRODUCTION_PATH = '$SERVING_PATH'
```

Write Stuff: ```vim content/my_post.md```

Use Invoke: ```$ invoke publish```

FAQ
===
1. What am I supposed to do with this?

Nothing, it's the code that builds my blog

2. So why is it here?

So it's persisted somewhere other than my laptop

3. Well, why not make it private, then?

Because it's more fun to work in public, and maybe it'll be useful for someone.

4. You misspelled a word/misused a tag/screwed up your CSS

Neat! Submit a PR.
