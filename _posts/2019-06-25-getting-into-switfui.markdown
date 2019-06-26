---
layout: post
title:  "Getting into SwiftUI"
date:   2019-06-26 08:00:00 -03:00
categories: swiftui
---

Being inserted into Apple's environment for a while, I always felt kinda obligated to start developing for either iOS or MacOS. Though there was one problem: Objective-C. The language and XCode seemed to have a high learning curve, and as I was still on college and more focused on my research, I never dig further on it. Then, in 2014 Swift was announced and the future looked brighter.

![Craig]({{site.baseurl}}/assets/swift-federighi.jpg)

As bright as it looked, it didn't solve much of the issues -- for me the initial high dependency on storyboards was not much appetizing. Some iterations of the Swift language passed by until we were announced in this year WWDC and improved language (?) to build interfaces, SwiftUI. It was very attractive to me, so attractive that I became determined in diving into it.

## Diving

So I started right away by getting XCode 13 Beta 1. It works on MacOS Mojave, though the full support will come just with MacOS Catalina and iOS 13. The most notable missing feature is the canvas, where you will be able to see a preview of the current view in _realtime_. For now, just need to have the simulator on and keep building to see things alive. 

Building a very simple app that shows a static caption when the button is clicked, it would look like the code below

{% highlight Swift %}
import SwiftUI

struct ContentView : View {
    @State var showT: String = ""
    
    var body: some View {
        VStack {
            Text("Getting into SwiftUI")
                .font(.title)
            
            Text("\(showT)")
                .font(.caption)
                .color(.gray)
            
            Spacer()
            
            Button(action: {
                self.showT = "Button has been clicked"
            }) {
                Text("Click here")
            }
                .foregroundColor(.red)
        }
    }
}
{% endhighlight %}

Very simple and straightforward! Results in the following view

![mockup]({{site.baseurl}}/assets/mockup-clicked.png){:.centered-img}

### Bugs

So far there are a couple of bugs, what is expected for the very first beta version. The one that annoys me more is the confusing compiling errors. Sometimes simples problems result in a very strange and unhelpful error, let's see the error below

![error]({{site.baseurl}}/assets/error-bug.png){:.centered-img}

I just removed the `@State` statement from line 12 and, instead of showing an error on line 26, where the missing statement will cause the problem, a crazy error appears on line 20. This happens by either auto-checker or after building.

### Moving forward

I've completed the official tutorial <https://developer.apple.com/tutorials/swiftui/tutorials> on SwiftUI already, learning a lot of how Apple engineering intend us doing the application and also how to integrating with existing framework. My goal for now is to continue working if the beta versions of XCode, trying to have an app - I already have the idea - by iOS 13 official launch later this year. Let's see.