# Working with ISBN

The **International Standard Book Number** (ISBN) of a book is a unique number
which helps identify information about published work. While Hardcover will
pull most information associated with an ISBN automatically, it can still be
helpful to know how to use an ISBN to retrieve data about an edition you're
intending to add to the database.

?> Some retailers may refer to an ISBN as *European Article Number* (EAN).

## Dissecting an ISBN

Let's look at all the different parts that make up an ISBN:

| EAN | Group | Publisher | Title | Check digit |
| --- | ----- | --------- | ----- | ----------- |
| 978 | 1     | 9747      | 3463  | 4           |

- **EAN**: Almost always 978 or 979
- **Registration Group**: Either a language-sharing country group, individual
country or territory
- **Publisher**: A unique number issued to a registered publisher by their local
or national ISBN registration agency
- **Title / Publication Element**: A unique number assigned by the publisher which is
associated with a specific edition of a book
- **Check digit**: A checksum character or digit, validating the ISBN

### Identifying the publisher of a book

With the help of the first three blocks we can look up the publisher of a
specific edition. The International ISBN Agency maintains an annually updated and searchable database of all registered publishers: The [Global Register of Publishers](https://grp.isbn-international.org/).
In our example above the registered publisher for any works starting with `978-1-9747` is `Viz Media, United States of America`.

### Identifying a mismatch between `Country` and ISBN

You will often find that Hardcover has pulled the wrong information for the
`Country` field of an edition. The second block of an ISBN will make that obvious
at a glance. 

| Group | Region / Language Area / Country     |
| ----- | ------------------------------------ |
| 0     | English                              |
| 1     | English                              |
| 2     | French                               |
| 3     | German                               |
| 4     | Japan                                |
| 5     | Former USSR                          |
| 6     | Prefixes of length 2 or 3            |
| 7     | China                                |
| 8     | Prefixes of length 2                 |
| 9     | Prefixes of length 2, 3, 4 or 5      |

*For a complete list refer to [Wikipedia](https://en.wikipedia.org/wiki/List_of_ISBN_registration_groups)*

If you see ISBN `9782820344960` with the `Country` listed as `United States of
America` you will immediately know that this edition needs editing!

## Calculating ISBN10 from ISBN13 (or vice versa)

Books published before 2007 will most likely use a ten-digit long ISBN. Similarly,
books published after 2007 often lack an ISBN10. You can calculate the
corresponding ISBN with an [online
tool](http://www.hahnlibrary.net/libraries/isbncalc.html).

!> Simply adding or removing '978' in front of an ISBN will not result in a valid number! 

## Retrieving information about a book

The ISBN does not encode information such as title or author of a book.
Hardcover will pull these fields from various databases automatically. We can
verify this data with the help of a few websites:

* [ISBNsearch.org](https://isbnsearch.org): Quickly check the binding,
publication date and associated cover
* [WorldCat](https://search.worldcat.org/): WorldCat will often include physical
descriptions of a book, including the page count
* [Amazon](https://amazon.com): Searching for an ISBN will return the product
page associated with the book. Amazon has high resolution covers and often a
complete list of series information
* [Google Books](https://books.google.com): You can search through Google's
database for a specific book by appending `isbn:` in front of the ISBN. Example:
`isbn:9782820344960`

Finally, you can look up information directly on a publisher's website, which
will often feature the most accurate and up-to-date data.

### National Libraries, Services and Retailers

* [BnF Catalogue Général](https://catalogue.bnf.fr): France
* [PORBASE Catalogue](https://urn.porbase.org): Portuguese language
* [Library of Congress](https://www.loc.gov/): United States of America
* [Ministerio de Cultura de España](https://www.cultura.gob.es/en/cultura/libro/isbn.html): Spain
* [Deutsche National Bibliothek](https://katalog.dnb.de/DE/home.html?v=plist):
Germany
* [Servizio Bibliotecario Nazionale](https://opac.sbn.it/): Italy
* [Koninklijke Bibliotheek](https://www.kb.nl/en/research-find): Netherlands
* [Books.or.jp](https://www.books.or.jp/): Japan

Retailers are also a good source for information, for example:

* [Barnes & Noble](https://www.barnesandnoble.com/), [Powells](https://www.powells.com/): United States of America
* [Thalia](https://www.thalia.de/), [Osiander](https://www.osiander.de/): Germany
* [Cultura](https://www.cultura.com/), [fnac](https://www.fnac.com): France
* [Agapea](https://www.agapea.com/): Spain

## ASIN

Amazon uses the **Amazon Standard Identification Number** (ASIN) for product
identification within their internal system. ASIN is not an international
standard. You can view the ASIN of a book on the associated product page on
Amazon's website. The quickest way to find the ASIN is to look at the URL:

`https://www.amazon.com/dp/0143105434`

The ASIN usually follows directly after `dp`. For *Wuthering Heights* the ASIN
is thus `0141439556`. Note that books are often assigned their ISBN10 as ASIN.

* [ASIN Collector](https://addons.mozilla.org/en-US/firefox/addon/asin-collector/) is a Firefox extension that can bulk-extract ASIN's for all available editions of a book.

### eBook ASIN

For eBooks the ASIN usually starts with a `B` and is listed under *Product
details*.

*Penguin Classics' Wuthering Heights deluxe edition*'s ASIN is `B0768ZM5QH`.

!> Don't get tricked by Amazon: AMZ will almost always omit the ISBN of an eBook
in favor of ASIN. That doesn't mean that the eBook of *Wuthering Heights* is
Kindle-exclusive. You can find the ISBN of an eBook by visiting the publisher's
website. Example: [Wuthering Heights](https://www.penguinrandomhouse.com/books/286389/wuthering-heights-by-emily-bronte/) eBook ISBN is `9780525505143`.

## Other available tools

* [isbntools](https://pypi.org/project/isbntools/) is a python CLI application
capable of retrieving ISBN information from various sources. It can also process
multiple ISBN provided by a text-file or even other CLI programs.
