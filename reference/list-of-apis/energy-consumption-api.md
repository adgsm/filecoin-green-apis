---
description: >-
  This API provides comprehensive data about Filecoin Storage Providers' energy
  consumption.
---

# ⚡ Energy consumption API

## Data model

Data model is listing all available data models (e.g. Energy intensity, Energy used to seal data, Energy used to store data, etc.).

{% swagger method="get" path="" baseUrl="https://api.filgreen.d.interplanetary.one/models/list" summary="List available API data models" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="JSON response" %}
```javascript
[
    {
        "id": 0,
        "name": "Energy consumption rate (v1.0.1)",
        "code_name": "TotalEnergyModelv_1_0_1",
        "category": "energy",
        "details": "The total rate of electrical energy use. This is the sum of sealing and storage energy use, multiplied by a [Power Usage Effectiveness](https://en.wikipedia.org/wiki/Power_usage_effectiveness) (PUE) representing overhead energy costs such as cooling and power conversion. Bounds and estimate come from combining the bounds and estimates of sealing and storage energy, as well as different values of estimated PUE.\n\n**Network view:** Total electrical power used by the Filecoin network.\n\n**Storage Provider (SP) view:** Electrical power used by this SP.\n"
    },
    {
        "id": 1,
        "name": "Energy used to seal data (v1.0.1)",
        "code_name": "SealingEnergyModelv_1_0_1",
        "category": "energy",
        "details": "[Sealing](https://spec.filecoin.io/systems/filecoin_mining/sector/sealing/) is the process of generating SNARK proofs for a data sector which will allow an SP to prove that they are continuing to store that data over time, and is one of the components of energy use of the Filecoin network. Energy use due to sealing is estimated by multiplying the increase in storage capacity over a given time period by a constant value as described in the methodology. Bounds and estimate come from different values of this constant.\n\n**Network view:** Total electrical power used to seal data for the entire Filecoin network.\n\n**Storage Provider (SP) view:** Electrical power used by this SP to seal data.\n"
    },
    {
        "id": 2,
        "name": "Energy used to store data (v1.0.1)",
        "code_name": "StorageEnergyModelv_1_0_1",
        "category": "energy",
        "details": "The energy used to store data over time, which is a component of the energy used by the Filecoin network. Storage energy use is estimated by multiplying storage capacity by a constant value. Bounds and estimate come from different values of this constant.\n\n**Network view:** Total electrical power used to store all data on the Filecoin network.\n\n**Storage Provider (SP) view:** Electrical power used by this SP to store data.\n"
    },
    {
        "id": 3,
        "name": "Cumulative Energy Use (v1.0.1)",
        "code_name": "CumulativeEnergyModel_v_1_0_1",
        "category": "energy",
        "details": "Total amount of energy used during a time period in kWh"
    },
    {
        "id": 4,
        "name": "Cumulative renewable energy purchases ",
        "code_name": "RenewableEnergyModel",
        "category": "energy",
        "details": "Cumulative renewable energy certificate (REC) purchases over time"
    },
    {
        "id": 5,
        "name": "Energy Intensity",
        "code_name": "EnergyIntensityModel",
        "category": "energy",
        "details": "\n             **Energy Intensity:** Total electrical power used by the Filecoin network \n             divided by data storage Capacity.\n             "
    },
    {
        "id": 6,
        "name": "Data storage capacity added per day",
        "code_name": "SealedModel",
        "category": "capacity",
        "details": "**Network view:** New data storage capacity added to Filecoin’s decentralized storage network (sealed) per day.\n\n**Storage Provider (SP) view:** The amount of new data storage contributed to the network (sealed) by this SP per day.\n"
    },
    {
        "id": 7,
        "name": "Data storage capacity",
        "code_name": "CapacityModel",
        "category": "capacity",
        "details": "**Network view:** The total amount of data storage capacity contributed to Filecoin’s decentralized storage network, based on on-chain proofs.\n\n**Storage Provider (SP) view:** The amount of data storage contributed by this SP, based on on-chain proofs.\n"
    }
]
```
{% endswagger-response %}
{% endswagger %}

### Daily, weekly and monthly data granulation

This endpoint provides data for selected data model on grouped on a daily, weekly or monthly level.

{% swagger method="get" path="" baseUrl="https://api.filgreen.d.interplanetary.one/models/model" summary="Daily, weekly and monthly energy consumption for selected model, date range and Storage Provider" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="id" type="Integer" required="true" %}
Id of the data model.

\


(either "id" or associated "code_name" query parameter have to be provided)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="code_name" required="true" %}
Code name of the data model.

\


(either "id" or associated "code_name" query parameter have to be provided)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="filter" %}
Data granulation. Possible values are: "day", "week" or "month".

\


If not provided "day" is considered as default value.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="start" type="Date / String" %}
ISO 8601 formatted start date.

\


If not provided data points are listed from the epoch 0.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="end" type="Date / String" %}
ISO 8601 formatted end date.

\


If not provided data points are listed up to the most recent measurement.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="offset" type="Integer" %}
Number of data points to skip from the beginning of the record set. Default 0.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="Integer" %}
Maximal number of data points to be listed. Default 10000.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="JSON response" %}
```javascript
{
    "id": "0",
    "code_name": "TotalEnergyModelv_1_0_1",
    "name": "Energy consumption rate (v1.0.1)",
    "category": "energy",
    "x": "time",
    "y": "kW",
    "version": 0,
    "filter": "day",
    "data": [
        {
            "title": "Lower bound",
            "data": [
                {
                    "value": "31894.361954900576",
                    "start_date": "2022-04-29T00:00:00.000Z",
                    "end_date": "2022-04-29T23:59:59.999Z"
                },
                {
                    "value": "31775.267922347760",
                    "start_date": "2022-04-30T00:00:00.000Z",
                    "end_date": "2022-04-30T23:59:59.999Z"
                }
            ]
        },
        {
            "title": "Estimate",
            "data": [
                {
                    "value": "171561.258677004376",
                    "start_date": "2022-04-29T00:00:00.000Z",
                    "end_date": "2022-04-29T23:59:59.999Z"
                },
                {
                    "value": "170551.946689708060",
                    "start_date": "2022-04-30T00:00:00.000Z",
                    "end_date": "2022-04-30T23:59:59.999Z"
                }
            ]
        },
        {
            "title": "Upper bound",
            "data": [
                {
                    "value": "473751.138657113246",
                    "start_date": "2022-04-29T00:00:00.000Z",
                    "end_date": "2022-04-29T23:59:59.999Z"
                },
                {
                    "value": "471916.373850792235",
                    "start_date": "2022-04-30T00:00:00.000Z",
                    "end_date": "2022-04-30T23:59:59.999Z"
                }
            ]
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

