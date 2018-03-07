# Twitter

Simple wrapper for [alct/noapi](https://github.com/alct/noapi).

## Usage

`\cmal\Twitter` is fully compatible with the original noapi methods. However, it additionally supports the caching of requests, and parsing from an array of params and not just a query string. The cache TTL (in seconds) is passed as a parameter to the class constructor:

```
$tweets = (new Twitter(60))->fromQuery($query);
```

### fromQuery

The `fromQuery` method is the original way of interacting with noapi, defined by the [queryToMeta](https://github.com/alct/noapi/blob/master/src/Twitter.php#L179) method. This is the method called when you do:

```
$data = $noapi->twitter($query);
```

### fromMeta

The `fromMeta` method is when you know precisely what kind of query you'd like to operate, bypassing queryToMeta. For example:

```
$hashtag = 'anarchism';
$args = [
  'type' => 'hashtag',
  'query' => $hashtag,
  'url' => 'https://twitter.com/hashtag/' . $hashtag . '?f=tweets'
];
$tweets = (new Twitter(60))->fromMeta($args);
```

## License

Copyleft [GPLv3](https://github.com/alct/noapi/blob/master/LICENSE)