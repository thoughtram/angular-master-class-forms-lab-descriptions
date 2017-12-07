# Exercise: Template validators and error messages

In this exercise we add validation and error messages to prevent adding contacts without a name.

## Scenario

We don't have any validations in our new form. Let's use the built-in `required` and `minlength` validator to have some validation and display appropriate error messages.

## Tasks

1. Add the `novalidate` HTML5 attribute to the form, so the browser's default validation is turned off
1. Disable `ContactCreatorComponent`'s save button using the forms validity state
2. Set `<mat-input-container>`'s `dividerColor` property to either "warn" or "primary" depending on if the field has errors or not
3. Add `required` and `minlength="3"` validator to the input control
4. Add an `<mat-hint>` element to into the `<mat-input-container>` if the field is not `valid` and not `pristine`. Here's a snippet:

  ```
  <input matInput #name="ngModel" ...>
  <mat-hint align="end" *ngIf="!name.valid && !name.pristine">
    <!-- Error messages go here -->
  </mat-hint>
  ```
4. Display error message inside the `<mat-hint>` element using `ngIf` for both `required` and `minlength`
5. Add information about `minlength` error in error message (`actualLength`)

## Bonus Tasks

1. Refactor `ContactsEditorComponent` to also use template-driven forms and the same validation (keep in mind that one button is of type `submit` whereas the other one is of type `button`.

### Additional resources and help


## Next Lab

Go to **Forms Lab #3**: [Add Custom eMail Validator](https://github.com/thoughtram/angular2-master-class-exercise-descriptions/blob/master/exercises/forms/exercise-3_add-custom-email-validator.md)
