FORMAT: 1A
HOST: http://polls.apiblueprint.org/

# IA API

IA API is API distributing information about auctions and allows investors to bid.

## IA API ROOT [/]

### Retreive the Entry Point [GET]

+ Response 200 (application/json)

    + Body

            {
                "data":{
                    "auctions_url": "/auctions"
                },
                "meta": {
                    "code": 200
                }
            }

## Auction [/auctions/{id}]
An Auction contains information about current state.

### Retreive Auction [GET]
Retreivest Auction with the given ID.

    + Parameters
        + id: 1 (number, required) - ID of auction
    
    + Attributes
        + bid_users - List of investor IDs, which bidded on auction.

+ Response 200 (application/json)

    + Body
    
            {
                "data":{
                    "id": 1,
                    "name": "Aukce 1"
                    "status": "RUNNING",
                    "due_date": "2016-06-30",
                    "end_date": "2016-05-18 13:10:00",
                    "price": "500000.00",
                    "currency": "CZK",
                    "economical_rating": "A+",
                    "payment_rating": "B++"
                    "face_value": "1000000.00",
                    "bid_users": [3, 6],
                    "max_interest": 12.0,
                    "winning_user": 6,
                    "actual_bid": 11.6,
                    "details": "Jedná se o dodávku nápojů ...",
                    "insurance": "Euler Hermes",
                    "counterparty": "Ahold",
                    "industry": "Maloobchod"
                },
                "meta": {
                    "code": 200
                }
            }

## Auctions [/auctions{?actual_bid}{?currency}{?industry}{?status}{?price}{?limit}{?offset}]
List of auctions.

### Retreive Auctions [GET]
Retreivest a list of auctions.

    + Parameters
        + actual_bid: 1 (number, optional) - Return auctions with higher actual bid.
        + currency: CZK (string, optional) - Return auctions with this currency.
        + industry: Maloobchod (string, optional) - Return auctions with this industry.
        + status: RUNNING (string, optional) - Return auctions with this current status.
        + price: <=500000 (number, optional) - Return auctions with price lower than or equal  500 000.
        + limit: 10 (number, optional) - Return 10 auctions.
        + offset: 25 (number, optional) - Skip / do not return first 25 auctions 
 

+ Response 200 (application/json)

    + Body
    
            {
                "data":[
                    {
                        "id": 1,
                        ...
                    },
                    {
                        "id": 2,
                        ...
                    },
                    {
                        "id": 3,
                        ...
                    }
                ],
                "meta": {
                    "code": 200,
                }
            }

## Bids [/auctions/{?id}/bids]
### Get bids on auction [GET]

+ Response 200 (application/json) 

    + Body
    
            {
                "data":[
                    {
                        "user_id": 1,
                        "bid_interest": 10.5,
                        "timestamp": "2016-07-21 17:08:00"
                    },
                    {
                        "user_id": 2,
                        "bid_interest": 10.4,
                        "timestamp": "2016-07-21 17:08:00"
                    }
                ],
                "meta": {
                    "code": 200,
                }
            }

### Post new offer [POST]  

+ Request (application/json) 

    + Body
    
            {
                "user_id": 1,
                "bid_interest": 10.5
            }

+ Response 201