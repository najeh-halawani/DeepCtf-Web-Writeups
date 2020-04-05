# Magic Word

> web

Author: [whitex](https://instagram.com/najeh_halawani)

Hacking is all about thinking outside the box.

Can you figure out this simple puzzle?


## Writeup

This challenge demonstrates a very common bypass that you can find in webapp security.

The gist of the challenge is the following :
- The app takes a word from the user through the `?magic_word=` argument.
- It then replaces all instances of `bumfuzzle` with an empty string
- Finally, it checks if `bumfuzzle` is still there, even after the replacements.

This is the behavior described above :
```
preg_replace("/d33p/", "", "hello") // Returns "hello"
preg_replace("/d33p/", "", "hellod33p") // Returns "hello"
```

Since `d33p` is removed, a simple trick we can use is to embed `d33p` inside `d33p`.

The solution is the following :
```
preg_replace("/d33p/", "", "d33d33pp") // Returns "d33p"
```

You can find the flag by visiting this URL : `http://ip:port/?magic_word=d33d33pp`.
