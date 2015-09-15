# SwiftRSS [![Build Status](https://travis-ci.org/tibo/SwiftRSS.svg)](https://travis-ci.org/tibo/SwiftRSS)

SwiftRSS is a simple RSS parser written in Swift. This repo is a fork of [tibo/SwiftRSS](https://github.com/tibo/SwiftRSS). I forked it because there has been no activity on the original repo for almost a year and it was incompatible with newer versions of Swift (this repo now works with Swift 2.0 and iOS 9).

## Swift versions
See the [releases](https://github.com/AlexChesters/SwiftRSS/releases) for information on which copy of the code supports which Swift version.

## Todo

- [x] Basic RSS Support
- [x] Handle internet dates (RFC822 & RFC3339)
- [x] Tests with several RSS feeds (Swift official blog, Wordpress, Tumblr)
- [x] Handle Feed headers
- [x] NSCoder compatibility
- [x] Handle Comment link, feed and count (specific to Wordpress)
- [x] Add images helper (an array of images URL like for BlockRSSParser)
- [x] Continuous integration

## Installation

For now you can install this module manually : Copy the content of the SwiftRSS folder and add it to your project.

You can also use this project as Git [submodule](http://git-scm.com/docs/git-submodule).

## Usage

This library is pretty simple to use.
All you need to do is to create a simple `NSURLRequest` with the URL of your feed and then use the `parseFeedForRequest()` method with the callback closure to be able to use your items or handle errors properly.

```swift
let request: NSURLRequest = NSURLRequest(URL: NSURL(string: http://developer.apple.com/swift/blog/news.rss))

RSSParser.parseFeedForRequest(request, callback: { (feed, error) -> Void in
  NSLog("Feed for : \(feed.title)")
  NSLog("contains : \(feed.items)")
})
```

As results you get a [RSSFeed](https://github.com/alexchesters/SwiftRSS/blob/master/SwiftRSS/RSSFeed.swift) object which contain a array of [RSSItem](https://github.com/alexchesters/SwiftRSS/blob/master/SwiftRSS/RSSItem.swift)s or, if something wrong happen the `NSError` which will give you the error from the network call or the parsing process.

## How to contribute

If you notice a bug, please open an issue with all the details and code to reproduce this issue.

If you want to contribute to the project, fix something or add a feature please fork this project, work in a seperate branch, and send a pull request. 
**Also please consider the following section about custom feeds and specific usecases**


## Custom feeds and specific usecases

This project is made to be a really simple RSS Parser for a basic news feed. You may need to parse more nodes if you want to use it with a custom feed (iTunes feed for instance).
With [BlockRSSParser](http://github.com/tibo/BlockRSSParser) I used to say that this kind of usage isn't really related to the originial philosophy of the project.

Now I think the best thing to do is to move these special use case to seperate branches.

If you want to adapt this project to a specific usecase, please fork the project, create a new branch named explicitly and send a pull request.

## Credits

Maintainers :
- [Thibaut Le Levier](http://github.com/tibo)

Code review: 
- [Ludovic Ollagnier](http://github.com/eLud)

Special thanks to :
- [Michael Waterfall](https://github.com/mwaterfall) author of the [MWFeedParser](https://github.com/mwaterfall/MWFeedParser/) where a lot of logic [on the Date formatters come from](https://github.com/mwaterfall/MWFeedParser/blob/master/Classes/NSDate%2BInternetDateTime.m)

## Licence

SwiftRSS is released under the MIT license. See LICENSE for details.
