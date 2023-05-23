# "Create your own url-shortener"-Kata

## Summary
Within this kata you should create a class `UrlShortener` which accepts an url to shorten `shorten(long: String)` and returns an shortened link.

Example from bit.ly:

|long url               |shortened url           |
|-----------------------|------------------------|
| https://www.google.de | https://bit.ly/1gjR8PE |
| https://www.denic.de  | https://bit.ly/2jNPT1Z |  


## Hints

- Each main-point or sub-point below should create at least one new test or an addition to an existing test
- Follow them line by line
- Please do not forget to refactor!
- Do not implement any other **public** methods than listed above and create them as you need them!
    - `size(): Int`
    - `shorten(long : String): String`
    - `unshorten(short : String): String`
    - `countUnshortenings(url : String): Int`
    - `stats(url : String): String`
- Parameter names:
    - `long` a non shortened url, i.e. `https://www.volkswagen.de`
    - `short` a shortened url, i.e. `https://sho.rt/123`
    - `url` a non shortened or shortened url

## Rules

- A newly created UrlShortener is empty:
    - The size is empty `size(): Int` returns 0
- There is a method which can be called to shorten an url `shorten(long: String): String`:
    - The size increases by 1
    - The shortened urls should start with https://sho.rt
    - The shortened url should follow the format https://sho.rt/ID, the format of the id is free to choose.
      Hint: think about using an ascending number.
- The full url behind a shortened url can be retrieved through `unshorten(String short) : String`
    - given the shortUrl it will return the long url
- The url shortener should handle multiple urls
- The url shortener should handle 1000 urls
- An url that has the same domain https://sho.rt can not be shortened (again) (throws Exception)
- if given an unknown shortUrl to `unshorten(short : String)` it will throw an Exception
- If the same url should be shortened more than once it will return the same short url. It should fail with Exception.
- The id should be of consist of 3 digits with [0-9]. Example: 001, 345, ...
- The count of _unshortenings_ `countUnshortenings(shortUrl: String) : Int` of an url should be counted:
    - When a short url is created the count is 0
    - When a short url is unshortend the count increases by one
    - When the short url given does not exist throw an Exception
- The id should be random and independent of the given url. (number between `0` and `999`)
  Hint: two instances of the UrlShortener should return different ids for same url.
- The method `countUnshortenings(shortUrl: String) : Int` should be changed to
  `countUnshortenings(url) : Int` so that it does not matter if the short url or long url were given.
  Hint: urls starting with https://sho.rt/ can not be shortened:
    - unknown long urls should throw a RuntimeException
- The method `shorten(url: String): String` should only accept urls starting with `https://`. If other urls are given, it should throw an Exception.
- Create a statistics method String `stats(url: String): String` which returns a string like:
  `Short URL: https://sho.rt/123, long URL: https://www.google.de, visits: 12`:
    - short/long url can be given
    - given an unknown url it throws an Exception

## Bonus

- replace the number with a random generated id from the chars [0-9,a-z,A-Z] with a fixed length of 7