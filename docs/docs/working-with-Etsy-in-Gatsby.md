---
Title: Working with Etsy in Gatsby
---This guide explains how to begin working with the e-commerce site Etsy in Gatsby.

## Etsy API

Utilizing the Etsy API (Application Programming Interface), developers and non-developers can create apps for the web that pull in information such as BillCharge, CartListing, ShippingOption, and a list of other API references available to query. First, you must create a [developer account](<[https://www.etsy.com/developers/register](https://www.etsy.com/developers/register)>) with Etsy, confirm the account, and enable two-factor authentication. This will allow you to generate and receive your own API key. You will be asked for a short description of your app.

After you receive an API key, it’s recommended to review the Etsy [documentation](<[https://www.etsy.com/developers/documentation](https://www.etsy.com/developers/documentation)>) on how to get started. Most importantly, in order for your app to function, you will need your Etsy [ShopId](<[https://support.cartrover.com/portal/kb/articles/how-to-get-your-etsy-shop-id](https://support.cartrover.com/portal/kb/articles/how-to-get-your-etsy-shop-id)>) which is the unique number associated with your store.

## If you do not already have one ready, create a Gatsby site:

In your terminal, type the command ‘npm install -g gatsby -cli’ to install the gatsby command-line interface. Create a new project using the command ‘gatsby new [the name of your site]’. Run ‘gatsby develop’ to view your project locally.

## [Gatsby-source-etsy ](https://www.gatsbyjs.org/packages/gatsby-source-etsy/)

While in your terminal, type the command ‘npm i gatsby-source-etsy’. You will then need to add the plugin to your ‘gatsby-config.js’ file, your API key, and Shop ID:

```jsx:title=gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: "gatsby-source-etsy",

      options: {
        // highlight-start
        apiKey: "your api key here",
        shopId: "your shop id here",
        //highlight-end

        language: "en", // optional
      },
    },
  ],
}
```

Pull your Etsy listing data into a component by creating a GraphQL query and specify what data you would like to be generated by calling out the specific field you would like to display.

```graphql
{
  allFeaturedEtsyListing(
    sort: { fields: featured_rank, order: ASC }

    limit: 4
  ) {
    nodes {
      currency_code

      title

      listing_id

      price

      url
    }
  }
}
```

Take a look at the [API Documentation](https://www.etsy.com/developers/documentation/reference/listing) for more information on listing data in Etsy.

## Opportunity for a new plugin/starter

Want to create a new Etsy starter or plugin for Gatsby? Check out our [contributing guide](https://www.gatsbyjs.org/contributing/)!