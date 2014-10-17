# upload

AngularJS Bootstrap UI Upload button for uploading through a single button click.

## Usage

Add a reference to `upload.js`. In your app config add `ui.bootstrap.upload` as a dependency module. Copy and paste `btn-file.css` contents into your own CSS file or include it.

The examples below use the [show-errors](https://github.com/paulyoder/angular-bootstrap-show-errors) directive as it greatly reduces markup when validating forms.

### View

```html
<form name="form">
    <div class="form-group" show-errors>
        <label>Upload</label>
        <button name="avatar" class="btn btn-default" upload="/api/avatar" ng-model="profileForm.avatar" required>Import Avatar</button>
    </div>
    <div ng-messages="form.avatar.$error">
        <div class="alert alert-danger" ng-message="invalidFile">Incorrect file type.</div>
        <div class="alert alert-danger" ng-message="otherError">Another errorCode.</div>
    </div>
</form>
```

### Controller

```js
$scope.profileForm = {
    avatar: null
};
```

### Request

**Warning:** All files are sent to the endpoint as `file`. This is done so that `upload` can be used more easily in a `ng-repeat`. If someone figures out a better solution please submit an issue.

### Response

While anything can be sent for the success the error must be sent in the format shown below to properly be parsed into a valid form validation error.

#### Success

This will be assigned to the `ngModel` once it is returned from the server.


#### Error:

The `errorCode` must be camelcase for validation handling. The `error` field is __optional__.

```json
{
    "errorCode": "invalidFile",
    "error": "Incorrect filetype sent to the server."
}
```
