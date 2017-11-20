# Exercise: Add custom email validator

## Scenario

Write your first custom validator.

The email field is optional, which is okay. However, we're able to enter whatever we want. Let's make sure the entered value is an actual email address.

## Tasks

1. Create a new directive using angular-cli `ng generate directive -m app email-validator`
2. Import `FormControl` from `@angular/forms` in that file
2. Write a stand-alone **function** `validateEmail(c: FormControl)` that uses a regular expression to test the value of the given control.
  - The Regexp is: 
  ```js 
  var VALID_EMAIL = /^[a-z0-9!#$%&'*+\/=?^_`{|}~.-]+@[a-z0-9]([a-z0-9-]*[a-z0-9])?(\.[a-z0-9]([a-z0-9-]*[a-z0-9])?)*$/i;
  ```
3. Use `.test()` on the regexp to check if control value is an email address
4. In case of an error, return an object that looks like this:

  ```js
  {
    validateEmail: {
      valid: false
    }
  }
  ```

3. Change `EmailValidator` directive's selector to `[trmValidateEmail][ngModel]`
4. Add the new validator to the `NG_VALIDATORS` multi provider
5. Add `EmailValidator` to the ngModule **`declarations`** in `app.modules.ts` (probably already one by angular cli)
6. Apply `trmValidateEmail` directive on email input control
7. Set `<md-input-container>`'s `dividerColor` property to either "warn" or "primary" depending on if the field has errors or not
8. Add an `<md-hint>` element to into the `<md-input-container>` if the field is not `valid` and not `pristine`. Here's a snippet:

  ```
  <input md-input #email="ngModel" ...>
  <md-hint align="end" *ngIf="!email.valid && !email.pristine">
    <!-- Error messages go here -->
  </md-hint>
  ```

## Bonus Tasks

1. Apply the same validator in the `ContactsEditorComponent` as well
