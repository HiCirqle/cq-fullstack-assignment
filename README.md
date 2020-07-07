# Setup

```
npm install
npm start
```

# Assignment

Allow users to select ad interests to target ads towards specific Facebook users.

## Back end

Create 1 endpoint to get Facebook ad interests information.

You can find documentation on how to get this data from Facebook here:
https://developers.facebook.com/docs/marketing-api/audiences/reference/targeting-search/

#### 1. Create a GET endpoint that returns a JSON array with all Facebook interests (id + name)

In the docs search for type=adTargetingCategory&class=interests

E.g.

```
GET /interests
[
  {"id":"6007828099136", "name":"Luxury goods", "path": "[...]" },
  {"id":"6009422452499", "name":"Home and garden", "path": "[...]" }
  ...
]
```

Notes:
Some interests are deprecated/not deliverable. To verify the status, use the Targeting Status endpoint (search for type=targetingoptionstatus).
Only return ad interests with status "NORMAL"

## Front end

Build a tree select component that allows the user to select interests.
Available interests are imported by consuming the endpoint created earlier.

The hierarchy for the interests can be found in the path property.
Users are able to select an unlimited amount of interests.

### 1. Front end framework or tools

You're free to decide what tooling you'd like to use to build up the tree select widget.
At Cirqle we use Vue (plain JS and Pug for templating) together with (S)CSS.

### 2. Interaction with tree select widget

Clicking the label and/or chevron toggles the visibility of the node's direct children (if any).

Children can contain multiple levels of grandchildren.

Selecting a grandchild only adds the clicked element to the selection. Parents of the selected (grand)child now have the intermediary state.

When a parent is selected, all underlying children and grandchildren are selected too.
