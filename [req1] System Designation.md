# System Designation

## Part A Business Documentation

### 1 Short Summary

Store and provide real-time exchange rates of various currencies against a base currency, and store historical exchange rate information.

### 2 Explain the Action

- A scheduled task periodically retrieves real-time exchange rate data from a third-party service and saves it to the database.
- Expose APIs for querying real-time and historical exchange rates to other services.

### 3 Explain the Outcome

- Persistent storage of exchange rate information in database.
- Provide exchange rate information for a specific point in time.

### 4 Definition of Done

- The API can correctly return exchange rate information relative to the base currency based on the specified time and currency.

- Accurately persist historical exchange rate data.

## Part B Solution Documentation

### 1 Database

Using MySQL as the database.

Currency Table

| Column        | Desription       |
| ------------- | ---------------- |
| id            | Primary Key, int |
| Currency_name | varchar(100)     |
| Exchange_rate | Decimal          |
| Time          | DateTIme         |

### 2 API

#### Description  

Provides the exchange rate of a specified currency relative to a base currency at a specific time. If no time is specified, the latest exchange rate is returned.

####  HTTP Method  `GET`

#### Endpoint  

#### ==/api/exchange-rate==

#### Query Parameters

| Name | Type   | Required | Description                                                  |
| ---- | ------ | -------- | ------------------------------------------------------------ |
| time | string | No       | ISO 8601 timestamp (e.g., `2025-07-18T13:00:00Z`) for historical query |

#### Response

```json
{
  "timestamp": "2025-07-18T13:00:00Z",
  "rates": {
    "1": 0.89,
    "2": 138.25,
    "3": 0.76,
    "4": 7.24,
    "5": 1.52,
    ...
  }
}
```

