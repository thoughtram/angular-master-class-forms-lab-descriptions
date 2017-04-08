# Exercise: FormArray for dynamic forms

Angular comes with another from control type `FormArray` that let us, similar to `FormGroup`, create groups of `FormControl`, however, the number of controls isn't static. This enables us to build form UIs where form controls can be added to the form at runtime.

Let's enhance our `ContactsCreatorComponent` to have multiple form controls for a contact phone numbers.

## Tasks

1. Replace the `phone` form control markup with the following template:

```
  <div formArrayName="phone">
    <div *ngFor="ITERATE_OVER_PHONE_CONTROLS_HERE">
      <md-input-container>
        <input mdInput placeholder="Phone">
      </md-input-container>
      <button md-icon-button type="button" *ngIf="i >= 1" (click)="removePhoneField(i)"><md-icon>highlight_off</md-icon></button>
      <button md-icon-button type="button" *ngIf="l && phone.value != ''" (click)="addPhoneField()"><md-icon>add_circle_outline</md-icon></button>
    </div>
  </div>
```
2. Change `phone` field in `ContactsCreatorComponent` to `FormArray` using `FormBuilder` APIs
3. Add a `removePhoneField(i)` method to `ContactsCreatorComponent` that removes a phone form control from the list by given index
4. Add a `addPhoneField()` method to `ContactsCreatorComponent` that adds a new control to the form control collection

## Bonus Tasks

1. Can you implement the same functionality in `ContactsEditorComponent`?

