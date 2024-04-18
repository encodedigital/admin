## Menu Requirements
### Pre-requisite
1. Code has to be in Codeigniter 4
2. Any CSS to be used is Tailwind CSS. You can you CDN version of Tailwind CSS for development.
3. For Javascript, use CDN VueJS if you know or use vanilla JavaScript. Do not use JQuery. If you don't know how to use CDN VueJS with CodeIgniter 4, then you can see this video - https://www.youtube.com/watch?v=GWNKTKZkvNI
   
Firstly I will cover things which are out of scope, so that you know what is not required. Below is the image of Wordpress Menu page which we trying to replicate in Codeigniter 4:

![alt text](https://i.imgur.com/adPHAu4.jpeg)

### Out Of Scope
1. You don't need to create side menu.
2. You don't need to create Screen Options or Help in top right corner of screen.
3. You don't need to create "Manage Locations" tab
4. You don't need to create "Manage with Live Preview" functionality

### In Scope
1. There should be functionality of "Create Menu" and dropdown to "Select Menu" exactly like wordpress. Functionality should work as it works in Wordpress.
2. I have attached screenshot of "Create Menu" and deleted part which is not required. For display location, you can use below array in your Controller and pass to Menu view

   ![alt text](https://i.imgur.com/IrHSuUh.jpeg)

```
$display_location = [
  ['name'  => 'Primary', 'key'  => 'primary'],
  ['name'  => 'Footer Left', 'key'  => 'footer_left'],
  ['name'  => 'Footer Middle', 'key'  => 'footer_middle'],
  ['name'  => 'Footer Right', 'key'  => 'footer_right']
];
```
3. Same like Wordpress, functionality should work for "Add to Menu". You don't need to display Most Recent, which I deleted in image below, but "View All" and "Search" should work. User should be able to multi select, and items should appear in tree structure (where applicable).
  
![alt text](https://i.imgur.com/u7GoLkf.jpeg)

![alt text](https://i.imgur.com/VMcnzNv.jpeg)

4. Menu Structure section should be exactly like Wordpress. User should be able to drag to create sub levels and it should show which type was it - like category, Product Category, Page, Post etc.

![alt text](https://i.imgur.com/4t7NLKc.jpeg)

5. User should be able to amend menu label as in Wordpress

![alt text](https://i.imgur.com/QB4utBQ.jpeg)

   
Some of the sample data which you can use is as below. Ask me more if I am missing any.

Data to show in list in "Add Menu items" section. For example for Product Categories
```
$product_categories = [
  'type'  => 'product_categories',
  'name'  => 'Product Categories',
  'data'  =>   [
  [
    'id'  => 1,
    'name'  => 'Technology',
    'link'  => 'https://example.com/category/technology',
    'sub_category'  =>  [
        [
        'id'  => 2,
        'name'  => 'Laptops',
        'link'  => 'https://example.com/category/technology/laptops'
        ],
        [
        'id'  => 3,
        'name'  => 'Watches',
        'link'  => 'https://example.com/category/technology/watches'
        ]
    ]
  ],
  [
    'id'  => 4,
    'name'  => 'Households',
    'link'  => 'https://example.com/category/households'
  ]
]
];
```

After adding the menu, save the outcome as below:

```
$menu = [
  'menu_location_key'  =>   'primary',
  'data'  =>  [
    [
      'type'  =>   'product_category',
      'id'    =>  1,
      'name'  =>  'Technology',
      'link'  =>  'https://example.com/category/technology'
      'sub_category'  =>  [
        [
          'type'  => 'page',
          'id'  => 22,
          'name'  => 'hot-offers-laptop',
          'link'  => 'https://example.com/pages/hot-offers-laptop'
        ],
        ]
    ],
    [
      'type'  =>   'custom_link',
      'id'    =>  null,
      'name'  =>  'Google',
      'link'  =>  'https://google.com'
    ]
  ]
];
```

I think that covers for now. Any question let me know.







































