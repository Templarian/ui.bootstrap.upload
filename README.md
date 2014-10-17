# ui.bootstrap.upload

AngularJS Bootstrap UI Upload Button

## Usage

The examples below use the [show-errors](https://github.com/paulyoder/angular-bootstrap-show-errors) directive as it greatly reduces markup when validating forms.

### View

```html
<form name="name">
    <div class="form-group" show-errors>
        <label>Upload</label>
        <button name="avatar" class="btn btn-default" upload="/api/avatar" ng-model="profileForm.avatar" required>Import Avatar</button>
    </div>
</form>
```

### Controller

### Request

**Warning:** All files are sent to the endpoint as `file`. This is done so that `upload` can be used more easily in a `ng-repeat`. If someone figures out a better solution please submit an issue.

### Response

While anything can be sent for the success the error must be sent in the format shown below to properly be parsed into a valid form validation error.

#### Success

This will be assigned to the `ngModel` once it is returned from the server.


#### Error:

```json
{
    "errorCode": "invalidFile", // Must be camelcase for validation handling.
    "error": "Incorrect filetype sent to the server."
}
```
