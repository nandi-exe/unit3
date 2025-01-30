# Quiz 38

##Instructions

<img width="973" alt="image" src="https://github.com/user-attachments/assets/7589da68-e7f3-4e90-bb97-bebdd3057dbe" />

## Code
```
from kivymd.app import MDApp
from kivymd.uix.screen import MDScreen

class MysteryPageA(MDScreen):
    def go_to_b(self):
        self.parent.current = "MysteryPageB"

class MysteryPageB(MDScreen):
    def go_to_a(self):
        self.parent.current = "MysteryPageA"

class Mystery(MDApp):
    def build(self):
        return

attempt = Mystery()
attempt.run()

```
## KivyMD
```
ScreenManager:
    id: scr_manager


    MysteryPageA:
        name: "MysteryPageA"

    MysteryPageB:
        name: "MysteryPageB"

<MysteryPageA>
    BoxLayout:
        orientation: "vertical"
        padding: dp(30)
        spacing: dp(4)

        MDLabel:
            text: "Welcome to Mystery Page B"
            halign: "center"
            font_size: "40sp"

        MDRaisedButton:
            size_hint: None
            font_size: "20sp"
            text: "Go to Mystery Page B"
            pos_hint: {"centre_x":.5, "center_y":.5}
            mg_bg_color: "#FEA500"
            on_press: root.go_to_b()

<MysteryPageB>
    BoxLayout:
        orientation: "vertical"
        padding: dp(30)
        spacing: dp(4)

        MDLabel:
            halign: "center"
            text: "Welcome to Mystery Page B"
            font_size: "40sp"

        MDRaisedButton:
            text: "Go to Mystery Page A"
            font_size: "20sp"
            size_hint: None
            pos_hint: {"center_x":.5, "center_y":.5}
            mg_bg_color: "#FEA500"
            on_press: root.go_to_a()

```
## Proof of Work
