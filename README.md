# OLEX

Open Lead Exchange

By William Estoque

## Objectives

OLEX is a specification for transferring leads in the internet. OLEX has 3 goals:

**Simple**

By having an efficient standard mapping, we can capture a wealth of information
using just 1 JSON object.

**Transferrable**

It should be easy to transfer leads to and from
different services providers. You can even capture data from a page and convert
it to an OLEX formatted JSON and send it anywhere.

**Extensible**

Extra fields could be added for different purposes,
insurance, real estate, etc.

This specification supports leads as simple as one contact to something as complex as one
contact with multiple members including vehicles, residences and insurance quotes.

In addition, multiple parsers and scrapers can be built to comply with the specification
and make it even easier to move around leads.

- Email parsers (links here)
- Page scrapers (links here)

## The Specification

The only fields required for a lead is:

- mainContact
- source

```
{
  mainContact: <MainContact> // required
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

### MainContact

```
{
  fistName: "Foo",                // optional
  middleName: "",                 // optional
  lastName: "Bar",                // optional
  email: "foo@bar.com",           // required
  phoneNumber: "+14155552671",    // required (E.164 format)

  // Extensions
                                  // TODO: More specific but optional. Can duplicate phone

  mobileNumber: ""                // optional
  landlineNumber: ""              // optional
}
```

### Contact

The contact model

```
{
  fistName: "Foo",                // optional
  middleName: "",                 // optional
  lastName: "Bar",                // optional
  email: "foo@bar.com",           // optional
  phoneNumber: "+14155552671",    // optional E.164 format

  mobileNumber: "+14445558888"    // optional
  landlineNumber: "+12223334444"  // optional
}
```

### Vehicle

The vehicle model

```
{
  year: "2020",
  make: "Tesla",
  model: "Y",
  vin: "VIN12345678"
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

### Contributing

Please file an issue detailing your feedback.
