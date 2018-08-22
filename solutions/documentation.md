# Recommended solutions for Documentation

Patterns for serving documentation pages to our communities and clients.

## Community documentation

The majority of our documentation will be community-focused. This means both that the various communities around our products are using the documentation, and that we hope they will also help to improve the documentation.

### Discourse forums for content

We recommend that community documentation content should live in [Discourse forums](https://www.discourse.org/). Discourse forums provide a useful model for building a community around our content.

This content could live inside a category inside [discourse.ubuntu.com](https://discourse.ubuntu.com/) or any other Discourse installation.

#### Structure

Documentation content should be stored in ["wiki" posts](https://meta.discourse.org/t/what-is-a-wiki-post/30801) that users can comment on, and when they build up enough trust, can edit directly. The [trust levels](https://blog.discourse.org/2018/06/understanding-discourse-trust-levels/) have configurable thresholds. Documentation topics should be grouped under an appropriately-named [category](https://meta.discourse.org/t/how-to-add-categories/71859) - e.g. `docs` or `product-docs`.

Each documentation set should have an introductory page, which should be pinned at the top of the `doc` category. At the bottom of this page should be a horizontal rule, followed by the heading "Content", and then a navigation list which should link to other documentation pages in the forum, e.g.:

``` markdown
Hello. Welcome to our documentation.

Please spend a while here.

---

# Content

## Basics

- [Getting started](/t/getting-started/3876)
- [Configuration options](/t/configuration-options/87)

## API

- [API outline](/t/api-outline/33)
```

#### Branching documentation

Every effort should be made to keep one canonical set of documentation. When there are differences between software versions that impact the documentation, these differences should be mentioned inline in the document - e.g. "Note: In v1.2 and below, the 'network' tab was called 'connections'".

If branches of documentation must be created, e.g. when a new major version of software is released, additional categories can be created for the old version - e.g. `docs-v1` alongside `docs-latest`. The title of this older content should contain the version number - e.g. `v1: Getting started`.

#### Base level categories
This is the list of basic categories that we recommend for any new Discourse installations. Teams may choose to modify their categories going forward, but such changes should be discussed beforehand with either the team (e.g. in the private "Staff" category) or the wider community (e.g. in the "General discussion" category).

##### News
A place for announcements and news about the product.

##### General discussions
Discussions about the product. 

##### Guides
Guides to help use and develop the product.

##### Social
Relaxed discussions loosely based on the product.

##### Feedback and bugs
Seeking help or found an issue with the product.

##### Docs
The latest product documentation

##### Staff (private)
The category for discussing processes and administrative topics.

#### Plugins

The owners of each Discourse installation ultimately decide how it should be managed. However, we discourage the use of plugins in Discourse, as it's easier to manage multiple Discourse installations if they remain as similar as possible.

### The website application

Documentation content will be pulled from the Discourse forum to be displayed on our official documentation websites - e.g. at https://maas.io/docs - which will be written and managed by the Web and Design team.

We will use a standard Python package, which we maintain, in each of our sites to pull this content and display it. This package will:

- Pull the "cooked" markup for the documentation page from Discourse, so the Discourse installation remains in control of parsing the markdown content.
  - Content will be pulled live (with some caching) so that changes to the content on Discourse will be reflected without significant delay.
- Extract the navigation and convert URL links to other Discourse forum posts into links that will work for the website
- Otherwise, perform no additional post-processing of the "cooked" markup
- Wrap the documentation in the HTML template for the site, and apply our standard set of styling

