JazzyViewPager
==============

Original repo: https://github.com/jfeinstein10/JazzyViewPager

This project was not maintained and was still running in old eclipse with out any gradle support, so I decided to make it gradle compatible.

How it looks like in the end? 
=============================

<img src="https://cloud.githubusercontent.com/assets/3941245/23747036/3f75e6e2-04e4-11e7-8c71-d444063da20b.png" width="200">
<img src="https://cloud.githubusercontent.com/assets/3941245/23747038/3f8346ac-04e4-11e7-86f7-ed318df49fb0.png" width="200">
<img src="https://cloud.githubusercontent.com/assets/3941245/23747037/3f82dd8e-04e4-11e7-8003-54ddba8c67ca.png" width="200">
<img src="https://cloud.githubusercontent.com/assets/3941245/23747039/3fc7b40e-04e4-11e7-9c86-c6afb86f9f77.png" width="200">

This is one from my own project: 
=======================
<img src="https://cloud.githubusercontent.com/assets/3941245/23747040/3fdbdc4a-04e4-11e7-96b4-feacf035bd6e.png" width="200">

How to use? 
===========

Step 1. Add it in your root build.gradle at the end of repositories:
-------------------------------------
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
Step 2. Add the dependency
-------------------------------------
	dependencies {
	        compile 'com.github.hishamMuneer:JazzyViewPager:1.0.0'
	}

Step 3. Code
-------------------------------------
You can select your animation by calling
```java
private JazzyViewPager mJazzy;
/* ... */
mJazzy.setTransitionEffect(TransitionEffect.*);
```

Step 4. Modifying your `PagerAdapter`
-------------------------------------
Due to the limitations of the `ViewPager` class (which `JazzyViewPager` is built upon) in order to get the animations to work correctly 
for more than 3 Views, you'll have to add the following to the `instantiateItem` method of your `PagerAdapter`.
```java
private JazzyViewPager mJazzy;
/* ... */
@Override
public Object instantiateItem(ViewGroup container, final int position) {
    Object obj = super.instantiateItem(container, position);
	mJazzy.setObjectForPosition(obj, position);
	return obj;
}
```
Once your `Object` is registered with the `JazzyViewPager`, you're good to go!

Jeremy Feinstein
================

An easy to use ViewPager that adds an awesome set of custom swiping animations. 
Just change your ViewPagers to JazzyViewPagers and you're good to go!

If you're looking at the name of the library and thinking "... so what does jazz have to do with it?"
I'd like to direct you to the following definition that I found in a dictionary:

```
jazz someone or something up:
	to make someone or something more exciting or sexy;
	to make someone or something appeal more to contemporary tastes.
```

**The aim of this library is to do exactly this: jazz up the normal, everyday `ViewPager`**
	
The example app will get better, but this is just to get something in your hands quickly :D!
This project was inspired by CyanogenMod's Trebuchet launcher.

Animations Available
-------
The `JazzyViewPager`'s animations are encapsulated in `TransitionEffect`. I'll be adding more, but if you can think of anything 
in particular, let me know by filing an "Enhancement" in the Issues section.
```java
public enum TransitionEffect {
    	Standard,
		Tablet,
		CubeIn,
		CubeOut,
		Flip,
		Stack,
		ZoomIn,
		ZoomOut,
		RotateUp,
		RotateDown,
		Accordion
	}
```

License
-------

    Copyright 2017 Hisham Muneer
    
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
    
    http://www.apache.org/licenses/LICENSE-2.0
    
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
