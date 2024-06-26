# Guide For Adding Token Metadata To The Cardano Token Registry

This guide aims to provide a comprehensive overview of how to add metadata to [the Cardano Metadata Registry](https://github.com/cardano-foundation/cardano-token-registry?tab=readme-ov-file), empowering token issuers, developers, and stakeholders to enhance the visibility, utility, and interoperability of their tokens within the Cardano network.

This guide will walk you through the process of adding your token metadata to the Cardano metadata registry, covering everything from understanding metadata structure and preparing data to verifying and publishing your token metadata.

## Cardano token registry repository

[The Cardano token registry](https://github.com/cardano-foundation/cardano-token-registry) is a centralized GitHub repository of metadata associated with tokens built on the Cardano blockchain. It serves as a comprehensive database where token issuers can register and publish metadata related to their tokens, enabling easy access and retrieval by users, wallets, and decentralized applications (DApps) within the Cardano ecosystem.

To add your token metadata to the registry you have to prepare your metadata in a special format and open a pull request in the Cardano Token Registry GitHub repository.

For more details about the Cardano token registry repository, check their README: https://github.com/cardano-foundation/cardano-token-registry/blob/master/README.md

All registered tokens are stored in [the mappings folder](https://github.com/cardano-foundation/cardano-token-registry/tree/master/mappings) of the Cardano token registry repository. This folder contains a file for each token's metadata in JSON format.

## Metadata structure

To add metadata to the Cardano metadata registry, you need to prepare the data and provide it as a JSON file. 

The metadata file must contain one object in JSON format with certain fields. Check the following list for the fields' description and examples for [the WingRiders Governance Token (WRT)](https://github.com/cardano-foundation/cardano-token-registry/blob/master/mappings/c0ee29a85b13209423b10447d3c2e6a50641a15c57770e27cb9d507357696e67526964657273.json).

1. **Subject field**

    - ***Field name***: `subject`
    - ***Field type***: `string`
    - ***Status***: mandatory

    The field contains a string that is a concatenation of a base16-encoded policy ID and base16-encoded asset name.

    <details>
    <summary><b>Example</b></summary>

    Base16-encoded policy id for WRT: `c0ee29a85b13209423b10447d3c2e6a50641a15c57770e27cb9d5073`
    
    Base16-encoded asset name (`WingRiders`): `57696e67526964657273`

    Field value:
    
    ```json
    "subject": "c0ee29a85b13209423b10447d3c2e6a50641a15c57770e27cb9d507357696e67526964657273"
    ```
    </details>

2. **Name field**

    - ***Field name***: `name`
    - ***Field type***: [`json object`](#json-object-field-struture)
    - ***Status***: mandatory
  
    The field contains a [json object](#json-object-field-struture) whose value is a human-readable subject name. It should be suitable for use in the interface.

    <details>
    <summary><b>Example</b></summary>
    
    ```json
    "name": {
        "signatures": [],
        "sequenceNumber": 0,
        "value": "WingRiders Governance Token"
    }
    ```
    </details>

3. **Description field**

    - ***Field name***: `description`
    - ***Field type***: [`json object`](#json-object-field-struture)
    - ***Status***: mandatory
  
    The field contains a [json object](#json-object-field-struture) whose value is a human-readable description of the token. It should be suitable for use in the interface.

    <details>
    <summary><b>Example</b></summary>
    
    ```json
    "description": {
        "signatures": [],
        "sequenceNumber": 0,
        "value": "WingRiders is a decentralized exchange protocol on Cardano. WRT provides access to dao voting and other DEX related functions."
    }
    ```
    </details>

4. **Policy field**

    - ***Field name***: `policy`
    - ***Field type***: [`json object`](#json-object-field-struture)
    - ***Status***: optional
  
    The field contains a [json object](#json-object-field-struture) whose value is the base16-encoded CBOR representation of the monetary policy script, used to verify ownership. Optional in the case of Plutus scripts as verification is handled elsewhere. Please note that this field is not the policy id.

5. **Ticker field**

    - ***Field name***: `ticker`
    - ***Field type***: [`json object`](#json-object-field-struture)
    - ***Status***: optional
  
    The field contains a [json object](#json-object-field-struture) whose value is a human-readable ticker name for the subject. It should be suitable for use in the interface.

    <details>
    <summary><b>Example</b></summary>
    
    ```json
    "ticker": {
        "signatures": [],
        "sequenceNumber": 0,
        "value": "WRT"
    }
    ```
    </details>

6. **URL field**

    - ***Field name***: `url`
    - ***Field type***: [`json object`](#json-object-field-struture)
    - ***Status***: optional
  
    The field contains a [json object](#json-object-field-struture) whose value is a HTTPS URL to the webpage related to your token.

    <details>
    <summary><b>Example</b></summary>
    
    ```json
    "url": {
        "signatures": [],
        "sequenceNumber": 0,
        "value": "https://www.wingriders.com"
    }
    ```
    </details>

7. **Logo field**

    - ***Field name***: `logo`
    - ***Field type***: [`json object`](#json-object-field-struture)
    - ***Status***: optional
  
    The field contains a [json object](#json-object-field-struture) whose value is the byte representation of the PNG image of your token logo.

    <details>
    <summary><b>Example</b></summary>
    
    ```json
    "logo": {
        "signatures": [],
        "sequenceNumber": 1,
        "value": "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"
    }
    ```
    </details>

8. **Decimals field**

    - ***Field name***: `decimals`
    - ***Field type***: [`json object`](#json-object-field-struture)
    - ***Status***: optional
  
    The field contains a [json object](#json-object-field-struture) whose value is a number of decimals to your token. Please note that the value field in the json object is a number, not a string.

    <details>
    <summary><b>Example</b></summary>
    
    ```json
    "decimals": {
        "signatures": [],
        "sequenceNumber": 0,
        "value": 6
    }
    ```
    </details>

### Json object field structure

Most of the fields in the metadata structure have the `json object` type. These metadata fields should follow the following structure:

```json
{
    "signatures": [...],
    "sequenceNumber": ...,
    "value": "..."
}
```

Json object fields:

- `value` - the actual value of the metadata field, e.g. name or description. It can take both string and numeric values.
- `sequenceNumber` - a number indicating the field version. Each time a field changes, this value must be incremented. If you add your token the first time, this value will be `0`.
- `signatures` - an array of signatures for this field. The item can be signed with keys used to define your asset policy, such that, the resulting signatures validate the original monetary script. The array can be empty.

## Metadata submission

Once you've ensured that you have all the necessary information to submit your token metadata, you can create a pull request to add your token to the registry. To do this, follow the following instructions:

1. **Create a fork of the cardano-token-registry repository**

    First of all, you need to create a fork of the cardano-token-registry repository. To do this, visit https://github.com/cardano-foundation/cardano-token-registry and find the "Fork" button in the top right corner. Click on it.

    <p align="center"><img src="./.assets/fork_button.png" alt="Fork button" style="width: 500px"/></p>

    You will be redirected to the page where you can finish the fork creation.

    <p align="center"><img src="./.assets/finish_fork_creation.png" alt="Finishing fork creation" style="width: 500px"/></p>

    Enter your fork name and click on the "Create fork" button.

2. **Clone your fork of the cardano-token-registry repository**

    Use the `git clone` command to clone the forked repository on your machine.

    ```console
    git clone https://github.com/WingRiders/cardano-token-registry.git
    cd ./cardano-token-registry 
    ```
   
3. **Add a file with your token metadata to the mappings folder**

    Create a JSON file for your token metadata in the mappings folder. To do this you can use the following command:

    ```console
    touch ./mappings/{your-token-subject}.json
    ```

    In the created file, put a JSON object that describes your token metadata. You can check the JSON-object description in [the metadata structure section](#metadata-structure)

4. **Push the change to your fork repository**

    Before creating PR, you need to commit your changes and push them to the forked repository. To do this use the following commands:

    ```console
    git add ./mappings/{your-token-subject}.json
    git commit -m "Add {your-token-name} metadata"
    git push
    ```

    Please note, that authentication may be required to push to GitHub.

5. **Open a pull request**

    Go to the forked repository on GitHub. On the repository page, go to the pull requests tab and click the "New pull request" button.

    <p align="center"><img src="./.assets/creating_pull_request.png" alt="Create a pull request" style="width: 500px"/></p>

6. **Provide a description for your PR**

    You will be redirected to the pull request creation page. On this page, you need to provide basic information about your token. There is no strict template for creating PR.

7. **Submit PR**

    Click on the "Create pull request" button to complete the PR creation.

8. **Make sure your token metadata pass the well-formedness check**

    After creating the PR, GitHub will launch an action that will check that the uploaded metadata is correctly formatted and does not contain errors. Make sure you pass this check, and if not, correct any errors in the metadata you are uploading.

## Approval process

After PR creation, you don't need to ask for someone to check your PR as they are monitored regularly. Someone from the Cardano token registry team will check your PR and merge it or leave a comment if something was done wrong.
