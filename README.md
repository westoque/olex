# OLEX

Open Lead Exchange Procolol.

## Objectives

OLEX is a specification for transferring leads in the internet. OLEX has 3 goals:

- Simple (by having 1 standard object mapping)
- Transferrable (using the JSON protocol)
- Extensible

This supports leads:

- 1 contact
- 1 contact with members
- 1 contact with members, vehicles, residences,
- 1 contact with members, vehicles, residences, vehicle_quotes, home_quotes (through Insurance Extension)

## Simple Format

```
{
  fistName: "Foo",
  lastName: "Bar",
  email: "foo@bar.com",
  phoneNumber: "222-333-5555",
  mobileNumber: "444-555-8888",
  members: {},
  vehicles: {},
  residences: {},
  dnc: true,
  tags: []
}
```

## Simple Transfer

Using the JSON protocol. We should be able to easily transfer records across platforms.

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
