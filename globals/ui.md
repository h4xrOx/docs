# Ui

Represented by `ui`.

* **`ui.new_checkbox(tab: string (menu tab), container: string (menu container), name: string (menu item))`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this control will be added.
	- **name**: The name of the checkbox.
	
	Returns a special value that can be passed to ui.get and ui.set, or throws an error on failure.
	

* **`ui.new_slider(tab: string (menu tab), container: string (menu container), name: string (menu item), min: number, max: number, init_value: number, show_tooltip: boolean, unit: string, scale: number, tooltips: table)`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this control will be added.
	- **name**: The name of the slider.
	- **min**: The minimum value that can be set using the slider.
	- **max**: The maximum value that can be set using the slider.
	- **init_value**: integer. The initial value. If not provided, the initial value will be min.
	- **show_tooltip**: boolean. true if the slider should display its current value.
	- **unit**: string that is two characters or less. This will be appended to the display value. For example, "px" for pixels or "%" for a percentage.
	- **scale**: The display value will be multiplied by this scale. For example, 0.1 will make a slider with the range [0-1800] show as 0.0-180.0 with one decimal place.
	- **tooltips**: table used to override the tooltip for the specified values. The key must be within min-max. The value is a string that will be shown instead of the numeric value whenever that value is selected.
	
	Returns a special value that can be passed to ui.get and ui.set, or throws an error on failure.
	

* **`ui.new_combobox(tab: string (menu tab), container: string (menu container), name: string (menu item), ...)`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this control will be added.
	- **name**: The name of the combobox.
	- **...**: One or more comma separated string values that will be added to the combobox. Alternatively, a table of strings that will be added.
	
	Returns a special value that can be passed to ui.get and ui.set, or throws an error on failure.
	

* **`ui.new_multiselect(tab: string (menu tab), container: string (menu container), name: string (menu item), ...)`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this control will be added.
	- **name**: The name of the multiselect.
	- **...**: One or more comma separated string values that will be added to the combobox. Alternatively, a table of strings that will be added.
	
	Returns a special value that can be passed to ui.get and ui.set, or throws an error on failure.
	

* **`ui.new_hotkey(tab: string (menu tab), container: string (menu container), name: string (menu item), inline: boolean)`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this control will be added.
	- **name**: The name of the hotkey.
	- **inline**: boolean. If set to true, the hotkey will be placed to the right of the preceding menu item.
	
	Returns a special value that can be passed to ui.get to see if the hotkey is pressed, or throws an error on failure.
	

* **`ui.new_button(tab: string (menu tab), container: string (menu container), name: string (menu item), callback: function)`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this checkbox will be added.
	- **name**: The name of the button.
	- **callback**: The lua function that will be called when the button is pressed.
	
	Throws an error on failure. The return value should not be used with ui.set or ui.get.
	

* **`ui.new_color_picker(tab: string (menu tab), container: string (menu container), name: string (menu item), r: number, g: number, b: number, a: number)`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this checkbox will be added.
	- **name**: The name of the color picker. This will not be shown, it is only used to identify this item in saved configs.
	- **r**: initial red value (0-255)
	- **g**: initial green value (0-255)
	- **b**: initial blue value (0-255)
	- **a**: initial alpha value (0-255)
	
	Throws an error on failure. The color picker is placed to the right of the previous menu item.
	

* **`ui.new_textbox(tab: string (menu tab), container: string (menu container))`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this textbox will be added.
	
	Throws an error on failure. Returns a special value that can be used with ui.get
	

* **`ui.reference(tab: string (menu tab), container: string (menu container), name: string (menu item))`**
	
	**Arguments:**
	
	- **tab**: The name of the tab: AA, RAGE, LEGIT, MISC, PLAYERS, SKINS, or VISUALS.
	- **container**: The name of the existing container to which this checkbox will be added.
	- **name**: The name of the menu item.
	
	Avoid calling this from inside a function. Returns a reference that can be passed to ui.get and ui.set, or throws an error on failure. This allows you to access a built-in pre-existing menu items. This function returns multiple values when the specified menu item is followed by unnamed menu items, for example a color picker or a hotkey.
	

* **`ui.set(item: number (menu reference), value: any, ...)`**
	
	**Arguments:**
	
	- **item**: The result of either ui.new_checkbox, ui.new_slider, or ui.reference.
	- **value**: The value to which the menu item will be set.
	- **...**: Optional. For multiselect comboboxes, you may want to set more than one option.
	
	For checkboxes, pass true or false. For a slider, pass a number that is within the slider's minimum/maximum values. For a combobox, pass a string value. For a multiselect combobox, pass zero or more strings. For referenced buttons, param is ignored and the button's callback is invoked. For color pickers, pass the arguments r, g, b, a.
	

* **`ui.get(item: number (menu reference))`**
	
	**Arguments:**
	
	- **item**: The special value returned by ui.new_checkbox, ui.new_slider, ui.new_combobox, ui.new_hotkey, or ui.reference.
	
	For a checkbox, returns true or false. For a slider, returns an integer. For a combobox, returns a string. For a multiselect combobox, returns an array of strings. For a hotkey, returns true if the hotkey is active. For a color picker, returns r, g, b, a. Throws an error on failure.
	

* **`ui.set_callback(item: number (custom menu reference), callback: function)`**
	
	**Arguments:**
	
	- **item**: The special value returned by ui.new_*. Do not try passing a reference to an existing menu item.
	- **callback**: Lua function that will be called when the menu item changes values. For example, this will be called when the user checks or unchecks a checkbox.
	

* **`ui.set_visible(item: number (menu reference), visible: boolean)`**
	
	**Arguments:**
	
	- **item**: A menu item reference.
	- **visible**: Boolean. Pass false to hide the control from the menu.
	

* **`ui.is_menu_open()`**
	
	Returns true if the menu is currently open.
	

* **`ui.mouse_position()`**
	
	Returns current mouse coordinates x, y
	