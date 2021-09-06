# OLEX

Open Lead Exchange Protocol.

By William Estoque

## Objectives

OLEX is a specification for transferring leads in the internet. OLEX has 3 goals:

- Simple (by having 1 standard mapping that is no longer than 3 levels)
- Easily Transferrable (just follow standard fields in JSON spec)
- Extensible (extra fields could be added for different purposes, insurance, real estate, etc)

This protocol supports leads with as simple as 1 contact to as complex as 1 contact with multiple members
including vehicles, residences and insurance quotes.

## Simple Format

The only fields required for a lead is:

- mainContact
- source
- createdAt
- updatedAt

```
{
  mainContact: <Contact> // required
  members: [<Contact>]
  vehicles: [<Vehicle>],
  residences: [Residence],
  dnc: true,
  source: "facebook",
  tags: [],
  createdAt: "", <----- required to tell how old the lead is
  updatedAt: ""  <----- required to know if the lead has been updated by provider since
}
```

### Contact

The contact model

```
{
  fistName: "Foo",                // optional
  middleName: "",                 // optional
  lastName: "Bar",                // optional
  email: "foo@bar.com",           // required
  phoneNumber: "222-333-5555",    // required (phoneNumber OR mobileNumber)
  mobileNumber: "444-555-8888"    // required (phoneNumber OR mobileNumber)
}
```

### Vehicle

The vehicle model

```
{
  year: "",
  vehicle: "",
  make: "",
  model: "",
  vin: ""
}
```

### Residence

```
{
  address1: "",
  address2: "",
  city: "",
  state: "",
  zipcode: ""

  // extensions
  sqFootage: "",
  beds: "",
  baths: ""
}
```

## Example

The simplest example:

```
{
  mainContact: {
    email: "foo@bar.com"
  },
  source: "linkedin"
  createdAt: "2021-09-06T00:47:48.534Z"
  updatedAt: "2021-09-06T00:47:48.534Z"
}
```


## Extensions

OLEX can be extended for Insurance, Real Estate, or others.

#### Insurance

```
{
  firstName: "",
  lastName: "",
  ...
  vehicle_quotes: {}
  residence_quotes: {}
  life_quotes: {}
  specialty_quotes: {}
}
```
