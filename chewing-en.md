# English 
## Advantages over the default OSK:
-	Function, modifier, tab, and arrow key support
-	Ability to move around the screen
-	More compact layout

## Requirements
- GNOME 43 or above
- Wayland (X11 is not working properly)
- ```ibus-chdwing``` or ```fcitx5``` or other 注音 input method installed

## Install
1. Confirm that you have [Extension Manager](https://github.com/mjakeman/extension-manager) installed.
2. Install [https://extensions.gnome.org/extension/5949/gjs-osk/](https://extensions.gnome.org/extension/5949/gjs-osk/)
3. Install [Block Caribou 36](https://extensions.gnome.org/extension/3222/block-caribou-36/) to block default GNOME OSK.
4. Make sure that QWERTY is the selected language.
    ![image](https://github.com/proton-penguin/gjs-osk-chewing/assets/142492829/1c4ff63c-bf76-44e4-aaa3-05d1ada95b0d)
5. run the command to enable Chewing layout
   ```bash
   cd ~
   git clone https://github.com/proton-penguin/gjs-osk-chewing.git
   rm ~/.local/share/gnome-shell/extensions/gjsosk@vishram1123.com/keycodes.json
   cp ~/gjs-osk-chewing/gjsosk@vishram1123.com/keycodes.json ~/.local/share/gnome-shell/extensions/gjsosk@vishram1123.com/keycodes.json
   rm -r ~/gjs-osk-chewing/
   ```
6. To restore, you can reinstall GJS OSK from Extension Manager. 

## Usage
- To drag the keyboard around, click on the move icon in the bottom right, then drag the keyboard around the screen. To get the full keyboard back, press the move icon again.
  - The keyboard will snap to the corners, edges, and center of the screen.
- To change properties about the keyboard, open up the "Extensions" application, and click on "Settings" under this extension to get a list of changeable properties
  - Close the settings dialog to save any modified settings
- To type special characters, open GNOME settings, and turn on "Compose Key" under the Keyboard submenu. Choose a modifier (preferably right alt), and use the [key combinations listed here](https://en.wikipedia.org/wiki/Compose_key#Common_compose_combinations) to type special characters
- To change the keyboard layout, change the layout in GJS OSK's settings
- To add typing prediction, add "Typing Booster" as an input source (in GNOME's settings), and keep it chosen as the primary input source [(extended guide here)](https://mike-fabian.github.io/ibus-typing-booster/docs/user/).
  - Note that this will cause predictive text to be present even without the OSK open, and the input language for Typing Booster's predictions will have to be set in Typing Booster's settings 
- To open the keyboard from the command line (or with a shortcut), run the command ```dconf write /org/gnome/shell/extensions/gjsoskindicator/opened true``` which will open the keyboard 


## Demo
[Chinese_Demo.webm](https://github.com/proton-penguin/gjs-osk-chewing/assets/142492829/5986bebe-2387-4999-9e71-84559d133729)

[Keyboard Demo.webm](https://user-images.githubusercontent.com/64966832/210458851-1b91adba-f6e4-4d40-b0d5-dba2c46cc354.webm)

[Settings Demo.webm](https://user-images.githubusercontent.com/64966832/210458854-eb458311-3d3f-4edb-93df-f5b8334d4cbc.webm)


## Known Problems/Issues and Intended Features (Would appreciate solutions about how to fix):
- 100% width or height doesn't take up the full monitor width or height (minus 25 px on either side). Instead, it is 1 or 2 px smaller, depending on the monitor size
- Even though the keyboard displays over system modals, it isn't interactable

## Help
- If you find any bugs, or if you have any suggestions, please open an issue or submit a pull request. Thanks!

### Keyboard Layouts
- If you wish to add a keyboard layout, edit the "keycodes.json" file as follows: 
  - If a letter behaves the same if caps lock or shift is turned on, add a `"letter": "primary"` key-value pair to the object pertaining to the character
  - If a letter simply turns uppercase on caps lock, but is a completely different character on shift, add a `"letter": "pseudo"` key-value pair to the object pertaining to the character
  - If a letter is not affected by caps lock, don't add a `"letter"` key to the object
  - If a letter changes to another on alt, change `"altName": ""` such that its value represents the output of the character if it is pressed along with alt
  - Keys have to follow a general QWERTY shape (though more or less keys can be on a single line), as this is how the keyboard is coded
- Once "keycodes.json" is modified, add the layout name to the array `langList` in prefs.js, and on the arrays in line 40 and 59 in extension.js

**Help in this area is greatly appreciated!**

