# Create a Data Solution on Azure Synapse Analytics with Snapshot Serengeti: A step by step guide for beginners. 

This will be the first article in a four-part series on building an end-to-end data analytics and machine learning solution on azure synapse analytics. 

The data used in this solution is the Snapshot Serengeti data set which is a large-scale dataset of camera trap images. To learn more about this dataset see https://lila.science/datasets/snapshot-serengeti. 

By the end of this series, you’ll learn how to transform and analyze this data then use it to train classification ML model to classify the camera trap images to one of the 48 species in the dataset. 

The solution described in this article combines a range of Azure Services that will ingest, store, transform and serve data and insights from different sources. i.e, 

1. Semi-structured data - these are Json files that contain the split of the dataset into train, test and validation sets.
2. Unstructured data - these are the images in the dataset and also the zipped files that contain the metadata of the images.

    ![](/snapshot-serengeti-synapse/images/Azure%20Data%20Lab-%20with%20Sanpshot%20Serengeti.png)

There are different ways to building this data solution but we'll go with one that allows you to interact with most of the services on Azure synapse. Before proceeding check the set up instruction as explained in this  GitHub repository: https://github.com/Jcardif/serengetidatalab on how to deploy the resources needed for this solution to azure.

Now that you have successfully deployed the resources needed for this solution, the remainder of this article will look at how we load the data into the [storage account](https://azure.microsoft.com/en-gb/free/storage/?WT.mc_id=data-89327-jndemenge), [transform the data](https://learn.microsoft.com/en-US/Azure/synapse-analytics/synapse-notebook-activity?WT.mc_id=data-89327-jndemenge&tabs=classical) and finally visualize it using [Power Bi](https://powerbi.microsoft.com/en-us/getting-started-with-power-bi/?WT.mc_id=data-89327-jndemenge).

 
 To begin, launch the Synapse Studio and navigate to the **Manage** hub to create a new **Linked Service**. Linked services in Synapse are used to connect to external resources. In this case we'll be linking Azure Key Vault to the Synapse workspace. This will allow us to retrieve stored credentials from the key vault.
 
Click on **New** and search for **Key Vault**. Select the **Key Vault** option and click on **Continue**. In the dialog that appears, provide a name for the linked service, select your subscription and the key vault name then commit.

![](/snapshot-serengeti-synapse//images/vault_linked_service.png)




