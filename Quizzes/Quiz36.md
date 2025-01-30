# Quiz 36

## Kivy File
```
Screen:
    size: 450, 400

    MDLabel:
        id: my_label
        text: "Your Name"
        theme_text_color: "Custom"
        halign: "center"
        font_size: "28sp" 

    MDRaisedButton:
        id: button_a
        text: "Press Here"
        size_hint: 0.3, 0.3
        font_size: "38sp"
        text_color: "#40E0D1"
        md_bg_color: "#f07164"
        pos_hint: {"center_x": 0.5}

        on_press:
            app.change_label()
```

## Code

```
from kivymd.app import MDApp

class quiz036(MDApp):
    def build(self):
        self.theme = "white"
        return

    def change_label(self):
        if self.theme == 'white':
            self.root.ids.my_label.text_color = '#ffffff'
            self.root.ids.my_label.md_bg_color = '#000000'
            self.root.ids.button_a.md_bg_color = '#40E0D1'
            self.root.ids.button_a.text_color = '#f07164'  
            self.theme = 'black'
        else:
            self.root.ids.my_label.text_color = '#000000'
            self.root.ids.my_label.md_bg_color = '#ffffff'
            self.root.ids.button_a.md_bg_color = '#f07164'
            self.root.ids.button_a.text_color = '#40E0D1'
            self.theme = 'white'

test = quiz036()
test.run()
```

## Proof of Work

https://github.com/user-attachments/assets/3eff54f9-6f33-4d3f-8548-e43c7278a312

