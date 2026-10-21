from copy import deepcopy

accounts = [
    {"name": "Alex",  "balance": 500},
    {"name": "Maria", "balance": 300},
    {"name": "John",  "balance": 100},
]

batches = [
    {
        "id": "batch_1",
        "steps": [
            {"type": "transfer", "from": "Alex", "to": "Maria", "amount": 100},
            {"type": "transfer", "from": "Maria", "to": "John", "amount": 50},
        ],
    },
    {
        "id": "batch_2",
        "steps": [
            {"type": "transfer", "from": "John", "to": "Alex", "amount": 30},
            {"type": "transfer", "from": "Alex", "to": "Maria", "amount": 1000},  # fails
        ],
    },
    {
        "id": "batch_3",
        "steps": [
            {"type": "transfer", "from": "Maria", "to": "John", "amount": 25},
        ],
    },
]
# {"batch_id": "...", "result": "committed"}
audit = []   # empty list; you append results as you go
#first for loop: 




Fail = []
for b in batches:
    test = deepcopy(accounts)
    best = True   
    for c in b["steps"]:
        
        ok = True
        Sender = None
        Reciver = None 
        
        for t in test:
            if c["from"] == t["name"]:

                Sender = t

            if c["to"] == t["name"]:

                Reciver = t
#this is start of check

        for t in test:
            if Sender is None or Reciver is None or Sender["balance"] < c["amount"]:
                ok = b["id"]
    

        if b["id"] is not ok:
            Sender["balance"] -= c["amount"]
            Reciver["balance"] += c["amount"]
            print( Sender, Reciver)

        else:
            Sender["balance"] += c["amount"]
            Reciver["balance"] -= c["amount"]
            print("correction")
            Fail.append(b["id"])
            print(Fail)

    
for b in batches:
     
    best = True   
    for c in b["steps"]:

        ok = True
        Sender = None
        Reciver = None 
        
        for a in accounts:
            if c["from"] == a["name"]:

                Sender = a

            if c["to"] == a["name"]:

                Reciver = a
#this is start of check

        for a in accounts:
            if Sender is None or Reciver is None or Sender["balance"] < c["amount"]:
                ok = b["id"]
    

        if b["id"] is not ok and b["id"] not in Fail:
            Sender["balance"] -= c["amount"]
            Reciver["balance"] += c["amount"]
            print( Sender, Reciver) 
            
            


            
for b in batches:
    if b["id"] not in Fail:
        audit.append({"batch_id": b["id"], "result": "committed"})

    if  b["id"] in Fail:
        audit.append({"batch_id": b["id"], "result": "rolled_back"})


import json
accounts         
with open("accounts.json", "w") as file:
    json.dump(accounts, file, indent=4)
import json
audit
with open("audit.json", "w") as file:
    json.dump(audit, file, indent=4)

    
print("nvfjnvjfnvjnfvjnv")
with open("accounts.json", "r") as file:
    accounts = json.load(file)

print(accounts)


with open("audit.json", "r") as file:
    audit = json.load(file)

print(audit)

print('comparison numbers')
print(accounts[0])
print(accounts[1])
print(accounts[2])
print(audit[0])
print(audit[1])
print(audit[2])
print(ok)
