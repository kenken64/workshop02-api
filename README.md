## Step by step for workshop 02

```
npm i compression express express-range mongodb uuid --save
```

```
mongoimport --file zips.json --host localhost -d cities -c cities --drop
```