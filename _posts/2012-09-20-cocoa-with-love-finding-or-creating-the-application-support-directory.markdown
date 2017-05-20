---
author: hummersoftware
comments: true
date: 2012-09-20 01:42:43+00:00
layout: post
link: http://www.hummersoftware.com/blog/cocoa-with-love-finding-or-creating-the-application-support-directory
slug: cocoa-with-love-finding-or-creating-the-application-support-directory
title: 'Cocoa with Love: Finding or creating the application support directory'
wordpress_id: 157
categories:
- Blog
post_format:
- Gallery
---

A simple post this week but one which optimizes a common task: locating the application support directory for the current application, creating it if it doesn't exist. The result makes accessing the current application's support directory a single line and provides a structure for locating and creating folders at other standard locations with similar ease.


#### The Application Support Directory


On the Mac, the correct location to store persistent user-related files for your application is in a directory with the same name as your application in the Application Support directory for the current user.

As an example, if the current user "person" runs an application named "ExampleApp" it would store such files in the following location:






<table cellpadding="0" cellspacing="0" style="width: 575px; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border-color: #ffcc99 !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin-right: 0px !important; margin-bottom: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" border="0" >
<tbody style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >
<tr style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >

<td style="background-color: #fffbf4 !important; border-left-style: solid !important; border-width: 0px 0px 0px 5px !important; border-left-color: #ff8800 !important; padding: 8px 0px !important; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: 572px; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" class="code" >





`/Users/person/Library/``Application` `Support/ExampleApp/`




</td>
</tr>
</tbody>
</table>






On iPhone OS devices, the running application gets its own copy of the Library directory, so you could write files wherever you choose within this. However, I use the same code on both platforms for consistency and there is no real penalty in doing this. For an iPhone OS device then, the path to the application support directory would look like this:






<table cellpadding="0" cellspacing="0" style="width: 672px; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border-color: #ffcc99 !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin-right: 0px !important; margin-bottom: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" border="0" >
<tbody style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >
<tr style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >

<td style="background-color: #fffbf4 !important; border-left-style: solid !important; border-width: 0px 0px 0px 5px !important; border-left-color: #ff8800 !important; padding: 8px 0px !important; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: 669px; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" class="code" >





`/User/Applications/``1``2``3``4``5``6``7``8``-AAAA-BBBB-CCCC-``0``1``2``3``4``5``6``7``8``9``AB/Library/``Application` `Support/ExampleApp/`




</td>
</tr>
</tbody>
</table>






where `12345678-AAAA-BBBB-CCCC-0123456789AB` is whatever UUID has been assigned to your application.


