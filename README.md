# DD api examples


## Create auth token
```
curl --request POST --url https://ddapi.production.dietdoctor.com/auth/create  --header 'content-type: application/json' --data '{ "username": "email@example.com", "password": "example" }' 
```


## Get 25 recipes

```shell
curl --request POST \
  --url https://ddapi.production.dietdoctor.com/v1/ \
  --header 'content-type: application/json' \
  --data '{"query":"# page itterates from 1 to 10\n# pageSize is 100\n# tagFilters is []\nquery GetRecipes($page: Int, $pageSize: Int, $tagFilters: [String]) {\n  listRecipes(input: {page: $page, includePremiumPreview: false, pageSize: $pageSize, tagFilters: $tagFilters}) {\n    recipes {\n      isMembersOnly\n      id\n      \n    \n  title\n  description\n  rating\n  modifiedAt\n  slug\n  nutrition {\n    values {\n      carbs\n      fat\n      protein\n      calories\n      fiber\n      __typename\n    }\n    \n    __typename\n  }\n  \n  images {\n    hz\n    vt\n    brightness\n    __typename\n  }\n  \n    }\n    totalSize\n    nextPage\n    __typename\n  }\n \n}\n","variables":{"page":1,"pageSize":25},"operationName":"GetRecipes"}'
```

## get member meal plans

```shell
curl --request POST --url https://ddapi.production.dietdoctor.com/v1/ \
  --header 'authorization: Bearer example' \
  --header 'content-type: application/json' \
  --data '{"query":"query GetMemberMealPlans {\n memberMealplans(perPage: 25, page: 1) {\n id\n title \n __typename\n }\n}","operationName":"GetMemberMealPlans"}' 
 ```
 
## postman collection
 
You can import postman collection with more examples: https://github.com/dietdoctor/postman-api-collection/blob/main/ddAPiCollection.json
