
# Develop a microservice app

We will develop an app for ticket booking using micro service .



Async communications => communicate chnages uisng events sent to an event bus

## Some challenges
it's bit challenge in a big micro service to understand the event flow

Also it's hard to remember the event properties.

Also hard to test event flows


## Central npm module
We will be building a central npm module, to avoid a lot of

duplicate code in the microservice.

Also we will define all the events in the shared library.

## Ticketing app overview

Selling event tickets 

If a popular event is there, tickets of that will be sold very quickly.
We need some mechanism here for smooth selling of tickets.

Some this app allows a user

1. list tickets for an event
2. other users can purchase it
3. when a user attempts to pucchase a ticket, it should be locked for some
specific time like 1 minute
while locked, no other user can buy it till the lock in  period is over.
4. ticket price can be editted if it's not locked

## Resource types in the project

Users
 email
 password

Ticket
   title
   price
   user_id
   order_id

Orders
  user_id
  status
  ticket_id
  expires_at

Charge
  order_id
  status
  amount
  stripe_id
  stripe_refund_id


## Services

auth
tickets
orders
expiration
payments


Feature-based service design would be better.
So one service might handle one feature.



## Events in the app

UserCreated 
UserUpdated
OrderCreated
OrderCancelled
OrderExpired
TicketCreated
TicketUpdated
ChargeCreated

NATS streaming is used as event bus in the app

















