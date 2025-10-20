---
layout: post
title: "Modern JavaScript Features You Should Be Using in 2025"
date: 2025-09-20 14:30:00 +0300
categories: javascript frontend tutorial
---

JavaScript continues to evolve rapidly. Let's explore some modern features that will make your code cleaner, more readable, and more maintainable.

## 1. Optional Chaining (?.)

Say goodbye to nested if statements when accessing deeply nested properties:

{% highlight javascript %}
// Old way
const city = user && user.address && user.address.city;

// Modern way
const city = user?.address?.city;

// Works with arrays too
const firstFriend = user?.friends?.[0]?.name;
{% endhighlight %}

## 2. Nullish Coalescing (??)

Better than `||` for default values:

{% highlight javascript %}
// Problem with ||
const count = 0 || 10; // Returns 10 (not what we want!)

// Solution with ??
const count = 0 ?? 10; // Returns 0 (correct!)

// Only null and undefined are considered nullish
const value = null ?? 'default'; // 'default'
const value2 = '' ?? 'default';  // '' (empty string is not nullish)
{% endhighlight %}

## 3. Array Methods: at()

Access array elements from the end without calculating length:

{% highlight javascript %}
const arr = [1, 2, 3, 4, 5];

// Old way
const last = arr[arr.length - 1];

// Modern way
const last = arr.at(-1); // 5
const secondLast = arr.at(-2); // 4
{% endhighlight %}

## 4. Object.hasOwn()

A better way to check if an object has a property:

{% highlight javascript %}
const obj = { name: 'Emanuel' };

// Old way (can be problematic)
obj.hasOwnProperty('name');

// Modern way (safer)
Object.hasOwn(obj, 'name');
{% endhighlight %}

## 5. Logical Assignment Operators

Combine logical operators with assignment:

{% highlight javascript %}
// OR assignment (||=)
let user = { name: '' };
user.name ||= 'Guest'; // Assigns 'Guest' if name is falsy

// AND assignment (&&=)
let settings = { theme: 'dark' };
settings.theme &&= 'light'; // Only assigns if theme exists

// Nullish assignment (??=)
let config = { timeout: 0 };
config.timeout ??= 5000; // Only assigns if null/undefined
{% endhighlight %}

## 6. Promise.any()

Get the first fulfilled promise:

{% highlight javascript %}
const promises = [
  fetch('/api/endpoint1'),
  fetch('/api/endpoint2'),
  fetch('/api/endpoint3')
];

// Returns the first successful response
const first = await Promise.any(promises);
{% endhighlight %}

## 7. String Methods: replaceAll()

Replace all occurrences without regex:

{% highlight javascript %}
const text = 'Hello world, world!';

// Old way
text.split('world').join('universe');
// or
text.replace(/world/g, 'universe');

// Modern way
text.replaceAll('world', 'universe');
{% endhighlight %}

## 8. Numeric Separators

Make large numbers more readable:

{% highlight javascript %}
// Hard to read
const billion = 1000000000;

// Easy to read
const billion = 1_000_000_000;

// Works with hex, binary, octal too
const hex = 0xFF_FF_FF;
const binary = 0b1010_0001_1000_0101;
{% endhighlight %}

## Bonus: Private Class Fields

True private properties in classes:

{% highlight javascript %}
class User {
  #password; // Private field

  constructor(username, password) {
    this.username = username;
    this.#password = password;
  }

  #hashPassword() {
    // Private method
    return btoa(this.#password);
  }

  authenticate(input) {
    return this.#hashPassword() === btoa(input);
  }
}

const user = new User('emanuel', 'secret');
// user.#password; // SyntaxError!
{% endhighlight %}

## Conclusion

These features are already well-supported in modern browsers and Node.js. Start using them today to write cleaner, more expressive JavaScript code!

Which feature do you find most useful? Let me know on [Twitter](https://twitter.com/EmanuelMazilu)!

## Resources

- [MDN Web Docs](https://developer.mozilla.org)
- [JavaScript.info](https://javascript.info)
- [Can I Use](https://caniuse.com)
