# Derefind &mdash; Refind Bookmark Converter

This JavaScript application processes your [Refind](https://refind.com) export file on your computer. It creates an output file that can be imported to [Shaari](https://github.com/shaarli/Shaarli/blob/master/README.md) and [Diigo](https://www.diigo.com/) with the tags preserved. It processes files locally, not on any server.

 ## How To Use It 

Use it on [this demo server](http://partialsolution.ca/derefind/) or simply [download the latest source code ZIP from GitHub open the `index.html` file on your computer](https://github.com/ShawnPConroy/Derefind/releases).

## Requirements

Tested on Chrome 62. I expect it will work on the major browsers released in 2017.

## Refind Export Problem

When Refind exports your bookmarks, it does it per tag. This means if you tag a bookmark with multiple tags, it will appear multiple times. This caused Shaari to report that some items were skipped or overwritten. (I am unsure if this means tags were lost.) When I tried to import it to Diigo, it was rejected (all links skipped).

The standard tag export as used by Del.icio.us is to list all link sequentially and have each link (HTML `a` tag) have a parameter listing tags. Refind instead uses the Netscape bookmark folder/category method of listing the tag after an HTML `h3` tag. It also has other differences such as closing tags Del.icio.us doesn't close.

## Solution

This script loads the Refind file, pulls out all elements sequentially, and iterates through them. Whenever it finds a link (`a`) it saves it, with the last tag (`h3`) it came across. When it find a duplicate link, it adds the new tag.

Finally, it generates the output and prompts you to save the file on your computer. The entire JavaScript application runs on your local computer and does not transmit any data.

I played around with the idea of using the ULR for the name of links without names in the file. I decided to leave them. Some services may find the name and auto-add? But Diigo gives them the name 'unnamed', which can be corrected after a quick search.

## Contributing

I threw this together when I became tired of Refind's limitations, and my import failed. I'd appreciate any code clean up or reworking to make more accessible, compatible, have a better interface or any other improvements.

## Dump Refind

Refind makes a great core product. And they are rolling out more and more features. I find it's not useful to keep bookmarks and notes. Comments are great. But when looking at a page or bookmark, you can't tell if you have comments or not.

I didn't find it as useful as a repository of bookmarks and comments as Shaari or Diigo.
