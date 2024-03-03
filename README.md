# MongoDB Day 1

`This repository contains word document.you need to download it to view`

## Queries

1. **🔍 Find all the information about each product:**
 ```
   db.products.find({})
  ```
2.**💰 Find the product price which are between 400 to 800:**
```
  db.products.find({ 'product_price': { $gte: 400, $lte: 800 } })
 ```
3.**❌ Find the product price which are not between 400 to 600:**
```
   db.products.find({‘product_price’:{$not:{$gte:400,$lte:600}});
```

4.**📈 List the four products which are greater than 500 in price:**

   ```
   db.products.find({ 'product_price': { $gt: 500 } }).limit(4)
   ```
5.**📝 Find the product name and product material of each product:**
  ```
  db.products.find({}, { 'product_name': 1, 'product_material': 1, '_id': 0 })
  ```
6.**🔍 Find the product with a row id of 10:**
  ```
   db.products.find().skip(9).limit(1);
  ```
7.**📝 Find only the product name and product material:**
```
 db.products.find({},{'id':0,'product_color':0,'product_price':0});
```

8.**🔍 Find all products which contain the value "soft" in product material:**
```

db.products.find({ 'product_material': 'Soft'})
```

9.**🔍 Find products which contain product color "indigo" and product price 492.00:**

```
db.products.find({ 'product_color': 'indigo', 'product_price': 492.00 })
```
10.**🗑️ Delete the products which product price value are same:**
```
 let Prices = db.products.distinct("product_price");

Prices.forEach(price => {
    let product = db.products.find({ product_price: price }).sort({ _id: 1 }).skip(1); 
    product.forEach(doc => {
        db.products.deleteOne({ _id: doc._id });
    });
});

```



