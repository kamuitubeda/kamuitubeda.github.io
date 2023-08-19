---
title: "Custom Menu Laravel Voyager"
subtitle: ""
date: 2023-08-19T13:25:57+07:00
date: 2023-08-19T13:25:57+07:00
draft: false
authors: []
description: ""

tags: []
categories: []
series: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---
The Voyager menu function is optimized for menus named 'admin', ensuring proper functionality like generating links. If you create a custom menu with a different name, hrefs might not work correctly. To overcome this, manipulate the JSON return value from `menu('admin', '_json')` for custom menus. This provides flexibility to create accurate hrefs and resolve any issues. Check [this GitHub issue (#5113)](https://github.com/the-control-group/voyager/issues/5113) for more insights.

So, instead of using default menu name like this:

```
<admin-menu :items="{{ menu('upt-menu', '_json') }}"></admin-menu>
```

We should implement custom code like this:

```
<div id="adminmenu">
    @if(Auth::user()->hasRole('admin'))
        <!-- Default Voyager Admin Menu -->
        <admin-menu :items="{{ menu('admin', '_json') }}"></admin-menu>
    @else
        <!-- Custom Menu for Role: UPT -->
        @php
            $items = menu('upt-menu', '_json');
        @endphp
        <ul class="nav navbar-nav">
            @foreach($items as $menu_item)
                <li class="">
                    <a target="_self" href="{{ $menu_item->link() }}">
                        <span class="icon {{ $menu_item->icon_class }}"></span>
                        <span class="title">{{ $menu_item->title }}</span>
                    </a>
                </li>
            @endforeach
        </ul>
    @endif
</div>

```

This code snippet demonstrates how to integrate custom menus into a Voyager Admin Panel layout. It checks the user's role, and if the user has the 'admin' role, it displays the default Voyager Admin Menu using the `admin-menu` component. If the user doesn't have the 'admin' role, it retrieves and displays a custom menu named 'upt-menu'. The code iterates through the menu items, generating accurate links, icons, and titles for each menu item.

Remember to adjust the role names ('admin' and 'upt-menu') and customize the HTML structure to match your application's specific requirements. This example showcases an effective approach to handling custom menus and ensuring proper functionality for different user roles.