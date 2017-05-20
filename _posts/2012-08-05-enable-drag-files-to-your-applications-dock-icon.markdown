---
author: hummersoftware
comments: true
date: 2012-08-05 03:11:24+00:00
layout: post
link: http://www.hummersoftware.com/blog/enable-drag-files-to-your-applications-dock-icon
slug: enable-drag-files-to-your-applications-dock-icon
title: Enable drag files to your application's dock icon
wordpress_id: 30
categories:
- Blog
post_format:
- Gallery
---

You can enable drag files to your application's dock icon by edit your application's plist:

    
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
    	<key>CFBundleDevelopmentRegion</key>
    	<string>English</string>
    	<key><span style="color: #ff0000;">CFBundleDocumentTypes</span></key>
    	<array>
    		<dict>
    			<key>CFBundleTypeExtensions</key>
    			<array>
    				<string>sdat</string>
    			</array>
    			<key>CFBundleTypeIconFile</key>
    			<string>@ICON@</string>
    			<key>CFBundleTypeMIMETypes</key>
    			<array>
    				<string>text/plain</string>
    				<string>text/xml</string>
                                    <string>text/xhtml</string>
    			</array>
    			<key>CFBundleTypeName</key>
    			<string>Text File</string>
    			<key>CFBundleTypeRole</key>
    			<string>@EXECUTABLE@</string>
    		        <key>LSIsAppleDefaultForType</key>
    			<true/>
    		</dict>
    	</array>
    	<key>CFBundleExecutable</key>
    	<string>Qedit</string>
    	<key>CFBundleGetInfoString</key>
    	<string>@EXECUTABLE@ Your name</string>
    	<key>CFBundleIconFile</key>
    	<string>mac_QeditIcon.icns</string>
    	<key>CFBundleIdentifier</key>
    	<string>your qsetting domain</string>
    	<key>CFBundleName</key>
    	<string>@EXECUTABLE@</string>
    	<key>CFBundlePackageType</key>
    	<string>APPL</string>
    	<key>CFBundleShortVersionString</key>
    	<string>1.4</string>
    	<key>CFBundleSignature</key>
    	<string>!Rch</string>
    </dict>
    </plist>


Use the CFBundleDocumentTypes key to configure your drag in file types, so it's so easy!