<blockquote>The application support directory is only for user-related persistent _files_. If you want to store user-related preferences, it is generally better to can store them in the [NSUserDefaults](http://developer.apple.com/mac/library/documentation/cocoa/reference/Foundation/Classes/NSUserDefaults_Class/Reference/Reference.html).</blockquote>




#### Getting paths correctly


The correct way to get the path to the Application Support directory is to use the`NSSearchPathForDirectoriesInDomains` function passing `NSApplicationSupportDirectory` for the search path and `NSUserDomainMask` for the domain.

This can be done in one line but on its own, it is only ever part of the solution.

While `NSSearchPathForDirectoriesInDomains` can return a path to the Application Support directory, it does not guarantee that the application support directory exists. For an iPhone OS device, it almost certainly won't exist the first time you run the application.

Further, we need to append the name of the current application to this path and create this application-specific subdirectory if needed.

Finally, we need to handle all of this in a way that is tolerant of errors including failure to create the directory or existence of files where we need a directory to go.

A simple idea — get the application support directory — turns out to be a multi-step operation.


#### Design of the solution


The solution that I use in many of my applications is based around a method with the following declaration:






<table cellpadding="0" cellspacing="0" style="width: 575px; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border-color: #ffcc99 !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin-right: 0px !important; margin-bottom: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" border="0" >
<tbody style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >
<tr style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >

<td style="background-color: #fffbf4 !important; border-left-style: solid !important; border-width: 0px 0px 0px 5px !important; border-left-color: #ff8800 !important; padding: 8px 0px !important; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: 572px; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" class="code" >





`- (``NSString` `*)findOrCreateDirectory:(NSSearchPathDirectory)searchPathDirectory`




`    ``inDomain``:(NSSearchPathDomainMask)domainMask`




`    ``appendPathComponent``:(``NSString` `*)appendComponent`




`    ``error``:(``NSError` `**)errorOut`




</td>
</tr>
</tbody>
</table>






This is a flexible method that can be used for resolving/creating a directory/subdirectory at any standard location searchable by `NSSearchPathForDirectoriesInDomains`.

The first two parameters are the parameters passed to `NSSearchPathForDirectoriesInDomains`, the third parameter is a subpath to append to the result from`NSSearchPathForDirectoriesInDomains` (which we can use to append the current application's name to get our application specific subdirectory). The final parameter is used to return information about any of the three errors that can occur (no path found, file exists at directory location or unable to create directories).

I further supplement this with a convenience method to invoke this with all the appropriate parameters for creating the application support directory:






<table cellpadding="0" cellspacing="0" style="width: 575px; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border-color: #ffcc99 !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin-right: 0px !important; margin-bottom: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" border="0" >
<tbody style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >
<tr style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >

<td style="background-color: #fffbf4 !important; border-left-style: solid !important; border-width: 0px 0px 0px 5px !important; border-left-color: #ff8800 !important; padding: 8px 0px !important; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: 572px; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" class="code" >





`- (``NSString` `*)applicationSupportDirectory`




</td>
</tr>
</tbody>
</table>






On error, this method simply logs any error result using `NSLog`.

In my solution, both of these methods are part of a category on `NSFileManager`. There is no technical requirement that it be a category on `NSFileManager` but these methods do use`NSFileManager` internally and do share the same goals of providing access to directories within the filesystem. Further refinements could also add a URL version based on the NSFileManager method`-URLsForDirectory:inDomains:` which would make the association less arbitrary.


#### Implementation


I've omitted the creation of the error objects for space but otherwise the implementation is as follows:






<table cellpadding="0" cellspacing="0" style="width: 575px; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border-color: #ffcc99 !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin-right: 0px !important; margin-bottom: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" border="0" >
<tbody style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >
<tr style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >

<td style="background-color: #fffbf4 !important; border-left-style: solid !important; border-width: 0px 0px 0px 5px !important; border-left-color: #ff8800 !important; padding: 8px 0px !important; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: 572px; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" class="code" >





`- (``NSString` `*)findOrCreateDirectory:(NSSearchPathDirectory)searchPathDirectory`




`    ``inDomain``:(NSSearchPathDomainMask)domainMask`




`    ``appendPathComponent``:(``NSString` `*)appendComponent`




`    ``error``:(``NSError` `**)errorOut`




`{`




`    ``// Search for the path`




`    ``NSArray* paths = NSSearchPathForDirectoriesInDomains(`




`        ``searchPathDirectory,`




`        ``domainMask,`




`        ``YES``);`




`    ``if` `([paths` `count``] == ``0``)`




`    ``{`




`        ``// *** creation and return of error object omitted for space`




`        ``return` `nil``;`




`    ``}`







`    ``// Normally only need the first path`




`    ``NSString` `*resolvedPath = [paths` `objectAtIndex``:``0``];`




`    `




`    ``if` `(appendComponent)`




`    ``{`




`        ``resolvedPath = [resolvedPath`




`            ``stringByAppendingPathComponent``:appendComponent];`




`    ``}`




`    `




`    ``// Create the path if it doesn't exist`




`    ``NSError` `*error;`




`    ``BOOL` `success = [``self`




`        ``createDirectoryAtPath``:resolvedPath`




`        ``withIntermediateDirectories``:``YES`




`        ``attributes``:nil`




`        ``error``:&error];`




`    ``if` `(!success) `




`    ``{`




`        ``if` `(errorOut)`




`        ``{`




`            ``*errorOut = error;`




`        ``}`




`        ``return` `nil``;`




`    ``}`




`    `




`    ``// If we've made it this far, we have a success`




`    ``if` `(errorOut)`




`    ``{`




`        ``*errorOut =` `nil``;`




`    ``}`




`    ``return` `resolvedPath;`




`}`




</td>
</tr>
</tbody>
</table>






I've noted that we "`Normally only need the first path`". If you pass multiple values ORed together for the domain mask (e.g. `NSUserDomainMask | NSLocalDomainMask`) then this assumption will not be true. If your program needs to handle multiple directories in this way, you'll need to add appropriate handling of multiple results.

Finally, we have the implementation of the `applicationSupportDirectory` method:






<table cellpadding="0" cellspacing="0" style="width: 602px; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border-color: #ffcc99 !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin-right: 0px !important; margin-bottom: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" border="0" >
<tbody style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >
<tr style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >

<td style="background-color: #fffbf4 !important; border-left-style: solid !important; border-width: 0px 0px 0px 5px !important; border-left-color: #ff8800 !important; padding: 8px 0px !important; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: 599px; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" class="code" >





`- (``NSString` `*)applicationSupportDirectory`




`{`




`    ``NSString` `*executableName =`




`        ``[[[``NSBundle` `mainBundle``]` `infoDictionary``]` `objectForKey``:``@"CFBundleExecutable"``];`




`    ``NSError` `*error;`




`    ``NSString` `*result =`




`        ``[``self`




`            ``findOrCreateDirectory``:NSApplicationSupportDirectory`




`            ``inDomain``:NSUserDomainMask`




`            ``appendPathComponent``:executableName`




`            ``error``:&error];`




`    ``if` `(error)`




`    ``{`




`        ``NSLog(``@"Unable to find or create application support directory:\n%@"``, error);`




`    ``}`




`    ``return` `result;`




`}`




</td>
</tr>
</tbody>
</table>






As you can see, it pulls the application name out of the main bundle's `infoDictionary` and uses this to create the Application Support directory.

The end result is that you can get the path to the application support directory with the following line:






<table cellpadding="0" cellspacing="0" style="width: 575px; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border-color: #ffcc99 !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin-right: 0px !important; margin-bottom: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" border="0" >
<tbody style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >
<tr style="border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; border: 0px !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" >

<td style="background-color: #fffbf4 !important; border-left-style: solid !important; border-width: 0px 0px 0px 5px !important; border-left-color: #ff8800 !important; padding: 8px 0px !important; border-top-left-radius: 0px !important; border-top-right-radius: 0px !important; border-bottom-right-radius: 0px !important; border-bottom-left-radius: 0px !important; background-image: none !important; bottom: auto !important; float: none !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; overflow: visible !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: 572px; box-sizing: content-box !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; min-height: inherit !important;" class="code" >





`NSString` `*path = [[``NSFileManager` `defaultManager``]` `applicationSupportDirectory``];`




</td>
</tr>
</tbody>
</table>








#### Conclusion




<blockquote>You can download the complete category here: [NSFileManager_DirectoryLocations.zip](http://projectswithlove.com/projects/NSFileManager_DirectoryLocations.zip) (6kb)</blockquote>


I like it when a task that can be unambiguously described in a simple sentence ("Get the path to the application support directory.") is correspondingly achieved in a single line.

The code presented in this post implements a simple set of steps but since I need to do this in most applications, it is one of my most commonly used categories.

original:[Cocoa with Love: Finding or creating the application support directory](http://cocoawithlove.com/2010/05/finding-or-creating-application-support.html).
