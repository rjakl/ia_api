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
                "auction_bids_url": "/auctions/{?id}/bids",
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
                "data":{
                    "id": 1,
                    "name": "Aukce 1",
                    "status": "RUNNING",
                    "start_date": "2016-04-18T13:10:00+0200",
                    "due_date": "2017-06-30T13:10:00+0200",
                    "end_date": "2017-04-28T13:10:00+0200",
                    "price": 500000.00,
                    "currency": "CZK",
                    "economical_rating": "A+",
                    "payment_rating": "B++",
                    "face_value": 1000000.00,
                    "bid_users": [3, 6],
                    "max_interest": 12.0,
                    "winning_user": 6,
                    "actual_bid": 11.6,
                    "details": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                    "insurance": true,
                    "counterparty": "Ahold",
                    "industry_id": 1,
                    "due_date_20": false,
                    "cleared": false

                },
                "meta": {
                    "code": 200
                }
            }

## Auctions [/auctions{?user_filter}{?interested}{?running}{?limit}{?offset}]
List of auctions.

### Retreive Auctions [GET]
Retreivest a list of auctions.

    + Parameters
        + user_filter: 1 (bool, optional) - Return user-filtered auctions.
  
        + interested: 1 (bool, optional) - Return "my" auctions.
  
        + running: RUNNING (bool, optional) - Return auctions with this current status (RUNNING / ENDED).
  
        + limit: 10 (number, optional) - Return 10 auctions.
  
        + offset: 25 (number, optional) - Skip / do not return first 25 auctions 
 
 

