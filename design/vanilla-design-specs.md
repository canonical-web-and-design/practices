---
layout: base
title: Vanilla patterns design specs
---

This document describes what to include when writing a Vanilla pattern design spec.

## Location

Design specs live in the code section of the [Vanilla design repo](https://github.com/ubuntudesign/vanilla-design), or of the corresponding theme's design repo (e.g. [Brochure theme design repo](https://github.com/ubuntudesign/vanilla-brochure-theme-design)).

## Structure 

Each pattern should have its own folder, and include two files:
- Detailed written spec (.md format)
- Visual spec (.png format)

### Detailed written spec

The detailed spec file should include:

- Title of the pattern: e.g. "[Vanilla: Buttons](https://github.com/ubuntudesign/vanilla-design/blob/master/Buttons/buttons.md)" or "[Brochure theme: Buttons](https://github.com/ubuntudesign/vanilla-brochure-theme-design/blob/master/Buttons/buttons.md)"
- All the properties needed to build the pattern: e.g. font size, text colour, padding, borders, shadows, backgrounds 
- Where applicable, include responsive variations for different viewports
- Where applicable, include: hover, active and focused states

The spec shouldn't be written in CSS format. For example, avoid writing "font-size", write "font size" instead.

Some properties should be defined using Vanilla variables, to maintain consistency across the framework. These are:

- [Font sizes](https://docs.vanillaframework.io/en/base/typography)
- [Colours](https://docs.vanillaframework.io/en/settings/color-settings)
- [Padding and margins](https://docs.vanillaframework.io/en/settings/spacing-settings)
- [Animation](https://github.com/vanilla-framework/vanilla-framework/blob/develop/scss/_settings_animations.scss)

Written specs should follow the [Canonical copy style guide](https://github.com/canonical-webteam/practices/blob/master/content/copy-reviews.md). 

### Visual spec

The visual specs for the Vanilla and theme patterns live in a single Sketch file (per theme). The latest version of this file can be found in the [root of the design repo](https://github.com/ubuntudesign/vanilla-design).

Each artboard of the file represents one pattern. This makes it easier to export a flat image of the pattern, which will be its visual spec.

The visual spec does not have to include any written properties (measurements, etc.), however in some cases adding key values might be useful for quick reference. For example, the size of the icons in the [heading icon pattern](https://github.com/ubuntudesign/vanilla-brochure-theme-design/blob/master/Heading%20icon/heading-icon.png).