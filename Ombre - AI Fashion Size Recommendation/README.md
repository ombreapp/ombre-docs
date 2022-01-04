# Ombre - AI Fashion Size Recommender

# Overview
* [Introduction](#introduction)
* [API Usage](#api-usage)
    * [Endpoint](#endpoint)
    * [Request Parameters](#request-parameters)
    * [Response Structure](#response-structure)
* [Limitations](#limitations)


## Introduction
AI Fashion Size Recommender is a machine learning system built based on the real-world dataset. If you're looking to purchase clothings online but unsure of your size, this recommender is for you.


## API Usage

### RapidAPI 
You can find our API here: [Link](https://rapidapi.com/OmbreRapid/api/ombre-ai-fashion-size-recommendation/)

### Endpoint
``` 
/sizing 
```
### Request Parameters
```js
    product_type: string
    brand: string
    size_type: string
    height: string
    weight:string
```

* `product_type`

    - Product Type is where the type of the garment is specified.
    - Valid inputs are either `top`, `bottom`, or `footwear`.
    - Providing an invalid input would result in a `422 Unprocessable Entity` response.

* `brand`
   
    - The brand of the garment.
    - Note that the spelling and punctuations matter. 
    - If no brand is supplied or invalid brand is supplied, the system will treat this field as an unknown.
    - Therefore, the accuracy of the recommendation might decrease.
    - Current supported brands can be seen in the dropdown below.
 <details>
   <summary>Click here for list of brands</summary>

    ```md
    - Abercrombie & Fitch
    - Adidas
    - Armani Exchange
    - Asos
    - Banana Republic
    - Calvin Klein
    - Cotton On
    - DKNY
    - Esprit
    - Forever 21
    - Fred Perry
    - Gap
    - Generic
    - H&M
    - Hollister
    - J Crew
    - Lavish Alice
    - Levi's
    - Mango
    - Mango / MNG
    - Marks & Spencer
    - Miss Selfridge
    - Nike
    - Padini
    - Polo Ralph Lauren
    - Pomelo
    - Pull & Bear
    - Shein
    - Tommy Hilfiger
    - Topman
    - Topshop
    - Uniqlo
    - Zalora
    - Zara
    ```
   </details>
        

* `size_type`
    
    - Size type of the garment.
    - Supported inputs are `INT` (International), `US` (United States), or `EU` (Europe).
    - Providing an invalid input will result in a `422 Unprocessable Entity`.

* `height`
    
    - The body height of the user.
    - The height measurement is in **centimeter**.
    - The ideal range of the input is from `145 to 202`.
    - The input's data type should be in _string_.

* `weight`
    
    - The body weight of the user.
    - The weight measurement is in **kilogram**.
    - The ideal range of input is from `28 to 156`.
    - The input's data type should be in _string_.

A request example is as shown below:
```json
{
    "product_type":"top", 
    "brand":"H&M",
    "size_type": "INT",
    "height": "150.0",
    "weight": "56.0"
}
```

### Response Structure

The response data type from the system is a **JSON object**. The prediction(s) from the system is stored as a value in `pred_response` key as an array. Depending on the input, the system might return 1 or more predictions along with a confidence score that represents the confidence of the system in the given prediction. Hence, the array consist one or more JSON objects with each containing two keys. `prediction` and `confidence_score`.

A response example is as shown below.
```json
{
    "pred_response": [
        {
            "prediction": "S",
            "confidence_score": "0.37499999753422675"
        },
        {
            "prediction": "XS",
            "confidence_score": "0.49999999671230233"
        }
    ]
}
```

