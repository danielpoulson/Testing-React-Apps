Enzyme
=======

Enzyme is a JavaScript Testing utility for React that makes it easier to assert, manipulate,
and traverse your React Components' output.

Enzyme's API is meant to be intuitive and flexible by mimicking jQuery's API for DOM manipulation
and traversal.

# Shallow Rendering API

Shallow rendering is useful to constrain yourself to testing a component as a unit, and to ensure
that your tests aren't indirectly asserting on behavior of child components.

Jest Snapshot Testing
=======================

Snapshot tests are a very useful tool whenever you want to make sure your UI does not change unexpectedly.

Instead of rendering the graphical UI, which would require building the entire app, you can use a test renderer to quickly generate a serializable value for your React tree.


```javascript
import React from 'react';
import Link from '../Link.react';
import renderer from 'react-test-renderer';

it('renders correctly', () => {
  const tree = renderer.create(
    <Link page="http://www.facebook.com">Facebook</Link>
  ).toJSON();
  expect(tree).toMatchSnapshot();
});
```

The first time this test is run, Jest creates a [snapshot file](https://github.com/facebook/jest/blob/master/examples/snapshot/__tests__/__snapshots__/Link.react-test.js.snap) that looks like this:

```javascript
exports[`renders correctly 1`] = `
<a
  className="normal"
  href="http://www.facebook.com"
  onMouseEnter={[Function]}
  onMouseLeave={[Function]}
>
  Facebook
</a>
`;
```

## Updating Snapshots

To resolve this, we will need to update our snapshot artifacts. You can run Jest with a flag that will tell it to re-generate snapshots:

```
jest --updateSnapshot
```


# Resources to read

* Testing React components with Jest and Enzyme
https://hackernoon.com/testing-react-components-with-jest-and-enzyme-41d592c174f