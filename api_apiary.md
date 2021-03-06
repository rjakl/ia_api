FORMAT: 1A
HOST: http://polls.apiblueprint.org/

# IA API

IA API is API distributing information about auctions and allows investors to bid.

## IA API ROOT [/]

### Retreive the Entry Point [GET]

+ Response 200 (application/json)

    + Body

            {
                "auctions_url": "/auctions",
                "auction_bids_url": "/auctions/{id}/bids",
                "auction_documents_url": "/auctions/{id}/documents",
                "industries_url": "/industries",
                "login_url": "/login",
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
                "id": 1,
                "name": "Aukce 1",
                "status": "RUNNING",
                "start_date": "2016-04-18T13:10:00+0200",
                "due_date": "2017-06-30T13:10:00+0200",
                "end_date": "2017-06-28T13:10:00+0200",
                "price": 500000.00,
                "currency": "CZK",
                "rating_score": "A+",
                "rating_payment": "B++",
                "face_value": 1000000.00,
                "bid_users": [3, 6],
                "max_interest": 12.0,
                "winning_user": 6,
                "top_bid": 11.6,
                "description": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                "insurance": true,
                "debtor": "Ahold",
                "industry_id": 1
            }

## Auctions [/auctions{?user_filter}{?my_bid}{?status}{?limit}{?offset}]
List of auctions.

### Retreive Auctions [GET]
Retreivest a list of auctions.

    + Parameters
    
        + user_filter: true (bool, optional) - Return user-filtered auctions.
  
        + my_bid: true (bool, optional) - Return "my" auctions.
  
        + status: "RUNNING" (string, optional) - Return auctions with this current status (RUNNING / ENDED).
  
        + limit: 10 (number, optional) - Return 10 auctions.
  
        + offset: 25 (number, optional) - Skip / do not return first 25 auctions 
 
 

+ Response 200 (application/json)

    + Body
    
            {
                "data":[
                    {
                        "id": 173152,
                        "status": "RUNNING",
                        "debtor": "Ahold",
                        "price": 500000.00,
                        "currency": "CZK",
                        "winning_user": 6,
                        "top_bid": 11.6,
                        "max_interest": 15,
                        "bid_users": [6],
                        "rating_score": "A+",
                        "due_date": "2017-08-30",
                        "end_date": "2017-06-26T16:24:00Z",
                        "insurance": true,
                        "industry_id": 1,
                        "name": "Aukce 173152",
                        "start_date": "2016-04-18T10:10:00Z",
                        "description": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 700000.00,
                        "rating_payment": "B++"
                    },
                    {
                        "id": 170124,
                        "status": "RUNNING",
                        "debtor": "Federal-Mogul a.s. a další firmy taky atd atd",
                        "price": 6444,
                        "currency": "EUR",
                        "winning_user": 1,
                        "top_bid": 3.4,
                        "max_interest": 15,
                        "bid_users": [1,  6],
                        "rating_score": "B++",
                        "due_date": "2017-08-30",
                        "end_date": "2017-06-27T11:39:00Z",
                        "insurance": true,
                        "industry_id": 2,
                        "name": "Aukce 170124",
                        "start_date": "2016-04-18T13:10:00Z",
                        "description": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 7000.00,
                        "rating_payment": "B++"
                    }...
                    
                ],
                "meta": {
                    "status":"ok",
                    "total_auctions":30,
                    "limit" : 10,
                    "offset" :20
                    
                }
            }

## Bids [/auctions/{id}/bids]
### Get bids on auction [GET]

+ Response 200 (application/json) 

    + Body
    
            {
                "data":[
                    {
                        "group_id": 1,
                        "bid_interest": 10.5,
                        "timestamp": "2016-07-21T17:08:00Z"
                    },
                    {
                        "group_id": 2,
                        "bid_interest": 10.4,
                        "timestamp": "2016-07-21T17:08:00Z"
                    },
                    {
                        "group_id": 3,
                        "bid_interest": 11,
                        "timestamp": "2016-07-21T17:08:00Z"
                    }
                ],
                "meta": {
                    "total_bids": 3
                }
            }



### Post new offer [POST]  

+ Request (application/json) 

    + Body
    
            {
                "bid_interest": 10.5
            }

+ Response 201

## Documents [/auctions/{id}/documents]
### Get auction documents [GET]

+ Response 200 (application/json) 

    + Body
    
            {
                "data":[
                  {
                   "name": "whatever",
                    "type": "INVOICE",
                    "files": [
                        {
                            "url": "https://cdn.pixabay.com/photo/2017/07/07/20/43/great-spotted-woodpecker-2482669_960_720.jpg",
                            "format": "jpeg"
                        },
                        {
                            "url": "https://cdn.pixabay.com/photo/2017/07/07/20/04/purple-2482544_960_720.jpg",
                            "format": "jpeg"
                        },
                         {
                            "url": "https://cdn.pixabay.com/photo/2017/07/07/20/02/coffee-2482536_960_720.jpg",
                            "format": "jpeg"
                        }
                    ]
                  },
                  {
                   "name": "whatever 2",
                    "type": "INVOICE",
                    "files": [
                        {
                            "url": "https://cdn.pixabay.com/photo/2017/07/07/20/43/great-spotted-woodpecker-2482669_960_720.jpg",
                            "format": "jpeg"
                        },
                        {
                            "url": "https://cdn.pixabay.com/photo/2017/07/07/20/04/purple-2482544_960_720.jpg",
                            "format": "jpeg"
                        },
                         {
                            "url": "https://cdn.pixabay.com/photo/2017/07/07/20/02/coffee-2482536_960_720.jpg",
                            "format": "jpeg"
                        }
                    ]
                  }
                ],
                "meta": {
                    "total_documents": 3
                }
            }

## Industries [/industries]
### Get industries IDs and names [GET]

+ Response 200 (application/json) 

    + Body
    
            [
                {
                    "id": 1,
                    "name": "Elektronika"
                },
                {
                    "id": 2,
                    "name": "Maloobchod a velkoobchod taky taky"
                },
                {
                    "id": 3,
                    "name": "Potraviny"
                },
                {
                    "id": 4,
                    "name": "Textil"
                }
            ]


## Login [/login]
### Login and get informations about investor [GET]

+ Response 200 (application/json) 

    + Body

            {
                "first_name": "Josef von pán",
                "last_name": "Novák velký",
                "user_id": 3,
                "auction_limit": 9,
                "auction_limi_used": 2
            }

            
## UserFilter [/user_filter]
### Get user filter from DB [GET]

+ Response 200 (application/json) 

    + Body
    
            {
                "bid_interest_min": 3.6,
                "price_min": 1500000,
                "price_max": 8500000,
                "currency": ["CZK"]
            }

### Update filter [POST]  

+ Request (application/json) 

    + Body
    
            {
                "bid_interest_min": 3.6,
                "price_min": 1500000,
                "price_max": 8500000,
                "currency": ["CZK", "EUR"]
            }

+ Response 201
