---
layout: post
title:  "Infinite loop on SwiftUI property observers"
date:   2020-05-24 17:00:00 -03:00
categories: swiftui
---

It appears the latest Xcode build 11E608c (20-May-2020) introduced a new behavior (or a bug) for property observers (`didSet`, `willSet`). Before the update, I had no problem in my project in have a function for a `didSet` observer of an object that updated its own value.

{% highlight Swift %}
...
@published var stock = Stock() {
    didSet {
        tickerChecker()
    }
}
...
func tickerChecker() {
    stock.ticker = stock.ticker.uppercased()
}
{% endhighlight %}

However, after a new build of my project, I got a surprisingly infinite loop after setting the first character of `stock.ticker`. After some debugging here and there, I wondered if if when `tickerChecker` set a new value for the property field, it could trigger a new `didSet` call. So, trying to avoid the chain of calls, I added a simple verification if the value is the same:

{% highlight Swift %}
@published var stock = Stock() {
    didSet {
        tickerChecker(oldValue)
    }
}
...
func tickerChecker(_ oldValue: Stock) {
    if stock.ticker == oldValue.ticker {
        return
    }
    stock.ticker = stock.ticker.uppercased()
}
{% endhighlight %}

And the result was that the infinite loop was fixed indeed. Still there are more than one call to `tickerChecker`, but my guess there is that they come from other field changes that happen inside the function. Also, goes without saying that the parameter `oldValue` is available as a default parameter, same happens for parameter `newValue` on `willSet` observer.

I know that a Xcode/iOS update usually comes with surprises. I'm not sure if it is a bug or a bugfix (and my code had a bug before). Anyhow, I gonna call this solved for now.