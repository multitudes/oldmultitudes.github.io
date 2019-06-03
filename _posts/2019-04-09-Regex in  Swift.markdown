---
layout: post
title:  "Some Swift tips for beginner and intermediate"
date:   2019-06-03
categories: iOS, developer
comments: true
published: false
---


<div class="message">
"iOS and macOS programs have long been written in a language called Objective-C. In the summer of 2014, Apple introduced a new and exciting language for writing apps called Swift" 
<br><cite></cite>
</div>

Martin Fowler wrote, “any fool can write code that a computer can understand, but good programmers write code that humans can understand.”

<!-- <a rel="ar" href="/assets/img/AR-QL-Pictures/retrotv.usdz">
    <img src="/assets/img/AR-QL-Pictures/Screenshot5.jpg">
</a> -->


/*
# Regex
A regular expression (commonly known as a “regex”) is a string or a sequence of characters that specifies a pattern.

*/

import UIKit

var str = "Hello, playground"

let testString = "[ddd - ddd] - cat"


let range = NSRange(location: 0, length: testString.utf16.count)
let regex = try! NSRegularExpression(pattern: "[a-z]at")

regex.firstMatch(in: testString, options: [], range: range) != nil

extension NSRegularExpression {
convenience init(_ pattern: String) {
do {
try self.init(pattern: pattern)
} catch {
preconditionFailure("Illegal regular expression: \(pattern).")
} }
}
extension NSRegularExpression {
func matches(_ string: String) -> Bool {
let range = NSRange(location: 0, length: string.utf16.count)
return firstMatch(in: string, options: [], range: range) != nil
}
}

// now is better
regex.matches("hat")


//We could take things further by using operator overloading to make Swiftʼs contains operator, ~=, work with regular expressions:
extension String {
static func ~= (lhs: String, rhs: String) -> Bool {
guard let regex = try? NSRegularExpression(pattern: rhs) else { return false }
let range = NSRange(location: 0, length: lhs.utf16.count)
return regex.firstMatch(in: lhs, options: [], range: range) != nil
}
}

// That code lets us use any string on the left and a regex on the right, all in one:

"hat" ~= "[a-z]at"

"[aiuhewf - kjef] - kajsefjr.jre" ~= "[[a-z]*-[a-z]]"
//There is a cost to creating an instance of NSRegularExpression, so if you intend to use a regex repeatedly itʼs probably better to store the NSRegularExpression instance.
//you can either use “[a-zA-Z]at” or create your NSRegularExpression object with the flag .caseInsensitive.
// you might also use [A-Fa-f0-9] to match hexadecimal numbers,
// quantification:  how many times something ought to appear.

//asterisk quantifier, *, which means “zero or more matches


let regex2 = NSRegularExpression("ca[a-z]*d")

"hat" ~= "ca[a-z]*d"
"cat" ~= "ca[a-z]*d"
"card" ~= "ca[a-z]*d"

"cd" ~= "c[a-z]*d"  // zero or more lowercase letters
"cd" ~= "c[a-z]?d"  //  zero or one lowercase letters
"cd" ~= "c[a-z]+d"  // one or more lowercase letters

// to match the word “color” in both US English (“color”) and International English (“colour”), you could use the regex colou?r. That is, “match the exact string ‘coloʼ, the match zero or one ‘uʼs, then an ‘rʼ.

// you can also be more specific about your quantities: “I want to match exactly three characters.” This is done using braces, { and }. For example [a-z]{3} means “match exactly three lowercase letters.”

"card" ~= "[a-z]{3}"

//[a-z]{1,3} means “match one, two, or three lowercase letters”, and [a-z]{3,} means “match at least three, but potentially any number more.”
//    . character – a period – which will match any single character except a linebreak.So,theregexc.twillmatch“cat”butnot“cart”.Ifyouuse. with the * quantifier it means “match one or more of anything that isnʼt a line break,” which is probably the most common regex youʼll come across.

//.* will match almost everything. The problem is, being specific is sort of the point of regular expressions
//[0- 9]{3}[ -]*[0-9]{4} means “find three digits, then zero or more spaces and dashes, then four digits.

//[0- 9]{3}[^0-9]+[0-9]{4} will match a space, a dash, a slash, and more – but it wonʼt match numbers

//https://www.raywenderlich.com/5765-regular-expressions-tutorial-getting-started
//https://whatdidilearn.info/2018/07/29/how-to-capture-regex-group-values-in-swift.html


let title = "Season 1 Episode 3 - When Joey meets Zoey"
//From that title we need to extract values “1” and “3” as a season and an episode numbers respectively. The regular expression pattern would look like:

let pattern = "^Season\\s+(\\d+)\\s+Episode\\s+(\\d+)"
//First we are looking for the text “Season” at the beginning of the string. The ^ indicates that.
//It should be followed by at least one space character (\\s+).
//Then followed by at least one number \\d+. We are also wrapping that value into parenthesis because we are going to capture it (\\d+).

let regex3 = try? NSRegularExpression(
pattern: pattern,
options: .caseInsensitive
)

// Then the expression followed by space characters again
"Season 1 Episode 3 - When Joey meets Zoey" ~= "^Season\\s+(\\d+)\\s+Episode\\s+(\\d+)"

if let match = regex3?.firstMatch(in: title, options: [], range: NSRange(location: 0, length: title.utf16.count)) {
print(match)

}

// Let’s try to refactor the code a little bit.

// First, accessing the captured groups by its index does not seem to be very readable. We can provide a name to every group in the regular expression pattern.

let pattern2 = "^Season\\s+(?<season>\\d+)\\s+Episode\\s+(?<episode>\\d+)"



let invitation = "Fancy a game of [Cluedo™?"
invitation.range(of: "Clue(do)?™?", options: .regularExpression) != nil
// true

let instructions =
"""
The object is to solve by means of elimination and deduction
the problem of the mysterious murder of Dr. Black.
"""

instructions.replacingOccurrences(
of: #"(Dr\.|Doctor) Black"#,
with: "Mr. Boddy",
options: .regularExpression
)



import UIKit
import Foundation

let title22 = "Season 1 Episode 3 - When Joey meets Zoey"
let pattern22 = "^Season\\s+(\\d+)\\s+Episode\\s+(\\d+)"
let regex22 = try? NSRegularExpression(pattern: pattern22, options: .caseInsensitive)

if let match = regex22?.firstMatch(in: title22, options: [], range: NSRange(location: 0, length: title22.utf16.count)) {
if let seasonRange = Range(match.range(at: 1), in: title22) {
let seasonNumber = title22[seasonRange]
}

if let episodeRange = Range(match.range(at: 2), in: title22) {
let episodeNumber = title22[episodeRange]
}
}




### Sources:

[](https://www.raywenderlich.com/5767-an-introduction-to-regular-expressions)
[](https://www.raywenderlich.com/5765-regular-expressions-tutorial-getting-started)
[](https://www.regular-expressions.info/backref.html)
[](https://www.regular-expressions.info)
[](https://developer.apple.com/documentation/foundation/nsregularexpression)

<hr>

[^1]: What?
