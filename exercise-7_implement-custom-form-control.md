# Exercise: Custom Form Controls


## Tasks

1. Create a new component `AddressInputComponent` by running `ng g c address-input`
2. Move the address fields template from `ContactsCreatorComponent` to `AddressInputComponent` template

  ```
  <fieldset [formGroup]="form" fxLayout="column">
    <legend>Address</legend>
    <md-input-container fxFlex>
      <input mdInput placeholder="Street" formControlName="street">
    </md-input-container>
    <md-input-container fxFlex>
      <input mdInput placeholder="Zip" formControlName="zip">
    </md-input-container>
    <md-input-container fxFlex>
      <input mdInput placeholder="City" formControlName="city">
    </md-input-container>
    <md-select placeholder="Country" formControlName="country">
      <md-option *ngFor="let country of countries" [value]="country.name">{{ country.name }}</md-option>
    </md-select>
  </fieldset>
  ```

3. Create a new form group in `AddressInputComponent` accordingly
4. Import `ControlValueAccessor` from `@angular/forms`
5. Make `AddressInputComponent` implement `ControlValueAccessor`
6. Implement `writeValue(address: Address)`
7. Implement `registerOnChange(fn)`
8. Implement `registerOnTouched(fn)`
9. Make sure the onchange handler is called whenever the value of the form group changes (hint: you can use `this.form.valueChanges.subscribe(...)` for that
10. Make sure ontouch handler is called whenever any of the form controls within `AddressInputComponent`'s template emit a `blur` event
11. Use `<trm-address-input>` in `ContactsCreatorComponent` and `ContactsEditorComponent`
