# Working with ISBN

The **International Standard Book Number** (ISBN) of a book is a unique number
which helps identify information about published works. While Hardcover will
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
specific edition. The International ISBN Agency maintains an annually updated and searchable database of all registered publishers: The <a href="https://grp.isbn-international.org/" target="_blank">Global Register of Publishers</a>.
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

*For a complete list refer to <a href="https://en.wikipedia.org/wiki/List_of_ISBN_registration_groups" target="_blank">Wikipedia</a>*

If you see ISBN `9782820344960` with the `Country` listed as `United States of
America` you will immediately know that this edition needs editing!

We can also use the group block to identify whether an edition with a Portuguese title was published in Portugal (972) or Brazil (85).

## Calculating ISBN10 from ISBN13 (or vice versa)

Books published before 2007 will most likely use a ten-digit long ISBN. Similarly,
books published after 2007 often lack an ISBN10. You can calculate the
corresponding ISBN with an [online
tool](http://www.hahnlibrary.net/libraries/isbncalc.html).

!> Simply adding or removing ``978`` in front of an ISBN will not result in a valid number! 

## Retrieving information about a book

The ISBN does not encode information such as title or author of a book.
Hardcover will pull these fields from various databases automatically. We can
verify this data with the help of a few websites:

* <a href="https://isbnsearch.org" target="_blank">ISBNsearch.org</a>: Quickly check the binding,
publication date and associated cover
* <a href="https://search.worldcat.org/" target="_blank">WorldCat</a>: WorldCat will often include physical
descriptions of a book, including the page count
* <a href="https://amazon.com" target="_blank">Amazon</a>: Searching for an ISBN will return the product
page associated with the book. Amazon has high resolution covers and often a
complete list of series information
* <a href="https://books.google.com" target="_blank">Google Books</a>: You can search through Google's
database for a specific book by appending `isbn:` in front of the ISBN. Example:
`isbn:9782820344960`. **Careful**: Google tends to auto-translate. The result above shows ``Band 1`` for users in Germany, but the edition is actually from France and should be labeled as ``Tome 1``!

Finally, you can look up information directly on a publisher's website, which
will often feature the most accurate and up-to-date data.

### National Libraries, Services and Retailers

* <a href="https://catalogue.bnf.fr" target="_blank">BnF Catalogue Général</a>: France
* <a href="https://www.books.or.jp/" target="_blank">Books.or.jp</a>: Japan
* <a href="https://katalog.dnb.de/DE/home.html?v=plist" target="_blank">Deutsche National Bibliothek</a>: Germany
* <a href="https://www.kb.nl/en/research-find" target="_blank">Koninklijke Bibliotheek</a>: Netherlands
* <a href="https://www.loc.gov/" target="_blank">Library of Congress</a>: United States of America
* <a href="https://www.cultura.gob.es/en/cultura/libro/isbn.html" target="_blank">Ministerio de Cultura de España</a>: Spain
* <a href="https://urn.porbase.org" target="_blank">PORBASE Catalogue</a>: Portuguese language
* <a href="https://opac.sbn.it/" target="_blank">Servizio Bibliotecario Nazionale</a>: Italy

Retailers are also a good source for information, for example:

* <a href="https://www.agapea.com/" target="_blank">Agapea</a>: Spain
* <a href="https://www.barnesandnoble.com/" target="_blank">Barnes & Noble</a>, <a href="https://www.powells.com/" target="_blank">Powells</a>: United States of America
* <a href="https://www.cultura.com/" target="_blank">Cultura</a>, <a href="https://www.fnac.com" target="_blank">fnac</a>: France
* <a href="https://www.thalia.de/" target="_blank">Thalia</a>, <a href="https://www.buecher.de/" target="_blank">Bücher.de</a>: Germany

## ASIN

Amazon uses the **Amazon Standard Identification Number** (ASIN) for product
identification within their internal system. ASIN is not an international
standard. You can view the ASIN of a book on the associated product page on
Amazon's website. The quickest way to find the ASIN is to look at the URL:

`https://www.amazon.com/dp/0143105434`

The ASIN usually follows directly after `dp`. For *Wuthering Heights* the ASIN
is thus `0141439556`. 

?> Note that printed books are often assigned their ISBN10 as ASIN.

* <a href="https://addons.mozilla.org/en-US/firefox/addon/asin-collector/" target="_blank">ASIN Collector</a> is a Firefox extension that can bulk-extract ASIN's for all available editions of a book.

### eBook ASIN

For eBooks the ASIN usually starts with a `B` and is listed under *Product
details*.

*Penguin Classics' Wuthering Heights deluxe edition*'s ASIN is `B0768ZM5QH`.

!> Don't get tricked by Amazon: It will almost always omit the ISBN of an eBook
in favor of ASIN. That doesn't mean that the eBook of *Wuthering Heights* is
Kindle-exclusive. You can find the ISBN of an eBook by visiting the publisher's
website. Example: <a href="https://www.penguinrandomhouse.com/books/286389/wuthering-heights-by-emily-bronte/" target="_blank">Wuthering Heights</a> eBook ISBN is `9780525505143`.

## Other available tools

### isbntools
* <a href="https://pypi.org/project/isbntools/" target="_blank">isbntools</a> is a python CLI application
capable of retrieving ISBN information from various sources. It can also process
multiple ISBN provided by a text-file or even other CLI programs.

Please refer to the official documentation for install instructions. Some useful commands:

```bash
# Fuzzy find an ISBN from the title (always confirm the result!)
isbn_from_words "mistborn final empire"
> 9780765311788

# Return a collection of ISBN's associated with a book
isbn_editions 9780765311788
> 9788413143194
> 9784150204990
> 9784150204952
> ...

# Get basic meta information
isbn_meta 9780765311788
> Type:      BOOK
> Title:     Mistborn - The Final Empire
> Author:    Brandon Sanderson
> ISBN:      9780765311788
> Year:      2006
> Publisher: Macmillan

# Calculate ISBN10
to_isbn10 9780765311788
> 076531178X

# Split ISBN into its elements
isbn_mask 9780765311788
> 978-0-7653-1178-8

# Use a specific service and output-format
isbn_meta 9780525505143 goob json
> {"type": "book",
>    "title": "Wuthering Heights - (Penguin Classics Deluxe Edition)",
>   "author": [{"name": "Emily Bronte"}],
>     "year": "2009",
> "identifier": [{"type": "ISBN", "id": "9780525505143"}],
> "publisher": "Penguin"}
```
