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