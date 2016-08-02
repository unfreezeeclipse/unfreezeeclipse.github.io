---
title: "Disable the Eclipse Styling Engine"
date:  2016-08-02 15:30:00 +0300
---

Eclipse 4 introduced the ability to customize the appearance of the user interface. Applying [CSS-based styling](http://www.vogella.com/tutorials/Eclipse4CSS/article.html) allows adding custom colors, rounded colors and shades.

This eye sugar is an extra layer in the UI rendering and comes with some performance price.

Luckily, Eclipse Neon makes the styling engine optional. If you don't need the Dark Theme or a High Contrast theme, you can switch the styling off. You will lose some shades and rounded corners, but you will hardly notice the difference.

## Steps to disable the styling engine

1. Open Window > Preferences from the main menu.
2. Open the General > Appearance page.
3. Uncheck the "Enable theming" checkbox.
![Disable theming](/assets/disable-theming.png)
4. Click the OK button to close the page.
5. Restart the IDE.
