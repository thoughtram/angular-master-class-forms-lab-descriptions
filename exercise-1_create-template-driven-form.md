# Exercise: Create template-driven form

In this exercise we're going to build a template-driven form to add a new contact to our contacts list using Angular form directives.

## Scenario

We can list and edit our contacts, but we don't have a way to add new ones. That's why we want to create a new form component that enables us to do that.

## Tasks

1. Create a new component **ContactsCreatorComponent** using angular-cli

    ```
    $ ng generate component contacts-creator
    ```
    or

    ```
    $ ng g c contacts-creator
    ```
2. Render a form to add a new contact using the following HTML:

  ```html
  <div class="trm-contacts-creator">
    <form>
      <md-card>
        <md-card-title-group>
          <img md-card-md-image alt="Placeholder image" src="/assets/images/placeholder.png">
          <md-card-title></md-card-title>
          <md-card-subtitle></md-card-subtitle>
        </md-card-title-group>
        <md-card-content>
          <div fxLayout="column">
            <md-input-container fxFlex>
              <input mdInput placeholder="Name" name="name">
            </md-input-container>
            <md-input-container fxFlex>
              <input mdInput placeholder="Email" name="email">
            </md-input-container>
            <md-input-container fxFlex>
              <input mdInput placeholder="Birthday" name="birthday" type="date">
            </md-input-container>
            <md-input-container fxFlex>
              <input mdInput placeholder="Phone" name="phone">
            </md-input-container>
            <md-input-container fxFlex>
              <input mdInput placeholder="Website" name="website">
            </md-input-container>
            <md-radio-group name="gender">
              <md-radio-button *ngFor="let variant of gender" [value]="variant">
              {{variant}}
              </md-radio-button>
            </md-radio-group>
            <fieldset fxLayout="column">
              <legend>Address</legend>
              <md-input-container fxFlex>
                <input mdInput placeholder="Street" name="street">
              </md-input-container>
              <md-input-container fxFlex>
                <input mdInput placeholder="Zip" name="zip">
              </md-input-container>
              <md-input-container fxFlex>
                <input mdInput placeholder="City" name="city">
              </md-input-container>
            <md-select placeholder="Country" name="country">
              <md-option *ngFor="let country of countries" [value]="country.name">{{ country.name }}</md-option>
            </md-select>
            </fieldset>
          </div>
        </md-card-content>
        <md-card-actions fxLayout fxLayoutAlign="center center">
          <button md-button type="submit">Save</button>
          <a md-button title="Cancel creating new contact">Cancel</a>
        </md-card-actions>
      </md-card>
    </form>
  </div>
  ```

3. 

Use this code for the ContactsCreator component:

```js
import { Component } from '@angular/core';
import { Router } from '@angular/router';
import { ContactsService } from '../contacts.service';
import { Contact } from '../models/contact';
import { COUNTRIES_DATA } from '../data/countries-data';
import { GENDER } from '../data/gender';

@Component({
  selector: 'contacts-creator',
  templateUrl: './contacts-creator.component.html',
  styleUrls: ['./contacts-creator.component.css'],
})
export class ContactsCreatorComponent {

  countries = COUNTRIES_DATA;
  gender = GENDER;

  constructor(private router: Router, private contactsService: ContactsService) {}

  save(value: Contact) {
    this.contactsService.addContact(value)
      .subscribe(() => this.router.navigate(['/']));
  }
}
```
  
4. Add a new route configuration that loads `ContactsCreatorComponent` with the path `contact/new` (**keep in mind that it has to be defined before `contact/:id` route**)
5. Append the following HTML to the `ContactsList` template, to create a button that links to `ContactsCreatorComponent`:

  ```html
  <a md-fab routerLink="contact/new" title="Add a new contact" class="trm-floating-button">
    <md-icon class="md-24">add</md-icon>
  </a>
  ```

6. Add a new method `addContact(contact: Contact)` to **ContactsService** that performs and http POST request to `http://localhost:4201/api/contacts` with a new contact data object that is passed to this method (you can use `updateContact()` as inspiration).
7. Add `ngModel` and `ngModelGroup` to **ContactsCreatorComponent**s template accordingly to submit an object structure on save that looks like this:

  ```js
  {
    name: '',
    email: '',
    phone: '',
    birthday: '',
    website: '',
    address: {
      street: '',
      zip: '',
      city: '',
    }
  }
  ```

8. Get an `ngForm` reference (`#form="ngForm"`) in the template and use it's value property to submit data on save (`(ngSubmit)="save(form.value)"`).
9. Add a new method `save(contact)` to  **ContactsCreatorComponent** that calls `ContactsService#addContact()` with the given contact, and navigates to **ContactsListComponent**, once the method returns.

### Additional resources and help

- [Template-driven Forms in Angular](http://blog.thoughtram.io/angular/2016/03/21/template-driven-forms-in-angular-2.html)


## Next Lab

Go to [Forms Lab #2: Template Validators & Error Messages](https://github.com/thoughtram/angular2-master-class-exercise-descriptions/blob/master/exercises/forms/exercise-2_template-validators-and-error-messages.md)

