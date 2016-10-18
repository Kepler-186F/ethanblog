---
layout: post
title: "GUICE All in one"
date: 2016-06-29 23:23:00 -0800
comments: true
categories:
---
"Not enough mana." --Diablo3

"You are right....Every project you touched turn into shit" -- Nathan Drake, Uncharted 3


Recently I need to work on some core java projects like Argus (https://github.com/SalesforceEng/Argus). It uses GUICE, as a classic DI framework. After searched around, there is no good tutorial for beginer to quickly jump in---all materials seem to be incomplete in some way, include the one provided by google/guice. So I decide to make one myself. Thanks to #rajsarkapally-sfdc helped me.


So this is basic idea
{% img /images/img/9-idea.jpg %}



Now let's use one example from Otaku's blog

The more I use dependency injection (DI) in my code, the more it alters the way I see both my design and implementation. Injection is so convenient and powerful that you end up wanting to make sure you use it as often as you can. And as it turns out, you can use it in many, many places.
Let’s cover briefly the most obvious scenarios where DI, and more specifically, Guice, are a good fit: objects created either at class loading time or very early in your application. These two aspects are covered by either direct injection or by providers, which allow you to start building some of your object graph before you can inject more objects. I won’t go too much in details about these two use cases since they are explained in pretty much any Guice tutorial you can find on the net.

Once the injector has created your graph of objects, you are pretty much back to normal and instantiating your “runtime objects” (the objects you create during the life time of your application) the normal way, most likely with “new” or factories. However, you will quickly start noticing that you need some runtime information to create these objects, other parts of them could be injected.

Let’s take the following example: we have a GeoService interface that provides various geolocation functions, such as telling you location if given a person's name:

```
package com.salesforce.service;

public class GeoService implements GeoServiceInterface{
	public boolean judge(String Name){
		System.out.println("juding...");
		return Name.isEmpty()?false:true;
	}
}

```
Then you have a Person class which uses this service and also needs a name and an address to be instantiated:

```
package com.salesforce.kepler;
import com.google.inject.Inject;
import com.google.inject.assistedinject.Assisted;
import com.salesforce.service.GeoServiceInterface;

public class Person implements PersonInterface {
	private String Name;
	private GeoServiceInterface gs;
	
	private Person(String Name, GeoServiceInterface gs){
		this.Name=Name;
		this.gs=gs;
	}
	public boolean getLocationByName(){
		return gs.judge(Name);
	}
}
```
Something odd should jump at you right away with this class: while name and address are part of the identity of a Person object, the presence of the GeoService instance in it feels wrong. The service is a singleton that is created on start up, so a perfect candidate to be injected, but how can I achieve the creation of a Person object when some of its information is supplied by Guice and the other part by myself?
Guice gives you a very elegant and flexible way to implement this scenario with “assisted injection”. (Quote ended here)

{% img /images/img/9-GUICE.jpg %}

Above are basic. To use provider.

{% img /images/img/9-Provider.jpg %}

So in the end, this is what you need.

{% img /images/img/9-Automatic.jpg %}


Links
http://stackoverflow.com/questions/9237996/pass-parameter-to-constructor-with-guice
https://github.com/google/guice/wiki/ProviderBindings
http://beust.com/weblog/2012/08/21/advanced-dependency-injection-with-guice/