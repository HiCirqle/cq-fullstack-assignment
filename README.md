# Assignment

At The Cirqle, we help our clients to reach their marketing objectives. One way we do this, is by helping them connect with new (potential) customers through paid media (sponsored) posts. To be successful when running paid media campaigns, precise and strategic targeting is of the utmost importance.

Through our platform we allow our users to select what interest categories they'd like to target with their campaigns.

![tree select](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/assets/mockups/1_emtpy_state.jpg)

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

#### 2. You can pull this repository to start building the Node.js backend

Setup and run boilerplate locally

```
npm install
npm start
```

## Front end

Build a tree select component that allows the user to select interests.
Available interests are imported by consuming the endpoint created earlier.

The hierarchy for the interests can be found in the path property.
Users are able to select an unlimited amount of interests.

#### 1. Front end framework or tools

You're free to decide what tooling you'd like to use to build up the tree select widget.
At Cirqle we use Vue (plain JS and Pug for templating) together with (S)CSS.

#### 2. Interaction with tree select widget

![Clicking the label and/or chevron toggles the visibility of the node's direct children (if any).](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/assets/mockups/2_open_leaves.jpg)

Clicking the label and/or chevron toggles the visibility of the node's direct children (if any).

![Children can contain multiple levels of grandchildren.](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/assets/mockups/3_recursively_open_leaves.jpg)

Children can contain multiple levels of grandchildren.

Selecting a grandchild only adds the clicked element to the selection. Parents of the selected (grand)child now have the intermediary state.

![Selecting a grandchild only adds the clicked element to the selection.](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/assets/mockups/4_select%20node_leaf.jpg)
![Selecting a grandchild only adds the clicked element to the selection.](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/assets/mockups/5_select_intermediary_leaf.jpg)

When a parent is selected, all underlying children and grandchildren are selected too.

![Selecting a grandchild only adds the clicked element to the selection.](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/assets/mockups/6_select%20parent_leaf.jpg)
