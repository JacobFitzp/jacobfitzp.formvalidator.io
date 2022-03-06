## FormValidator

### Basic Usage

```javascript

let validator = new FormValidator(document.getElementById('target-form'), {
            fields: {
                username: {
                    notEmpty: {
                        message: 'Username is required'
					},
					stringLength: {
                        message: 'Username must be between 5 and 32 characters long',
						min: 5,
						max: 32
					}
				},
				email_address: {
                    notEmpty: {
                        message: 'Email address is required'
					},
					emailAddress: {
                        message: 'Email address is not valid'
					}
				},
				password: {
                    notEmpty: {
                        message: 'Password is required'
					},
					stringLength: {
                        message: 'Password must be between 8 and 64 characters long',
                        min: 8,
						max: 64
					},
					passwordStrength: {
                        mode: 'STRICT',
						message: 'Password is too easy to guess, please choose something stronger'
					}
				},
				confirm_password: {
                    matchesField: {
                        target: 'password',
						message: 'Passwords don\'t match'
					}
				}
			}
		});

```

### Validators

### Events

### FormValidator API

### Extending

#### Validators

#### Plugins
