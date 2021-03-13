First Header
=============
second header
-------------

# First Header
## Second Header
### Third Header

# Lists
* one
* two
* three

+ one
+ two
+ three

- one
- two
- three

* one
* + one
* + - one
* + - two
* + - three

* + two
* + three

* two
* three

1. one
2. two
3. three

## List with Paragraphs
* list item

  This is a paragraph inside a list

* list item after paragragh

# Links
Lets go to [GitHub](https://www.github.com/ "interesing")

<http://example.com/>

## Reference Links
Search tools are [Google][1], [Yahoo][2], [Bing][Bing], and [My search engine][]

[1]: http://google.com    "Google link text"
[2]: http://yahoo.com
[Bing]: http://bing.com   "Bing link text"
[My Search Engine]: http://bing.com   "also bing"

# Images
![alt text][image-id]

[image-id]: https://images-tt-com.nmo.at/v2/assets.tt.com/im-content/images/a6ef4bed-5279-57a2-a912-9bbd3aced1df?p=eyJjcm9wIjp7InR5cGUiOiJwZXJjZW50IiwibGVmdCI6MCwidG9wIjowLCJ3aWR0aCI6MSwiaGVpZ2h0IjowLjkyNTkyNTkyNTkyNTkyNTl9LCJyZXNpemUiOnsid2lkdGgiOjEyODAsImhlaWdodCI6NzIwLCJmaXQiOiJjb3ZlciJ9LCJmb3JtYXQiOiJ3ZWJwIn0%3D "What's up doc!"

# Code
Inline `<code>` element

    void swap(int& x, int& y)
    {
        x = x + y
        y = x - y
        x = x - y
    }

``There is a literal backtick (`) here.``

A single backtick in a code span: `` ` ``

A backtick-delimited string in a code span: `` `foo` ``

`&#8212;` is the decimal-encoded equivalent of `&mdash;`.

# German Umlauts
"M&uuml;ller"

* a-umlaut - &auml;
* o-umlaut - &ouml;
* u-umlaut - &uuml;

# Paragraphs
<blockquote>
    <p>Nice looking paragraph</p>
</blockquote>

Also a paragraph<br />
this is a new line.

Also a paragraph  
this is a new line.

1.  This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

2.  Suspendisse id sem consectetuer libero luctus adipiscing.


<blockquote>
Also a paragraph      
this is a new line.
</blockquote>

# Horizontal line
---

# Emphasis
*single asterisks*

_single underscores_

**double asterisks**

__double underscores__

un*frigging*believable

\*this text is surrounded by literal asterisks\*

# Tables
| Syntax | Description |
| --- | --- |
| r1c1 | r1c2 |
| row2 - column-1 | row2 - column-2 |


| Left Aligned Column | Center Aligned Column | Right Aligned Column |
| :--- | :---: | ---: |
| r1c1 | r1c2 | r1c3 |
| row2 - column-1 | row2 - column-2 |row-2 \| column-3|

<table>
    <thead>
        <tr>
            <th>Layer 1</th>
            <th>Layer 2</th>
            <th>Layer 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=4>L1 Name</td>
            <td rowspan=2>L2 Name A</td>
            <td>L3 Name A</td>
        </tr>
        <tr>
            <td>L3 Name B</td>
        </tr>
        <tr>
            <td rowspan=2>L2 Name B</td>
            <td>L3 Name C</td>
        </tr>
        <tr>
            <td>L3 Name D</td>
        </tr>
    </tbody>
</table>
