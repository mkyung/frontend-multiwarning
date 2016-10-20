## API References

### Frontend

1. **Multiwarning.version**	
	Returns the semantic version number
	1. **new Multiwarning({options})**
	1. `options.scrollToTop (boolean, default=true)`		Scroll the page to top when validation finishes
			1. `options.disableCaller (boolean, default=true)`		Disable the caller HTML button when validation in progress
			1. `options.disabledCallerText (string, default=“Validating”)`

		Change the text of the caller when disabled. Original text will be restored upon finish of validation
			1. `*options.endpointURL (string, default=null)`		
		URL to validate the form
				1. URL parameter `ruleFilePath`			vRule file Path
					1. URL parameter `formBeanName`

			The name of the form bean that needs to be cast into	1. `*options.form (jQuery object, default=null)`		
		A jQuery-wrapped object of the form element, e.g. `$(form1)`
			1. `options.removeSyskeyToken (boolean, default=true)`
		Remove syskey field in the form when submitted to validation – necessary to prevent duplicated page submission error
			1. `options.onValidationPass (function, default=$.noop)`
		A callback function when the validation passes
			1. `options.onValidationEnd (function, default=$.noop)`
		A callback function when the validation ends
			1. `options.page (jQuery object, default=...)`
		A jQuery object on the page to which the Multiwarning container attach to
	1. `options.containerSelector (string, default=“#warning-container”)`
		A CSS selector to the sub-container for warnings to append in the template	1. `options.template (jQuery object, default=...)`
		Template to display warnings
		1. **new Multiwarning()**
	1. `.validate(caller context)`
		- Disable the caller if “this” supplied
		- Validate the form using ajax		- Execute callbacks			- On Validation Passes			- On Validation Ends

				1. `.clone({options})`		
		Clone the multiwarning instance with *new options* overwriting the old options
		
1. **Endpoint return format**

	~~~json
	[{
		"errorMessage": "...",
		"xPath": "",
		"errorType": "",
		"errorCode": "MSG_100000306",
		"errorLevel": "W"
	 },{
	 	...
	}]
	~~~
