---
layout: post
category : umbraco
title : Razor Components - First Release
date : 2012-06-19 20:00:00
tags : [umbraco, razor, opensource]
---
{% include JB/setup %}


Razor Components has been released on [_Our_](http://our.umbraco.org/projects/website-utilities/razor-components) 
and [NuGet](https://nuget.org/packages/Tocsoft.Umbraco.RazorComponents).
Also the source is available on [github](https://github.com/tocsoft/Umbraco-Razor-Components). 

<!--break-->

##What does it do?
Razor Components is a set of Extension methods for the Library property on Umbraco Razor macros.

##Compatibility
This library is compatible with with both normal Umbraco Razor macros and 
[UmbraMVCo](http://our.umbraco.org/projects/website-utilities/umbramvco) razor views.

##Usage

To use the library, after you have installed the package ether from the package on _Our_ or from NuGet you 
will have to add `@using Tocosft.Umbraco.RazorComponents` to the top of your scripts then you can use the 
Extensions.

There are 2 main extensions 

Number one is `RenderMacro` which has to modes alias mode and file include mode.

To render a macro using an alias you use `@Library.RenderMacro("MacroAlias", new { Property1 = "value", Prop2= "value2"})` 
this will render a named macro from the back office Alternativly if you pass in a virtual Url pointing to a macroScript
we render the razor file as a macro(for compatibility) an example would be 
`@Library.RenderMacro("~/macroScripts/scriptFile.cshtml", new { Property1 = "value", Prop2= "value2"})`.


The second part is the `ImageUrl`/`ImageUrls` calls, this is used to retrieve crop Urls form media 
picker properties(also supports DAMP and embedded media xml). To return the urls use
`@Library.ImageUrl("imagePropertyAlias", "aliasOfCropPropertyOnMediaNode", "cropName")`. If there are
no crops findable using the supplied crop/property then we fallback to using the umbracoFile property
so if possible we always return an image url.


###Disclaimer
It works on my machine, I have been using a variant of this Helper in a few sites so its should be 
relatively stable but I promise nothing yet.
