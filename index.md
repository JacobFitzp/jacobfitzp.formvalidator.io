<h1>FormValidator</h1>

FormValidator is a powerful form validation library built with extensibility in-mind. Easily improve your forms by preventing erroneous data from being submitted, and provide meaningful error messages to users.

FormValidator comes with everything you need to get started, and it's easy to build upon our foundations to create your own validators and plugins.

## Basic Usage

FormValidator is extremely easy to use, see the basic example bellow:

```javascript
let validator = new FormValidator(document.getElementById('target-form'), {
    fields: {
        /* Field Name */
        username: {
            /* Validator Name */
            notEmpty: {
                /* Validator Params ... */
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
})
```

## Validators

FormValidator comes bundled with a range of validators to cover most use cases:

### notEmpty

Check if value is not empty.

### regexp

Check if value matches regexp.

<table>
    <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>regexp</td>
        <td>RegExp</td>
        <td>Regex to test against</td>
    </tr>
</table>

### stringLength

## Events

The following events are fired by the FormValidator library...

**<u>fv.field.invalid</u> :** Fired when invalid data is entered into a field.

**<u>fv.field.valid</u> :** Fired when valid data is entered into a field.

**<u>fv.form.invalid</u> :** Fired when the user attempts to submit an invalid form.

You can easily register an event listener by using the built-in `on` method:

```javascript
validator.on('{event name}', function (event) {
    /* Do something here... */
});
```

## FormValidator API

## Extending

FormValidator is highly extensible, allowing you to add your own validators, as well as custom functionality (via the plugin interface).

### Validators

Custom validators can be created by extending the Validator interface:

```javascript
export default class CustomValidator implements Validator
{
    /* If set to true will break the sequence when it encounters erroneous data. */
    breakSequence = true;

    check(value: string, params: object): boolean {
        return value === 'Expected Value';
    }
}
```

You will then need to register the new validator so the FormValidator library is aware of it, this can easily be done using the ValidatorManager:

```javascript
ValidatorManager.registerValidator('customValidator', new CustomValidator());
```

### Plugins
