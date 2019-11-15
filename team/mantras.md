---
title: Team mantras
description: A set of high level mantras the web and design team embrace
---

## Never remove data or functionality because of screen size
Never hide information or remove functionally on different screen sizes. In the modern era,  applications should be fully featured and easy to use on all devices and screens.

**Do:** If a details page contains a set of metadata and actions which can be performed on that entity. That data and functionality should be accessible on all screens.
For example, when viewing the list on a phone the user should be able to search and filter as they can on a desktop screen.

**Don’t**: Reduce the information on the listing to fit the content in.
For example, tables rows may need to stack or become expandible to persist that same information.


## Do not assume a user's intent
Any request for data should be clearly triggered by a user action such as a click or key press. Scrolling or hovering is not an intentional data request from a user.

**Do**: Provide a button or interaction that will clearly request more data from the server.
For example, provide a “Load more…” button at the end of a limited list to request to next page of data.

**Don’t**: On mouseover or scroll request additional data from the server.
For example: a tooltip that requests extra data to populate its contents.


## Reflect state of the application in the URL
All views in an application should be reflected in the URL so a user can share or bookmark an area and jump to it on load. This includes filter and search inputs on listing pages.

**Do**:  When entering an entity details reflect that view in the URL.
For example, /entity/12345

**Don’t**: When clicking to reveal a popover update the address. For example, when filtering and selecting the filters from the drop down do not persist that state in the URL.
For example, /listing/+filter-open


## Always allow the user to undo an action
If a user performs an action it should be clear how they can reverse the action.

**Do**: Pop up a notification to undo the action or replace the action button with an opposite action.
For example, Delete an entity and get a notification detailing its success and the action to undo.
**Don’t**:
For example, Mark an entity public without a clear action to make it private in case of mistakes.
