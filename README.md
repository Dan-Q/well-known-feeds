# `.well-known/feeds` resource identifier

This document describes the use of URIs whose path component is `/.well-known/feeds`.

## Registration

Information required by RFC5785:

```
URI suffix: feeds
Change controller: Dan Q <https://danq.me/>
Specification document(s): https://github.com/Dan-Q/well-known-feeds
Status: provisional
Related information: OPML 2.0 specification <http://opml.org/spec2.opml>
```

## Representation

The `feeds` well-known resource endpoint provides an OPML document of any valid OPML version. That OPML document's `<body>` is expected to contain one or more `<outline>` elements, referencing some or all of the feeds published by or representative of the website. This might include for example outlines of `type="rss"` referring to feeds themselves, references of `type="include"` pointing to further OPML documents, or any other valid OPML content.

If in-use by a website, a request to the `feeds` well-known resource endpoint must return a valid OPML document using the `text/x-opml`, `application/xml`, or `text/xml` MIME type.

## As an alternative to `Link:`/`<link rel="alternate">`

`.well-known/feeds` supplements but does not replace the utility of techniques like `<link rel="alternate">` to reference RSS feeds associated with a web page. Specific differences include:

- `.well-known/feeds` provides a single lightweight location from which a user agent can retreive feed information, obviating the need for `<link>` headers delivered with every page
- `.well-known/feeds` is especially suitable for websites with multiple feeds, for example a news site or community weblog with different categories of feed
- `<link rel="alternate">` remains the best way to associate a feed with a specific page rather than with the entire site

## Use Cases

`.well-known/feeds` benefits:

- Content publishers who want to promote their feeds in a site-wide way
- Producers of feed reader software who need a way to enumerate feeds belonging to a site that a subscriber might like to add to their reading list
- Content consumers who want to use their feed reader see a "menu" of possible subscriptions available from a particular website
- Syndication services that want to be able to dynamically subscribe to new feeds published by a site, as they're added

## Security Considerations

There are no security considerations for this well-known resource identifier.
