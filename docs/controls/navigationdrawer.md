---
title: NavigationDrawer
sidebar_label: NavigationDrawer
slug: navigationdrawer
---

Material Design Navigation Drawer component.

Navigation Drawer is a panel that slides in horizontally from the left or right edge of a page to show primary destinations in an app. To add NavigationDrawer to the page, use [`page.drawer`](page#drawer) and [`page.end_drawer`](page#end_drawer) properties. Similarly, the NavigationDrawer can be added to a [`View`](view#drawer). To display the drawer, set its `open` property to `True`.

## Examples

[Live example](https://flet-controls-gallery.fly.dev/navigation/navigationdrawer)

### NavigationDrawer sliding from the left edge of a page

<img src="/img/docs/controls/navigationdrawer/navigation-drawer-start.gif" className="screenshot-60"/>

```python
import flet as ft


def main(page: ft.Page):
    page.drawer = ft.NavigationDrawer(
        controls=[
            ft.Container(height=12),
            ft.NavigationDrawerDestination(
                label="Item 1",
                icon=ft.icons.DOOR_BACK_DOOR_OUTLINED,
                selected_icon_content=ft.Icon(ft.icons.DOOR_BACK_DOOR),
            ),
            ft.Divider(thickness=2),
            ft.NavigationDrawerDestination(
                icon_content=ft.Icon(ft.icons.MAIL_OUTLINED),
                label="Item 2",
                selected_icon=ft.icons.MAIL,
            ),
            ft.NavigationDrawerDestination(
                icon_content=ft.Icon(ft.icons.PHONE_OUTLINED),
                label="Item 3",
                selected_icon=ft.icons.PHONE,
            ),
        ],
    )

    def show_drawer(e):
        page.drawer.open = True
        page.drawer.update()

    page.add(ft.ElevatedButton("Show drawer", on_click=show_drawer))


ft.app(main)
```

### NavigationDrawer sliding from the right edge of a page

<img src="/img/docs/controls/navigationdrawer/navigation-drawer-end.gif" className="screenshot-60"/>

```python
import flet as ft


def main(page: ft.Page):
    def end_drawer_dismissed(e):
        print("End drawer dismissed!")

    end_drawer = ft.NavigationDrawer(
        on_dismiss=end_drawer_dismissed,
        controls=[
            ft.NavigationDrawerDestination(
                icon=ft.icons.ADD_TO_HOME_SCREEN_SHARP, label="Item 1"
            ),
            ft.NavigationDrawerDestination(icon=ft.icons.ADD_COMMENT, label="Item 2"),
        ],
    )

    def show_end_drawer(e):
        page.show_end_drawer(end_drawer)

    page.add(ft.ElevatedButton("Show end drawer", on_click=show_end_drawer))


ft.app(main)
```

## `NavigationDrawer` properties

### `bgcolor`

The [color](/docs/guides/python/colors) of the NavigationDrawer itself.

### `controls`

Defines the appearance of the items within the navigation drawer.

The list contains `NavigationDrawerDestination` items and/or other controls such as headlines and dividers.

### `elevation`

The elevation of the NavigationDrawer itself.

### `indicator_color`

The [color](/docs/guides/python/colors) of the selected destination indicator.

### `indicator_shape`

The shape of the selected destination indicator. See [button style example](elevatedbutton#style) for possible values.

### `selected_index`

The index for the current selected `NavigationDrawerDestination` or null if no destination is selected.

A valid selected_index is an integer between 0 and number of destinations - 1. For an invalid `selected_index`, for example, `-1`, all destinations will appear unselected.

### `shadow_color`

The [color](/docs/guides/python/colors) used for the drop shadow to indicate `elevation`.

### `surface_tint_color`

The surface tint of the Material that holds the NavigationDrawer's contents.

### `tile_padding`

Defines the padding for `NavigationDrawerDestination` controls.

## `NavigationDrawer` events

### `on_change`

Fires when selected destination changed.

### `on_dismiss`

Fires when NavigationDrawer is dismissed by clicking outside of the panel or [programmatically](page#close_drawer).

## `NavigationDrawerDestination` properties

### `icon`

The name of the icon of the destination.

### `icon_content`

The icon `Control` of the destination. Typically the icon is an [`Icon`](icon) control. Used instead of `icon` property.

If `selected_icon_content` is provided, this will only be displayed when the destination is not selected.

To make the NavigationDrawer more accessible, consider choosing an icon with a stroked and filled version, such as `icons.CLOUD` and `icons.CLOUD_QUEUE`. The icon should be set to the stroked version and `selected_icon` to the filled version.

### `label`

The text label that appears below the icon of this `NavigationDrawerDestination`.

### `open`

Set to `True` to display a NavigationDrawer.

### `selected_icon`

The name of alternative icon displayed when this destination is selected.

### `selected_icon_content`

An alternative icon `Control` displayed when this destination is selected.

If this icon is not provided, the NavigationDrawer will display `icon_content` in either state.