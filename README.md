## Gambit Groups API
Micro service which handles group generation & provides ID's to messaging services.

## Setup
`npm install`

`cat .env.example >> .env`

`heroku local`

## API
All API requests require the `x-gambit-group-api-key` to be set in the headers.

#### Create a group
**POST** `/api/v1/group`
```
{
	"campaign_id": "1112",
	"campaign_run_id": "23343212"
}
```

If no group already exists for that campaign & campaign run, it will create a new group & mobile commons groups for each environment.
It will then return the id's in the response.

```
{
  "campaign_id": 1112,
  "campaign_run_id": 23343212,
  "_id": "58125db53938a0125414dec6",
  "mobilecommons_groups": {
    "production": 257104,
    "thor": 257101,
    "local": 257098
  }
}
```

#### Get a group
**GET** `/api/v1/group/:campaign_id/:campaign_run_id`

Retrieves the group for the given campaign ID & campaign run ID.

```
{
  "_id": "58125db53938a0125414dec6",
  "campaign_id": 1112,
  "campaign_run_id": 23343212,
  "__v": 0,
  "mobilecommons_groups": {
    "production": 257104,
    "thor": 257101,
    "local": 257098
  }
}
```
