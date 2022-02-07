# Assignment

At The Cirqle, we help our clients to reach their marketing objectives. One way we do this, is by helping them connect with new (potential) customers through paid media (sponsored) posts. To be successful when running paid media campaigns, precise and strategic targeting is of the utmost importance.

Through our platform we allow our users to select what interest categories they'd like to target with their campaigns.

![tree select](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/mockups/1_emtpy_state.jpg)

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

Please use Vue or Nuxt to build the frontend for this assignment.
At Cirqle we use Vue & Nuxt (plain ES6+ JS and Pug for templating) together with SCSS.


#### 2. Interaction with tree select widget (BASIC)
![Render the parent categories that are returned in a linear list, with a checkbox against each item](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/mockups/2_open_leaves.jpg)

Render the parent categories that are returned in a linear list, with a checkbox against each item. You need only render the parent items shown in this mockup, DO NOT RENDER CHILDREN ITEMS (this is for the extended version of this assignment). This also means you do not need to add the chevron indicating when a parent has been selected, a simple checkbox is enough.

When you select a parent category from this list, it should select this parent, and all the child categories underneath as returned from the Facebook API into a suitable object or array, and print this onto the screen somewhere. Again, when selecting parent items simply select the children from the data, do not do any visual rendering of child selection.


#### 2. Interaction with tree select widget (ADVANCED)

![Clicking the label and/or chevron toggles the visibility of the node's direct children (if any).](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/mockups/2_open_leaves.jpg)

Clicking the label and/or chevron toggles the visibility of the node's direct children (if any).

![Children can contain multiple levels of grandchildren.](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/mockups/3_recursively_open_leaves.jpg)

Children can contain multiple levels of grandchildren.

Selecting a grandchild only adds the clicked element to the selection. Parents of the selected (grand)child now have the intermediary state.

![Selecting a grandchild only adds the clicked element to the selection.](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/mockups/4_select%20node_leaf.jpg)
![Selecting a grandchild only adds the clicked element to the selection.](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/mockups/5_select_intermediary_leaf.jpg)

When a parent is selected, all underlying children and grandchildren are selected too.

![Selecting a grandchild only adds the clicked element to the selection.](https://github.com/HiCirqle/cq-fullstack-assignment/blob/master/mockups/6_select%20parent_leaf.jpg)
