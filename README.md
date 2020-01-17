# Models

## Core

`abstract model to track created and modified time of models`

- abstract
- TimeStampedModel
- created
- modified

## Project

`Project model`

- name: charfield
- client: foreign key
- product: manytomany

## Client

`Client model. Each clients can have many projects and lanes`

- name: client name
- location: location

## Area

`Client Area`

- name: charfield
- countries: list
- client: foriegnkey

### lanes

`Production Lane of Client` Not sure for this. Because it's totally up to the client where to use the rolls.
If having this, we can see our product's average condition sorted by modelname. But it already can be done in design model.

- name
- modelname
- foriegnkey(client)

## Inventory

`list of materials we have, is this really needed?`
type of materials

1. raw materials(sa649)
   mat no, outer diameter, length, current length, ordering number(foreign key)

2. materials(to manufacturing roll)
   rawmaterial(foreign key)

3. bearings
   name
   qty

4. wheels
   name
   qty

5. powders
   name
   amount[kg]

6. lubricants
   name:
   amount[liter]

7. coolant
   name:
   amount[liter]

8. bolt&nut&washers
   name:
   amount:[qty]

9. general tools

10. mearsuring tools
    name:
    qty

## Material

type: charfield with choice

## Design

## Reports

## Conversations

## Messages on:

- Product
- Project
- Client
- Design
- Material

# Project View

## Listing & Search

- summary of projects
- grid shows project list
- listing should be separated as opportunity, in progress, finished
- search bar(option: search by name, client, product, status(opportunity, in progress, finished))
- each items should have link to project detail view

## Detail

- project name
- client + link to client
- products grid shows dedicated to the project(each items should have link to product detail view)

## Create

- only can be issued by sales team

## Update

- can be done everywhere(sales, material, production, a/s, qc etc)
- direct update at detail view? not sure

## Delete

- only can be deleted by sales team

# Client View

# Inventory View

## Listing

- detail grid shows inventory list or summary of inventory
- each items have link to material detail
- shows inventory

# Ideas

1.  Alarm model

```
    class Alarm(TimestampedModel):
    from: foreignkey User relatedname=alarm_from
    to: foreignkey User relatedname=alarm_to

    message: charfield
    display: booleanfield
```

결재 버튼 누르기 => 결재자에게 알람 => 결재자가 레포트 누르면 결재 가능한 화면이 뜸.
여기서 생각해보면, 기안자 및 결재자 둘 다 레포트를 볼 수 있어야 함. 결재 올리기 전이면 기안자만 볼 수 있고 결재 올리고 나면 결재자에게 알람이 가고 둘 다 내용을 볼 수 있음.
결재자는 수정은 불가능 하지만 결재/반려 중 선택 가능.
반려 누르면 반려사유를 작성하여야 함. 반려되면 기안자에게 알람이 가게 되며 다시 기안자가 수정가능해짐.
결재가 되고나면 레포트가 확정되며 내용을 프린트 가능하며, 유관부서가 레포트를 볼 수 있게 됨.

1. 입고소재검사레포트
2. 입고롤검사레포트
3. A/S 레포트
4. 부적합 레포트