+ Response 200 (application/json)

    + Body
    
            {
                "data":[
                    {
                        "id": 173152,
                        "status": "RUNNING",
                        "counterparty": "Ahold",
                        "price": 500000.00,
                        "currency": "CZK",
                        "winning_user": 6,
                        "actual_bid": 11.6,
                        "max_interest": 15,
                        "bid_users": [6],
                        "rating": "A+",
                        "due_date": "2017-08-30T13:10:00+02:00",
                        "end_date": "2017-04-27T23:15:00+02:00",
                        "insurance": "T",
                        "industry_id": 1,
                        "name": "Aukce 1",
                        "start_date": "2016-04-18T13:10:00+02:00",
                        "details": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 1000000.00,
                        "payment_rating": "B++",
                        "due_date_20": false,
                        "cleared": false
                    },
                    {
                        "id": 170124,
                        "status": "RUNNING",
                        "counterparty": "Federal-Mogul a.s.",
                        "price": 6444,
                        "currency": "EUR",
                        "winning_user": 1,
                        "actual_bid": 3.4,
                        "max_interest": 15,
                        "bid_users": [1,  6],
                        "rating": "B++",
                        "due_date": "2017-08-30T13:10:00+02:00",
                        "end_date": "2017-04-27T23:45:00+02:00",
                        "insurance": true,
                        "industry_id": 2,
                        "name": "Aukce 170124",
                        "start_date": "2016-04-18T13:10:00+02:00",
                        "details": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 1000000.00,
                        "payment_rating": "B++",
                        "due_date_20": false,
                        "cleared": false
                    },
                    {
                        "id": 134679,
                        "status": "RUNNING",
                        "counterparty": "Alza.cz a.s.",
                        "price": 90000,
                        "currency": "CZK",
                        "winning_user": 2,
                        "max_interest": 15,
                        "actual_bid": 11.6,
                        "bid_users": [2, 3, 6],
                        "rating": "A+",
                        "due_date": "2017-08-30T13:10:00+02:00",
                        "end_date": "2017-04-28T15:10:00+02:00",
                        "insurance": true,
                        "industry_id": 3,
                        "start_date": "2016-04-18T13:10:00+02:00",
                        "details": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 1000000.00,
                        "payment_rating": "B++",
                        "due_date_20": false,
                        "cleared": false
                    },
                    {
                        "id": 180951,
                        "status": "RUNNING",
                        "counterparty": "Eur s.r.o.",
                        "price": 2500000,
                        "currency": "CZK",
                        "winning_user": 3,
                        "max_interest": 15,
                        "actual_bid": 11.6,
                        "bid_users": [3, 6],
                        "rating": "A++",
                        "due_date": "2017-08-30T13:10:00+02:00",
                        "end_date": "2017-06-18T13:10:00+02:00",
                        "insurance": false,
                        "industry_id": 4,
                        "start_date": "2016-04-18T13:10:00+02:00",
                        "details": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 1000000.00,
                        "payment_rating": "B++",
                        "due_date_20": false,
                        "cleared": false
                    },{
                        "id": 123124,
                        "status": "RUNNING",
                        "counterparty": "Penny market",
                        "price": 38354,
                        "currency": "CZK",
                        "winning_user": 5,
                        "max_interest": 15,
                        "actual_bid": 3.4,
                        "bid_users": [3, 5, 6],
                        "rating": "B++",
                        "due_date": "2017-08-30T13:10:00+02:00",
                        "end_date": "2017-07-10T13:10:00+02:00",
                        "insurance": true,
                        "industry_id": 3,
                        "start_date": "2016-04-18T13:10:00+02:00",
                        "details": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 1000000.00,
                        "payment_rating": "B++",
                        "due_date_20": false,
                        "cleared": false
                    },
                    {
                        "id": 123679,
                        "status": "RUNNING",
                        "counterparty": "Penny market",
                        "price": 420000,
                        "currency": "CZK",
                        "winning_user": 4,
                        "max_interest": 15,
                        "actual_bid": 11.6,
                        "bid_users": [ 4, 6],
                        "rating": "A+",
                        "due_date": "2017-08-30T13:10:00+02:00",
                        "end_date": "2017-07-11T13:10:00+02:00",
                        "insurance": false,
                        "industry_id": 4,
                        "start_date": "2016-04-18T13:10:00+02:00",
                        "details": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 1000000.00,
                        "payment_rating": "B++",
                        "due_date_20": false,
                        "cleared": false
                    },
                    {
                        "id": 180952,
                        "status": "RUNNING",
                        "counterparty": "Eur s.r.o.",
                        "price": 52500000,
                        "currency": "CZK",
                        "winning_user": 3,
                        "max_interest": 15,
                        "actual_bid": 11.6,
                        "bid_users": [2, 3, 6],
                        "rating": "A++",
                        "due_date": "2017-08-30T13:10:00+02:00",
                        "end_date": "2017-07-18T13:10:00+02:00",
                        "insurance": false,
                        "industry_id": 1,
                        "start_date": "2016-04-18T13:10:00+02:00",
                        "details": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin in tellus sit amet nibh dignissim sagittis. Integer vulputate sem a nibh rutrum consequat. Nullam at arcu a est sollicitudin euismod. Morbi leo mi, nonummy eget tristique non, rhoncus non leo. Nullam feugiat, turpis at pulvinar vulputate, erat libero tristique tellus, nec bibendum odio risus sit amet ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Nullam lectus justo, vulputate eget mollis sed, tempor sed magna. Pellentesque pretium lectus id turpis. Vestibulum erat nulla, ullamcorper nec, rutrum non, nonummy ac, erat. Fusce tellus. Nullam justo enim, consectetuer nec, ullamcorper ac, vestibulum in, elit. ",
                        "face_value": 1000000.00,
                        "payment_rating": "B++",
                        "due_date_20": false,
                        "cleared": false
                    }
                ],
                "meta": {
                    "total_auctions":30,
                    "limit" : 10,
                    "offset" :20
                    
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
                        "timestamp": "2016-07-21T17:08:00+02:00"
                    },
                    {
                        "user_id": 2,
                        "bid_interest": 10.4,
                        "timestamp": "2016-07-21T17:08:00+02:00"
                    },
                    {
                        "user_id": 3,
                        "bid_interest": 11,
                        "timestamp": "2016-07-21T17:08:00+02:00"
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

## Documents [/auctions/{?id}/documents]
### Get auction documents [GET]

+ Response 200 (application/json) 

    + Body
    
            {
                "data":[
                    {
                        "name": "faktura 1",
                        "url": "https://investaukce.cz/...invoice.jpg"
                    },
                    {
                        "name": "faktura 2",
                        "url": "https://investaukce.cz/...invoice.jpg"
                    },
                    {
                        "name": "příloha 1",
                        "url": "https://investaukce.cz/...document.pdf"
                    }
                ],
                "meta": {
                    "total_documents": 2
                }
            }

## Industries [/industries]
### Get industries IDs and names [GET]

+ Response 200 (application/json) 

    + Body
    
            [
                {
                    "industry_id": 1,
                    "name": "Elektronika"
                },
                {
                    "industry_id": 2,
                    "name": "Maloobchod"
                },
                {
                    "industry_id": 3,
                    "name": "Potraviny"
                },
                {
                    "industry_id": 4,
                    "name": "Textil"
                }
            ]


## Login [/login]
### Login and get informations about investor [POST]


+ Response 200 (application/json) 

    + Body

            {
                "name": "Josef",
                "surname": "Novák",
                "user_id": 3,
                "auction_limit": 9,
                "auctions_win": 2
            }

            
## UserFilter [/userFilter]
### Get user filter from DB [GET]

+ Response 200 (application/json) 

    + Body
    
            {
                "bid_interest_min": 3.6,
                "price_min": 1000,
                "price_max": 100000,
                "currency": ["CZK"]
            }

### Update filter [PUT]  

+ Request (application/json) 

    + Body
    
            {
                "bid_interest_min": 3.6,
                "price_min": 1000,
                "price_max": 100000,
                "currency": ["CZK", "EUR"]
            }

+ Response 201
