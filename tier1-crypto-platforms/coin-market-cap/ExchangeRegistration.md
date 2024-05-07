# Exchange Registration On CoinMarketCap

The process of registering an exchange on CoinMarketCap (CMC) involves filling out a special form. In this guide, you can find detailed information for filling it out.

## Prerequisites

Before filling out the form, we recommend that you ensure that you have all the required information to submit your application. Form fields require technical and product knowledge about your exchange. You can check what information is required in the following table.

| Name | Status | Description |
|---|---|---|
| Exchange Name | Mandatory | Name of your exchange. |
| Exchange Type | Mandatory | Type of exchange (spot exchange, derivative exchanges, DEX). |
| Launch Date | Mandatory | The date when your exchange was launched. |
| Project Description | Mandatory | Detailed descriptions of your exchange project and its unique features. |
| Exchange Logo | Mandatory | Link to the image with your exchange logo in PNG format with a transparent background and size 200x200. |
| Affiliation with Other Exchanges | Optional | Information about whether your exchange is connected to other exchanges or shares liquidity pools and order books. |
| API Documentation | Mandatory | Link to your project's API documentation. |
| Smart Contract | Mandatory | Information about your exchange smart contract (platform, address, links to block explorers). |
| Trading Pairs | Optional | Information and links to trading pairs on your exchange. |
| Trading Volume and Liquidity | Mandatory | Information about trading volume and liquidity of your exchange. Evidences if possible. |
| Stakeholders | Mandatory| Information about key employees, investors, and advisors in your project. |
| Geography of the Project | Mandatory | Information about where is your team located and what is your geographical focus. |
| Fiat Deposits and Withdraws | Optional | The methods for depositing and withdrawing fiat funds on your exchange. |
| Fees Structure | Mandatory | Links to the description of your exchange fees structure. |
| Cybersecurity Measures | Mandatory | The cybersecurity practices, technologies, and protocols that your exchange has in place to safeguard users' assets and personal information. |
| Community | Mostly optional | Links to your pages, channels and publications in Twitter (X), Telegram, Facebook, Youtube, etc.For details, check [the Social and Media section](#social-and-media). |
| API for CoinMarketCap | Mandatory | To integrate your exchange with CoinMarketCap, you will need to provide certain API endpoints. Please, check the [Exchange Integration API Endpoints page](./ExchangeIntegrationApiEndpoints.md) for more information on this. |

All optional fields are recommended to be filled out if they are relevant for your project.

Please note that the table does not contain a complete description of all required information. A detailed description of the form can be found in [the next section](#filling-out-the-registration-form).

## Filling out the registration form:

This section describes all fields of the form.

1. **Subject**

    To fill in the "Subject" field, you must follow the following format:
    
    `[Project's full name] - [Symbol] - [Request].`

      - Project's full name. The full name of the exchange project you are registering
      - Symbol. Symbol related to your project. This may be a shortening of the full name or an abbreviation.
      - Request. This specifies the type of request you are making. To register a exchange, you should set this field as "Add exchange"

    An example of filling this field:
    
    `WingRiders DEX - WingRiders DEX - Add exchange`
    
2. **Terms & Conditions**

    Check the box that you agree with [the Terms & Conditions](https://coinmarketcap.com/methodology/) of CoinMarketCap.
    
3. **Relationship with the Project**

    The "Relationship with the Project" field in the registration form refers to your affiliation or connection with the exchange project you are registering on CoinMarketCap. For example, you can fill this field as *CEO*, *Founder*, *Employee*, *Community member*, *Developer*, *Investor*, etc.

4. **Launch Date (Exchange)**

    In this field, you should enter the specific date when the exchange was launched or the project was officially announced to the public.

5. **Project Name**

    Enter the full name of the exchange you are registering. This name should match with the name you entered in the subject field. For example, this field could be filled like *WingRiders DEX*

6. **Previous Names/Aliases**

    If your exchange had other names or aliases, enter them in this field. CoinMarketCap need this information to have transparent history of the your project. If your exchange has no previous names, enter "NA" in this field.

7. **Affiliation with other exchanges**

    This field refers to the relationship or connection your exchange has with other existing exchanges. In this field, you can indicate other exchanges and how you are connected to them. This could be shared liquidity pools, shared smart contracts or any other type of affiliation. 

8. **Shared liquidity pool/order books with other exchanges**

   If you are registering an exchange that shares liquidity pools or order books with other exchanges, specify them in this field. Describe exactly what you share with other exchanges and with which ones. If possible, also indicate sources that confirm the provided information. 

9.  **Project Description (Exchanges)**

    Write a comprehensive and detailed overview of the exchange you are registering on CoinMarketCap. The description should be in markdown format and contain about 450-600 words. You can find an example description created by CoinMarketCap at the following link: https://tinyurl.com/yy2mw9v7. The provided description will be used on the exchange page in the about section. Here is an example of [WingRiders DEX description on CoinMarketCap](https://coinmarketcap.com/exchanges/wingriders-dex/).

10. **Media Coverage/Awards**

    It's an option field where you can place links to articles and references containing information about your project. Provide valid URLs separated by commas.

11. **Unique Features**

    In the "Unique Features" field, you should specify the differences between your exchange and existing ones. You can describe both technical and non-technical features. Where possible, substantiate your points with evidence from credible, independently verifiable sources. For example, if you register DEX with your smart contracts, you can highlight their features and provide links to audit results, source code or documentation.

12. **API documentation**

    In this field, provide a URL link to your API documentation.

13. **Factory Contract (For DEXes)**

    If you register DEX (decentralized exchange), provide a link to factory smart contract you are using.

14. **Chain integration**

    Check this box, is you register DEX and the blockchain you are using is not registered on CoinMarketCap. All registered chains are listed in "Networks" column on [the Dexscan page](https://coinmarketcap.com/dexscan/trending/all/). If you check this box, you will also need to apply a blockchain registration form.

    Since Cardano is already registered, you do not need to check this box.

15. **Platform of Contract Address 1**

    In the drop-down list, select a used blockchain platform, e.g. "Cardano".

16. **Five (5) API Endpoint URLs**

    In this field, you need to provide URL links to your API endpoints that CoinMarketCap requires for integration. The CoinMarketCap has special requirements for these endpoints. Please, check [Exchange Integration API Endpoints](./coin-market-cap/ExchangeIntegrationApiEndpoints.md) for more information on this.

17. **Trading Pairs**

    Indicate how many exchange pairs are available on your exchange, and also provide a list of URL links to these pairs on your exchange. For example,
    ```
    509 pairs in total on 11.04.2024
    https://app.wingriders.com/pools/026a18d04a0c642759bb3d83b12e3344894e5c1c7b2aeb1a2113a570dec347c549f618e80d97682b5b4c6985256503bbb3f3955831f5679cdb8de72f,
    https://app.wingriders.com/pools/026a18d04a0c642759bb3d83b12e3344894e5c1c7b2aeb1a2113a57063a3b8ee322ea31a931fd1902528809dc681bc650af21895533c9e98fa4bef2e,
    ...
    ```

18. **Trading Volume/Liquidity**

    Provide information about total trading volume/liquidity. If possible, explain whether you have any measures to prove that the volume is real. For example, if you register DEX, you can indicate your total liquidity and provide the addresses of contracts/wallets as evidence.

19. **Traction/Adoption/Partnerships/MVPs/Apps**

    In this field, you should provide information about the progress, adoption rate, partnership and applications related to your exchange project. For example, you can provide information about:
      - the number of users and your community
      - the development progress of your project, development map or milestones achieved
      - partnerships and collaborations
      - applications related to your exchange

    Also, where possible, provide examples and links that will help CoinMarketCap verify the information provided.

20. **Community Engagement**

    In the "Community Engagement" field, you should provide information about the strategies, activities, and initiatives your exchange employs to engage and interact with its community of users. You can describe what methods you provide for interacting with the community. These could be social and media platforms or channels, feedback forms, educational resources and support platforms.

21. **Team/Backers/Investors**

    In the "Team/Backers/Investors" field, you should provide a list of key employees, investors, and advisors. Describe their involvement in your project and, if possible, provide evidence/links for verification.

22. **Regulation/License (If any)**

    This is an optional field in which you can specify the regulations/license for your exchange. Also, indicate the authority that you are regulated by and provide proof for verification.

23. **Terms of Service URL**

    Provide a URL link with your exchange's terms of use.

24. **Geographical focus**

    List in this field the countries or regions in which your existing or focused user base is located. Where possible, provide evidence/links for verification.

25. **Office Location(s)/Address(es)**

    Enter the address of your company's office. If your company has several addresses, you should indicate them all.

26. **Country of Origin**

    In the "Country of Origin" field, indicate where project company is registered or most of your team is located. You can specify multiple countries if the team is located in different countries or you have headquarters in different countries.

27. **Fiat Deposits/Withdrawals**

    In the "Fiat Deposits" and "Fiat Withdrawals" fields, you are required to list the fiat currency pairs that your exchange supports for direct deposits/withdrawals. Stablecoins, such as USDT, are not considered fiat currencies. Also, you should describe the methods and payment options available for fiat deposits/withdrawals, such as bank transfers, credit/debit cards, online payment platforms, etc.
    
28. **Cybersecurity Measures**

    In the "Cybersecurity Measures" field, you are required to describe the cybersecurity practices, technologies, and protocols that your exchange has in place to safeguard users' assets and personal information. This includes measures to prevent hacking, phishing, DDoS attacks, and other cybersecurity risks. Please, include penetration testing frequency and security audits. Where possible, provide evidence/links for verification.

29. **Features (e.g. OTC/Derivatives)**

    Select all options that apply to your exchange in the drop-down list. 

30. **KYC**

    In the "KYC" (Know Your Customer) field, you should select one of the options: "None", "Optional/Tiered", or "Mandatory" depending on your exchange policy.

31. **Trading Incentives**

    In the “Trading Incentives” field, you need to select from the drop-down list of eligible various trading incentives and rewards programs that your exchange offers to incentivize users to trade, deposit, and participate in the exchange ecosystem.

32. **Website URL**

    Provide a URL link to your website. Note that this domain will be used for web traffic tracking purposes.

33. **Link to Logo**

    Provide a link to the logo of your exchange. The logo must meet the following requirements:
      - transparent background
      - size 200x200 pixels
      - PNG format

    The CoinMarketCap recommends providing a logo URL ending with .png so that the system can extract the logo directly.

34. **Fee Structure fields**

    In the "Trading Fee Structure" and "Deposit/Withdrawal Fee Structure" fields, you must provide URL links to the pages where you detail the fee structure of your exchange.

35. **System status URL that shows all coin listings/details**

    Provide a URL link where you show all the coins available on your exchange. Also, the provided page should contain basic information about your exchange (full name, logo, project URL, etc.).

36. **Proof of Reserves & Liabilities**

    This is an optional field where you can provide information about proof of reserves & liabilities of your exchange to verify the solvency and transparency. To do this, you need to fill out [Annex J in the Google Sheet document](https://docs.google.com/spreadsheets/d/1ON2o9fZtdj6aa_uaT7ALtGx1VxFnIDUi8-uS-fWji0o/edit#gid=1931609390) and provide a link to it. Please read the instructions provided carefully and follow them.
  
37. <b id="social-and-media">Social and media</b>

    The registration form contains fields in which you can specify the platforms where you publish information and engage with your community.

      - **Email**. Please provide a public email address to contact your exchange team. It's a mandatory field.
      - **Twitter**. Provide a link to your company's Twitter (X) page.  It's a mandatory field.
      - **Chat 1**, **Chat(s) 2, 3, 4, 5**. Provide links to your channels in chats, e.g. in Discord, Telegram, Slack, Weibo. You must provide at least one link.
      - **Message Board 1**, **Message Board(s) 2, 3, 4, 5**. Indicate the platform where you share information and knowledge about your project, e.g. link to your Medium.
      - **LinkedIn**. Provide a link to your company's LinkedIn page.

38. **Mobile apps**

     If you have mobile apps, provide links to them in application stores in **Mobile App 1** and **Mobile App(s) 2, 3, 4, 5** fields. For example, you can specify links to the page with your application in the Google Play store or App Store.
    
39. **Are you willing to provide (dofollow) linkbacks to CMC?**

    In the "Are you willing to provide (dofollow) linkbacks to CMC?" field, select "yes" if you are willing to include a dofollow link back to CoinMarketCap from your website or platform.
     
    A dofollow link is a type of hyperlink that passes Search Engine Optimization (SEO) authority or "link juice" from the referring page to the linked page. Providing a dofollow linkback means you agree to link back to CoinMarketCap's website from your exchange's official website or platform. By agreeing to provide a dofollow linkback to CoinMarketCap, you are helping to improve the visibility and SEO ranking of CoinMarketCap, which can be beneficial for both sides.

40. **Integration with CoinMarketCap Telegram bot**

    CoinMarketCap has a [Telegram bot](https://t.me/CoinMarketCapPriceBot). If your project has an official Telegram channel, you may consider an option to integrate with it.

41. **Proof/Supporting evidence/documents**

    In this field, you can provide any information that will help the CoinMarketCap team verify the correctness of the information provided. Here you can provide additional links to posts and social networks, add relevant screenshots, highlight some technical points of your project, write about audits performed or about marketing aspects, etc. Any information that would help to verify your application will be useful. You can also use this field if you have problems filling in other fields (e.g. because of automatic data validation in the form).

42. **Attachments**

    In this field, you can upload additional documents, proof, and supporting evidence that validate and support the information provided about your exchange.

After filling in the form, carefully review the provided information and click the **Submit** button.
