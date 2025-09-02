# MongoDB

---

## Instructions: 
Create a new database and some requests following the task

---

## Solution:

### Create new database qa_shop
use qa_shop;

### Create new collection card_info
db.createCollection("card_info")

### In the collection create several documents with different cards
db.card_info.insertMany([
{
card_type: "VISA",
expiry_month: 12,
expiry_year: 26,
CVV: 123,
balance: 2000.00,
status: "valid",
card_code: 8820354696467284
},
{
card_type: "MasterCard",
expiry_month: 12,
expiry_year: 26,
CVV: 456,
balance: 2000.00,
status: "valid",
card_code: 5248106661644884
},
{
card_type: "VISA",
expiry_month: 1,
expiry_year: 20,
CVV: 789,
balance: 2000.00,
status: "expired",
card_code: 4340511554108849
},
{
card_type: "MasterCard",
expiry_month: 1,
expiry_year: 20,
CVV: 101,
balance: 2000.00,
status: "expired",
card_code: 0307328035514696
},
{
card_type: "VISA",
expiry_month: 6,
expiry_year: 26,
CVV: 234,
balance: 2000.00,
status: "stolen",
card_code: 0779330784258313
},
{
card_type: "MaterCard",
expiry_month: 6,
expiry_year: 26,
CVV: 567,
balance: 2000.00,
status: "stolen",
card_code: 1151842195999505
},
{
card_type: "VISA",
expiry_month: 12,
expiry_year: 26,
CVV: 890,
balance: 0.00,
status: "valid",
card_code: 7178218557247775
},
{
card_type: "MaterCard",
expiry_month: 12,
expiry_year: 26,
CVV: 112,
balance: 0.00,
status: "valid",
card_code: 3320643190265792
},
{
card_type: "VISA",
expiry_month: 12,
expiry_year: 26,
CVV: 0,
balance: 2000.00,
status: "blocked",
card_code: 9181347306820824
},
{
card_type: "MaterCard",
expiry_month: 12,
expiry_year: 26,
CVV: 0,
balance: 2000.00,
status: "blocked",
card_code: 6107972359241284
}
])

### Show all IDs and card_type with valid status
db.card_info.find( {status: "valid"}, {card_type :1})

### Show all IDs and card_type with expiry month greater than 6
db.card_info.find( {expiry_month: {$gt: 6}}, {card_type :1})

### Show all IDs and card_type with expiry month in-between 5 and 11
db.card_info.find( {expiry_month: {$gt: 5, $lt: 11}},
{card_type :1})

### Count the amount of VISA cards
db.card_info.aggregate([
{$match: {card_type: "VISA"}},
{$count: "totalamount"}
])

### Show the info of all cards with the letter "r" in the name
db.card_info.find( {card_type: /r/})
