[https://apify.com/epctex/tasty-scraper](https://apify.com/epctex/tasty-scraper?fpr=yhdrb)

# Actor - Tasty Scraper

## Tasty scraper

Since Tasty doesn't provide a good and free API, this actor should help you to retrieve data from it. This actor can provide you with very detailed

The Tasty data scraper supports the following features:

-   Search any keyword - You can search for any keyword and find the recipes according to your needs.

-   Scrape recipes - Scrape any recipes in a very detailed and structured from Tasty.

-   Scrape articles - Fetch any articles that have been published on Tasty.

-   Scrape compilations - You can scrape any compilation that you need. It is structured and provides all the detailed information.

-   Scrape topics - If you want to scrape a specific topic with a huge list of recipes, you can just provide it and Tasty Scraper will do the rest.

-   Scrape ingredients - You can even scrape the list that is based on the ingredients.

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/tasty-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Tasty that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Tasty.

- `startUrls`: (Optional) (Array) List of Tasty URLs. You should only provide the recipe, article, compilation, search, topic, and ingredient URLs.

- `includeReviews`: (Optional) (Boolean) This will add all the reviews that Tasty provides into the detail objects. Please keep in mind that the time and resources the actor uses will increase proportionally to the number of reviews.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. The default is `Infinite`. This applies to all `search` requests and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns an object with data.

- `customMapFunction`: (Optional) (String) Function that takes each object's handle as an argument and returns the object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific item URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape many items as possible. Therefore, it forefronts all item detail requests. If the actor doesn't block very often it'll scrape 100 items in 1 minute with ~0.04-0.06 compute units.

### Tasty Scraper Input example

```json
{
  "startUrls":[
    "https://tasty.co/search?q=avocado&sort=popular",
    "https://tasty.co/recipe/tuna-avocado-tartine",
    "https://tasty.co/article/melissaharrison/easy-dinner-recipes",
    "https://tasty.co/compilation/4-unique-ways-to-cook-eggs",
    "https://tasty.co/topic/healthy",
    "https://tasty.co/ingredient/chicken"
  ],
  "search":"avocado",
  "proxy":{
    "useApifyProxy": true
  },
  "maxItems": 50,
  "endPage": 2
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## Tasty Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any language (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Tasty actor.

## Scraped Tasty Output

The structure of each item in Tasty looks like this:

### Recipe Detail

```json
https://api.apify.com/v2/datasets/7uHdEg8f6mODflKcJ/items?clean=true&format=json
```

### Article Detail

```json
https://api.apify.com/v2/datasets/d0LQfge68CZGItUNU/items?clean=true&format=json
```

### Compilation Detail

```json
https://api.apify.com/v2/datasets/qwtTygaITMW1klZpc/items?clean=true&format=json
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
