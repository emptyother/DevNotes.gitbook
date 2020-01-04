---
description: Anything related to the ExtJs 3 javascript library.
---

# ExtJs 3

## Ext.util.Observable

Base class that handles events. This is not DOM events, but are often bound to the DOM events. Doesn't do any rendering.

Useful methods:

* **addListener\(eventName, handler\)**: Add a function to a list in the property

  `this.events[eventName]`.

* **on\(eventName, handler\)**: Alias of addListener.
* **fireEvent\(eventName, ...args\)**: Iterates trough every function in

  `this.events[eventName]` and calls them with the arguments.

* **enableBubble\('myEvent'\)**: When myEvent is fired, calls

  `this.container.fireEvent('myEvent')`.

* **un\(..\)**: Alias of removeListener.

## Ext.Component \(extends Ext.util.Observable\)

Base class for almost all Ext JS classes. Handles rendering.

Useful configs:

* `{ renderTo: myDiv }` Calls `render(myDiv)` immediatly after constructor.
* `{ autoEl: { tag: 'div', cls: 'myClass' } }` How the DOM element should look

  like. Default is just `'div'`.

* `{ tpl: new Ext.Template("<div>{myName}</div>") }` A template for rendering

  this component.

* `{ data: { myName: 'My Name' } }` If you have set a `tpl`, this object gets

  merged into the template.

* `{ html: 'My text' }` If you aren't using a template and data, this just

  renders text directly to `this.el.dom.innerHTML`.

Useful methods:

* **render\(myDiv\)**: Creates a Ext.Element in `this.el`. Renders the component

  to `this.el.dom`.

* **getEl\(\)**: Returns `this.el`.
* **setVisible\(bool\) / show\(\) / hide\(\)**
* **setDisabled\(bool\) / enable\(\) / disable\(\)**
* **update\(data\)**: Re-renders `this.el.dom` using this data and the template.

Example:

```typescript
const target = document.getElementById('myTarget') as HTMLElement;
const g = new Ext.Component({
    html: 'This is ExtJS body text.',
});
g.render(target);
```

Result:

```markup
<div id="myTarget">
    <div id="ext-comp-1018">This is ExtJS body text.</div>
</div>
```

## Ext.BoxComponent \(extends Ext.Component\)

Base class for any Component that is to be sized as a box, using width and height.

Example:

```typescript
const g = new Ext.BoxComponent({
    html: 'This is a box component.',
});
g.setSize(200, 200);
g.render(target);
```

Result:

```markup
<div id="myTarget">
    <div id="ext-comp-1004" style="width: 200px; height: 200px;">
        This is a box component.
    </div>
</div>
```

## Ext.Container \(extends Ext.BoxComponent\)

Base class for any Ext.BoxComponent that may contain other Components.

On render it does `this.items = new Ext.util.MixedCollection()`. The class has methods for adding or removing items, and uses a layout property to decide how to render the child items.

If you are using a layout, the child items should inherit from Ext.Panel.

Useful configs:

* `{ layout: 'form' }` Sets a layout.
* `{ items: [myComponent, myComponent2] }` These items will be added at render.
* `{ defaultType: 'button' }` The default type of all child items if you are

  using xtypes instead of classes. Defaults to `panel`.

Useful methods:

* **doLayout\(\)**: Refreshes the layout. Useful if you have resized the

  container.

* **add\(myComponent\)**: Calls `this.items.add(myComponent)` and then calls

  `this.doLayout()`.

* **getComponent\("myItem1"\)**: Searches `this.items.items[]` for any object that

  has `itemId: "myItem1"`.

* **find\("itemId", "myItem1"\)**: Searches `this.items.items[]` and children for

  all items that has `itemId: "myItemId1"`.

* **findBy\(function\)**: Find by custom function.
* **removeAll\(\)**: Removes everything from `this.items.items[]`.

Example:

```typescript
const g = new Ext.Container({
    layout: 'column',
    items: [
        new Ext.Panel({
            html: 'Item 1',
            columnWidth: 0.5,
        }),
        new Ext.Panel({
            html: 'Item 2',
            columnWidth: 0.5,
        }),
    ],
});
g.render(target);
```

Result:

```markup
<div id="myTarget">
    <div id="ext-comp-1028" class=" x-column-layout-ct">
        <div class="x-column-inner" id="ext-gen29" style="width: 923px;">
            <div id="ext-comp-1026" class=" x-panel x-column" style="width: 461px;">
                <div class="x-panel-bwrap" id="ext-gen31">
                    <div
                        class="x-panel-body x-panel-body-noheader"
                        id="ext-gen32"
                        style="width: 461px;"
                    >
                        Item 1
                    </div>
                </div>
            </div>
            <div id="ext-comp-1027" class=" x-panel x-column" style="width: 461px;">
                <div class="x-panel-bwrap" id="ext-gen34">
                    <div
                        class="x-panel-body x-panel-body-noheader"
                        id="ext-gen35"
                        style="width: 461px;"
                    >
                        Item 2
                    </div>
                </div>
            </div>
            <div class="x-clear" id="ext-gen30"></div>
        </div>
    </div>
</div>
```

## Ext.Panel \(extends Ext.Container\)

A more advanced container. The Panel has a border, a title, a top toolbar, a body, a bottom toolbar and a button/footer area. It can be collapsed, closed, or dragged.

