Originally ianwalter/ng-context-menu

This project is not maintained any longer. Please feel free to fork it if you need to make changes to the library.

# [ng-context-menu](http://ianwalter.github.io/ng-context-menu/)
*An AngularJS directive to display a context menu when a right-click event is triggered*

#### Step 1: Install ng-context-menu

Install using Bower:

```
bower install ng-context-menu --save
```

Include ng-context-menu.min.js in your app.

#### Step 2: Load the ng-context-menu module

```javascript
var app = angular.module('menu-demo', ['ngRoute', 'ng-context-menu'])
```

#### Step 3: Add the context-menu directive to a DOM element

```html
<div context-menu class="panel panel-default position-fixed"
     data-target="menu-{{ $index }}"
     ng-class="{ 'highlight': highlight, 'expanded' : expanded }">
  ...
</div>
```
#### Step 4: Add the markup of the menu you want to be displayed

Customize the menu to your needs. It may look something like:

```html
<div class="dropdown position-fixed" id="menu-{{ $index }}">
  <ul class="dropdown-menu" role="menu">
    <li>
      <a class="pointer" role="menuitem" tabindex="1"
         ng-click="panel.highlight = true">
         Select Panel {{ $index + 1 }}
      </a>
    </li>
    <li>
      <a class="pointer" role="menuitem" tabindex="2"
         ng-click="panel.highlight = false">
         Deselect Panel  {{ $index + 1 }}
      </a>
    </li>
    <li>
      <a class="pointer" role="menuitem" tabindex="3"
         ng-click="panel.expanded = true">
         Expand Panel {{ $index + 1 }}
      </a>
    </li>
    <li>
      <a class="pointer" role="menuitem" tabindex="4"
         ng-click="panel.expanded = false">
         Contract Panel {{ $index + 1 }}
      </a>
    </li>
    <li>
      <a class="pointer" role="menuitem" tabindex="5"
         ng-click="addPanel()">
         Add a panel
      </a>
    </li>
    <li>
      <a href="https://github.com/ianwalter/ng-context-menu"
         role="menuitem"
         tabindex="-1">
         ng-context-menu on GitHub
      </a>
    </li>
  </ul>
</div>
```

#### Step 5: Make sure your menu is has the ```position: fixed``` CSS property

As you can see in the demo, I just created a class called position-fixed and added the property:

```css
.position-fixed {
  position: fixed;
}
```

#### Disabling the contextmenu

If you need to disable the contextmenu in certain circumstances, you can add an expression to the
 ```context-menu-disabled``` attribute. If the expression evaluates to true, the contextmenu will be
 disabled, for example, ```context-menu-disabled="1 === 1"```

That's it, I hope you find this useful!

#### `close` Callback

Add the following attribute to the `context-menu` element: `context-menu-close` which should be a function
that will be called whenever the context menu is closed.

```html
<div context-menu="onShow()" context-menu-close="onClose()"></div>
```

#### Customizing the bind event

By default, the context menu will open when the ```contextmenu``` event is triggered.  You can override this by specifying a value for the ```context-menu-event``` attribute.

```html
<div context-menu="onShow()" context-menu-close="onClose()" context-menu-event="click"></div>
```

Some possible values are ```contextmenu``` for right-click (default), ```click``` for left-click, ```focus```, ```onmouseover```, etc. You may specify multiple event types by separating them with a space.

«–– [Ian](http://ianvonwalter.com)
