## Badges

### Examples

#### Dismissing

Using the badge JavaScript plugin, it's possible to dismiss any badge inline. Here's how:

- Be sure you've loaded the badge plugin, or the compiled Bootstrap JavaScript.
- Add a [close button]({{< docsref "/components/close-button" >}}) and the `.badge-dismissible` class, which adds extra padding to the right of the badge and positions the close button.
- On the close button, add the `data-bs-dismiss="badge"` attribute, which triggers the JavaScript functionality. Be sure to use the `<button>` element with it for proper behavior across all devices.

You can see this in action with a live demo:

```html
<span class="badge bg-primary badge-dismissable" role="badge">
  Primary
  <button type="button" class="btn-close" data-bs-dismiss="badge" aria-label="Close"></button>
</span>
```

```markdown
When an badge is dismissed, the element is completely removed from the page structure. If a keyboard user dismisses the badge using the close button, their focus will suddenly be lost and, depending on the browser, reset to the start of the page/document. For this reason, we recommend including additional JavaScript that listens for the `closed.bs.badge` event and programmatically sets `focus()` to the most appropriate location in the page. If you're planning to move focus to a non-interactive element that normally does not receive focus, make sure to add `tabindex="-1"` to the element.
```

### JavaScript behavior

#### Initialize

Initialize elements as badges

```js
var badgeList = document.querySelectorAll('.badge')
var badges = Array.prototype.slice.call(badgeList).map(function (element) {
  return new bootstrap.Badge(element)
})
```

```markdown
For the sole purpose of dismissing a badge, it isn't necessary to initialize the component manually via the JS API. By making use of `data-bs-dismiss="badge"`, the component will be initialized automatically and properly dismissed.

#See the [triggers](#triggers) section for more details.
```

#### Triggers

Dismissal can be achieved with the data attribute on a button within the alert as demonstrated below:

```html
<button type="button" class="btn-close" data-bs-dismiss="badge" aria-label="Close"></button>
```

or on a button outside the badge using the data-bs-target as demonstrated below:

```html
#<button type="button" class="btn-close" data-bs-dismiss="badge" data-bs-target="#my-badge" aria-label="Close"></button>
```


**Note that closing an badge will remove it from the DOM.**

#### Methods

```html
<table class="table">
  <thead>
    <tr>
      <th>Method</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <code>close</code>
      </td>
      <td>
        Closes an badge by removing it from the DOM. If the <code>.fade</code> and <code>.show</code> classes are present on the element, the badge will fade out before it is removed.
      </td>
    </tr>
    <tr>
      <td>
        <code>dispose</code>
      </td>
      <td>
        Destroys an element's badge. (Removes stored data on the DOM element)
      </td>
    </tr>
    <tr>
      <td>
        <code>getInstance</code>
      </td>
      <td>
        Static method which allows you to get the badge instance associated to a DOM element, you can use it like this: <code>bootstrap.Badge.getInstance(badge)</code>
      </td>
    </tr>
    <tr>
      <td>
        <code>getOrCreateInstance</code>
      </td>
      <td>
        Static method which returns an badge instance associated to a DOM element or create a new one in case it wasn't initialized.
        You can use it like this: <code>bootstrap.Badge.getOrCreateInstance(element)</code>
      </td>
    </tr>
  </tbody>
</table>
```

```js
var badgeNode = document.querySelector('.badge')
var badge = bootstrap.Badge.getInstance(badgeNode)
badge.close()
```

#### Events

Bootstrap's badge plugin exposes a few events for hooking into badge functionality.

```html
<table class="table">
  <thead>
    <tr>
      <th>Event</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>close.bs.badge</code></td>
      <td>
        Fires immediately when the <code>close</code> instance method is called.
      </td>
    </tr>
    <tr>
      <td><code>closed.bs.badge</code></td>
      <td>
        Fired when the badge has been closed and CSS transitions have completed.
      </td>
    </tr>
  </tbody>
</table>
```

```js
var myBadge = document.getElementById('myBadge')
myBadge.addEventListener('closed.bs.badge', function () {
  // do something, for instance, explicitly move focus to the most appropriate element,
  // so it doesn't get lost/reset to the start of the page
  // document.getElementById('...').focus()
})
```

## Input Badges

## How it works

The input badges uses dismissable [badge]({{< docsref "/components/badge" >}}) internally to provide the functionality.

## Example

Add tags below by pressing "Enter" and click on the cross button to remove them.

{{< example >}}
<input class="form-control" type="text" data-bs-badges="input-badges" data-bs-colour="secondary" data-bs-rounded="false">
{{< /example >}}

## JavaScript behavior

### Initialize

Initialize elements as input badges

```js
var inputBadgesList = document.querySelectorAll('input[type="text"][data-bs-badges="input-badges"]')
var inputBadges = Array.prototype.slice.call(inputBadgesList).map(function (element) {
  return new bootstrap.InputBadges(element)
})
```

### Methods

<table class="table">
  <thead>
    <tr>
      <th>Method</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <code>dispose</code>
      </td>
      <td>
        Destroys an element's badge. (Removes stored data on the DOM element)
      </td>
    </tr>
    <tr>
      <td>
        <code>getInstance</code>
      </td>
      <td>
        Static method which allows you to get the badge instance associated to a DOM element, you can use it like this: <code>bootstrap.Badge.getInstance(badge)</code>
      </td>
    </tr>
    <tr>
      <td>
        <code>getOrCreateInstance</code>
      </td>
      <td>
        Static method which returns an badge instance associated to a DOM element or create a new one in case it wasn't initialized.
        You can use it like this: <code>bootstrap.Badge.getOrCreateInstance(element)</code>
      </td>
    </tr>
  </tbody>
</table>

```js
var inputBadgesNode = document.querySelector('input[type="text"][data-bs-badges="input-badges"]')
var inputBadge = bootstrap.InputBadges.getInstance(inputBadgesNode)
inputBadge.dispose()
```

### Events

Bootstrap's input badges plugin exposes a few events for hooking into input badges functionality.

<table class="table">
  <thead>
    <tr>
      <th>Event</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>add.bs.input-badges</code></td>
      <td>
        Fires immediately 'Enter' is pressed and the input value is new and not empty.
      </td>
    </tr>
    <tr>
      <td><code>added.bs.input-badges</code></td>
      <td>
        Fires immediately after a new badge is added to the list.
      </td>
    </tr>
    <tr>
      <td><code>removed.bs.input-badges</code></td>
      <td>
        Fired after a badge is removed from the list.
      </td>
    </tr>
  </tbody>
</table>

```js
var inputBadges = document.getElementById('inputBadges')
inputBadges.addEventListener('add.bs.input-badges', function () {
  // do something, for instance, check the value to be added is valid
  // so it doesn't get to the field
})
```

