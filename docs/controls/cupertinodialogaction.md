---
title: CupertinoDialogAction
sidebar_label: CupertinoDialogAction
slug: cupertinodialogaction
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

A button typically used in a [CupertinoAlertDialog](/docs/controls/cupertinoalertdialog).

## Examples

[Live example](https://flet-controls-gallery.fly.dev/buttons/cupertinoalertdialog)

### CupertinoAlertDialog example

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft


def main(page: ft.Page):
    def dialog_dismissed(e):
        print("Dismissed!")

    cupertino_alert_dialog = ft.CupertinoAlertDialog(
        title=ft.Text("Cupertino Alert Dialog"),
        content=ft.Text("Do you want to delete this file?"),
        on_dismiss=dialog_dismissed,
        actions=[
            ft.CupertinoDialogAction(
                "OK",
                is_destructive_action=True,
            ),
            ft.CupertinoDialogAction(text="Cancel"),
        ],
    )

    def open_cupertino_dialog(e):
        page.dialog = cupertino_alert_dialog
        cupertino_alert_dialog.open = True
        page.update()

    page.add(
        ft.OutlinedButton("Open Cupertino Dialog", on_click=open_cupertino_dialog),
    )


ft.app(target=main)
```
  </TabItem>

</Tabs>

<img src="/img/docs/controls/cupertinodialogaction/cupertinoalertdialog.png" className="screenshot-50" />

## Properties

### `content`

A Control representing custom button content.

### `is_default_action`

If set to True, the button will have bold text. More than one action can have this property set to True in CupertinoAlertDialog. The default value is False.

### `is_destructive_action`

If set to True, the button's text color will be red. Use it for actions that destroy objects, such as an delete that deletes an email etc. The default value is False.

### `text`

The text displayed on a button.

### `text_style`

The text style to use for text on the button. See [`text_style` properties](text#textstyle-properties) for possible values.

## Events

### `on_click`

Fires when a user clicks the button.