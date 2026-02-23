---
tags:
  - Markup
  - HTML
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses HTML box model layout.
Status: Done
Started: 
EditDate: 2024-02-26
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[Box model layout.png]]

The **blue box**, symbolizing the content area, encapsulates the actual content like text, images, or video within the element. It is defined by the content width (or content-box width) and content height (or content-box height), often complemented by a background color or image.

When the box-sizing property is set to content-box (default) and the element is a block element, the content area's dimensions can be precisely specified using properties such as width, min-width, max-width, height, min-height, and max-height. This allows explicit control over the size of the content within the element.

The **green box**, representing the padding area, expands from the padding edge, enveloping the content area and including the element's padding. Its dimensions are defined by the padding-box width and the padding-box height.

Adjusting the thickness of the padding is achieved through properties like padding-top, padding-right, padding-bottom, padding-left, and shorthand padding. These properties collectively determine the space between the content and the border, contributing to the overall design and layout of the element.


The **light orange box**, denoting the border area, expands from the border edge, encompassing the padding area and incorporating the element's borders. Its dimensions are determined by the border-box width and the border-box height.

Controlling the thickness of the borders is achieved through the border-width and shorthand border properties. When the box-sizing property is set to border-box, the border area's size can be precisely defined using properties like width, min-width, max-width, height, min-height, and max-height.

Additionally, if a background (background-color or background-image) is set on a box, it naturally extends to the outer edge of the border, essentially reaching underneath the border in z-ordering. This default behavior can be modified using the background-clip CSS property.


The **orange box**, representing the margin area, extends from the margin edge, enlarging the border area to create an empty space that separates the element from its neighboring elements. Its dimensions are specified by the margin-box width and the margin-box height.

The size of the margin area is dictated by properties such as margin-top, margin-right, margin-bottom, margin-left, and the shorthand margin. In instances of margin collapsing, where margins are shared between boxes, the margin area may not be distinctly defined.

For non-replaced inline elements, the space they occupy, contributing to the height of the line, is determined by the line-height property. This occurs even though borders and padding are still visibly displayed around the content.