# OLEX

Open Lead Exchange

By William Estoque

## Objectives

OLEX is a modern specification for transferring leads in the internet.

A lead is any contact that is **reachable**. There is only 1 requirement for a contact,
a phone number OR an email. The OLEX specification supports modern requirements such as
phone number DNC (Do Not Call) flags and email unsubscribed flags so you can determine
if you can reach out to the lead. In addition, the fields in the OLEX specification 
gives us a flexible base that can support leads as simple as one main contact to something
as complex as one main contact with multiple members including vehicles, residences
and insurance quotes.

Multiple parsers and scrapers can be built to comply with the specification
and make it even easier to move around leads.

- Email parsers (links here)
- Page scrapers (links here)

OLEX has 3 goals:

**Simple**
By having an efficient standard mapping, we can capture a wealth of information
using just 1 JSON object.

**Transferrable**
It should be easy to transfer leads to and from different services providers.
You can even capture data from a page and convert it to an OLEX compliant JSON
and send it anywhere.

**Extensible**
Extra fields could be added for different purposes, insurance, real estate, etc.

## The Specification

The only field required for a lead is:

- mainContact

```
{
  mainContact: <MainContact> // required
}
```

A simple example:

```
{
  mainContact: {
    email: {
      emailAddress: "foo@bar.com",
      isUnsubscribed: false
    }
  }
}
```

A more complex structure:

```
{
  mainContact: <MainContact> // required
  members: [<Contact>]
  vehicles: [<Vehicle>],
  residences: [Residence],
  tags: [],                  // optional, could be added to add metadata. example, `tags: ["facebook"]`
  createdAt: "",             // recommendation, required to tell how old the lead is
  updatedAt: ""              // recommendation, required to know if the lead has been updated by provider since
}
```

### MainContact

```
{
  fistName: "Foo",                // optional
  middleName: "",                 // optional
  lastName: "Bar",                // optional
  email: {
    emailAddress: "foo@bar.com",      // required (has to be valid format)
    isUnsubscribed: true              // optional, if none provided, we don't know
  },
  phone: {
    phoneNumber: "+14155552671"       // required (E.164 format)
    isDnc: false                      // optional, if none provided, we don't know
  }
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
