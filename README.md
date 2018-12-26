# Advanced CSS

Max Width should be used for desktop first.

Min Width should be used for mobile first.

Media queries do not add more specificity to a selector. That's why order matters.

**Is Mobile-First Right For You?**

Pros

* 100% optimized for mobile
* Reduces websites and apps to the absolute essentials
* Results in smaller, faster and more efficient products
* Prioritizes content over aesthetic design, which may be desirable

Cons

* The desktop version might feel overly empty and simplistic
* More difficult and counter-intuitive to develop
* Less creative freedom, making it more difficult to create distinctive products
* Clients are used to seeing a desktop version of the site as a prototype
* Do your users even use the mobile web? What is the purpose of the website? **Always** consider the purpose of a website.

Always keep both desktop and mobile in mind. Design for both 100% of the time.

## Selecting Our Breakpoints

There are multiple different methods of determining breakpoints.

### The Bad Way

Using individual products to optimize for. Like an iPhone 8 vs the iPhone X. Boo.

### The Good Way

Look at most used device sizes everywhere. Find a service that does this for you.

#### The Perfect Way

Ignore devices altogether and just set design breaks. Look at StatCounter to find the most used screen sizes.

Try to shoot for the following:

* Big Desktops (Optional) - 1920 x 1080
* Desktop Size - 1440 x 900
* Tablet Landscape - 1024 x 768
* Tablet Portrait - 768 x 1024
* Phone Only - 375 x 667

`em`s are best for media queries.

* Big Desktops (Optional) - 1920 x 1080
* Desktop Size - 1440 x 900
* Tablet Landscape - 1024 x 768
* Tablet Portrait - 768 x 1024
* Phone Only - 375 x 667

0-600px:    Phone
600-900px:  Tablet Portrait
900-1200px: Tablet Landscape
1200-1800:  Normal style applies
1800px+:    Big desktop

> NOTE: Order matters with media queries.

