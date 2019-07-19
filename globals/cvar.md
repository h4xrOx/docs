# Cvar

Represented by `cvar`.

* **`cvar.set_string(value: string)`**
	
	**Arguments:**
	
	- **value**: String value
	

* **`cvar.get_string()`**
	
	Returns nil on failure.
	

* **`cvar.set_float(value: number (float))`**
	
	**Arguments:**
	
	- **value**: Float value
	

* **`cvar.set_raw_float(value: number (float))`**
	
	**Arguments:**
	
	- **value**: Float value
	
	This sets the float value without changing the integer and string values.
	

* **`cvar.get_float()`**
	
	Returns nil if called on a ConCommand.
	

* **`cvar.set_int(value: number (integer))`**
	
	**Arguments:**
	
	- **value**: Integer value
	

* **`cvar.set_raw_int(value: number (integer))`**
	
	**Arguments:**
	
	- **value**: Integer value
	
	This sets the integer value without changing the float and string values.
	

* **`cvar.get_int()`**
	
	Returns nil if called on a ConCommand.
	

* **`cvar.invoke_callback()`**
	