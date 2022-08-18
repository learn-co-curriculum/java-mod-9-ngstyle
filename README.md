# ngStyle

## Learning Goals

- Explain the ngStyle directive.

## The ngStyle Directive

`ngStyle` lets you assign actual CSS styles instead of assigning CSS classes.
This is most commonly done by creating a function in your component's controller
to return a list of styles on whatever conditions are appropriate for your use
case.

An example for our "online vs offline" use case might look like this in
`sender-message-component.component.ts`

```typescript
  getCurrentStyles() {
    let currentStyles = {
      'background-color': this.message.sender.isOnline ? 'blue' : 'red',
    };
    return currentStyles;
  }
```

And the corresponding view would look like this:

```html
<div class="container">
  <div class="row">
    <div class="col-1 p-3">
      <span class="badge" [ngStyle]="getCurrentStyles()">
        {{message.sender.firstName[0]}}</span
      >
    </div>
    <div class="col-8 p-3 border rounded-5">
      <span>{{message.text}}</span>
    </div>
  </div>
</div>
```

In general, however, we recommend using CSS classes instead of inline styles, as
they make your application much easier to maintain over time.
