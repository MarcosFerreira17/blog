---
title: What is and how ARM Template works in Microsoft Azure
date: 2023-03-14T15:54:51-03:00
draft: true
description:
---The ARM Template is an Azure tool that enables the creation of infrastructure resources as code (IaC). It is used to deploy and manage Azure resources in a consistent, predictable, and repeatable way. With the ARM Template, it is possible to define the infrastructure topology, define the dependencies between resources, and specify the configurations of the resources to be deployed.

## **Advantages of ARM Template:**

- Improves consistency and facilitates reuse
- Reduces manual, error-prone, and repetitive tasks
- Express complex deployments
- Express requirements through code
- Provides validation tasks
- Modular and can be linked
- Simplifies orchestration

# **Template Schema**

The ARM Template Schema is used to define the structure and format of an ARM Template. It includes the definitions of resources, parameters, variables, and outputs that are used in the template. The schema version is also specified in the template to ensure that the correct version is being used. The schema is an essential part of creating a valid ARM Template and helps ensure that the deployment is successful.

## **Characteristics of the Template Schema:**

- Defines all Resource Manager resources in a deployment
- Written in JSON
- A collection of key-value pairs
- Each key is a string
- Each value can be a string, number, boolean expression, list of values, object

Here is an example of the schema of an ARM Template:

```json
{
  "$schema": "<https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#>",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "storageAccountType": {
      "type": "string",
      "defaultValue": "Standard_LRS",
      "allowedValues": [
        "Standard_LRS",
        "Standard_GRS",
        "Standard_ZRS",
        "Premium_LRS"
      ],
      "metadata": {
        "description": "Type of storage account to create."
      }
    }
  },
  "variables": {
    "storageAccountName": "[concat(uniquestring(resourceGroup().id), 'storage')]"
  },
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "apiVersion": "2019-04-01",
      "location": "[resourceGroup().location]",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {

      }
    }
  ],
  "outputs": {
    "storageAccountName": {
      "type": "string",
      "value": "[variables('storageAccountName')]"
    }
  }
}
```

This example defines a single resource, an Azure storage account, with the option to select the type of storage account to be used. The storage account name is dynamically generated based on the resource group ID and a unique string.

## **Template Parameters**

Template parameters are a fundamental part of the ARM Template. They are used to define the values that can be configured by the user in the template deployment, allowing deployments to be customized to meet specific needs. The parameters defined in the Template Schema are used to create the list of parameters available in the deployment. Each parameter has a name, a type, and a default value, which can be overridden by the user during deployment.

Here is a simple example of template parameters in an ARM Template:

```json
"parameters": {
  "vmName": {
    "type": "string",
    "defaultValue": "myVM",
    "metadata": {
      "description": "Nome da VM a ser criada."
    }
  },
  "adminUsername": {
    "type": "string",
    "defaultValue": "admin",
    "metadata": {
      "description": "Nome de usuário do administrador da VM."
    }
  },
  "adminPassword": {
    "type": "securestring",
    "metadata": {
      "description": "Senha do administrador da VM."
    }
  }
}

```

This example defines three parameters: **`vmName`**, **`adminUsername`**, and **`adminPassword`**. The default value for **`vmName`** is "myVM", the default value for **`adminUsername`** is "admin", and **`adminPassword`** is a secure value that is not displayed during deployment. Each parameter also has a description that describes what the parameter does.

# **Template Bicep**

Bicep is an infrastructure modeling language that builds on top of ARM Template. It provides a more concise and readable syntax than ARM Template, making it easier to create and maintain deployment models. Bicep is compiled into an ARM Template before deployment, so there is no difference in functionality between Bicep and ARM Template.

## **Characteristics of Bicep**

- Structured language with a cleaner syntax and fewer lines of code than ARM Template
- Strongly typed, which means it provides compile-time checking of code
- Can be used to create and manage resources across multiple Azure subscriptions and resource groups
- Enables modular code reuse and composition of templates
- Supports loops, conditions, and other advanced language features that make it easier to write complex templates
- Provides built-in functions for common tasks like string manipulation, arithmetic, and date/time conversion

Here is an example of a Bicep template that creates a virtual network, a subnet, and a virtual machine:

```powershell
param vnetName string
param subnetName string
param vmName string
param adminUsername string
param adminPassword securestring

resource vnet 'Microsoft.Network/virtualNetworks@2021-02-01' = {
  name: vnetName
  location: resourceGroup().location
  properties: {
    addressSpace: {
      addressPrefixes: [
        '10.0.0.0/16'
      ]
    }
  }
}

resource subnet 'Microsoft.Network/virtualNetworks/subnets@2021-02-01' = {
  name: '${vnet.name}/${subnetName}'
  properties: {
    addressPrefix: '10.0.1.0/24'
    virtualNetwork: {
      id: vnet.id
    }
  }
}

resource vm 'Microsoft.Compute/virtualMachines@2021-04-01' = {
  name: vmName
  location: resourceGroup().location
  properties: {
    hardwareProfile: {
      vmSize: 'Standard_B1ls'
    }
    storageProfile: {
      imageReference: {
        publisher: 'Canonical'
        offer: 'UbuntuServer'
        sku: '20.04-LTS'
        version: 'latest'
      }
      osDisk: {
        createOption: 'FromImage'
      }
    }
    osProfile: {
      computerName: vmName
      adminUsername: adminUsername
      adminPassword: adminPassword
    }
    networkProfile: {
      networkInterfaces: [
        {
          id: subnet.id
        }
      ]
    }
  }
}
```

This example defines five parameters that allow the user to specify the names of the virtual network, subnet, virtual machine, admin username, and password. The **`vnet`** resource creates a virtual network with an address space of **`10.0.0.0/16`**. The **`subnet`** resource creates a subnet within the virtual network with an address prefix of **`10.0.1.0/24`**. The **`vm`** resource creates a virtual machine with an Ubuntu Server image and connects it to the subnet.

# **Conclusion**

In summary, the ARM Template and Bicep are powerful tools for creating and managing infrastructure as code in Azure. They provide a structured way to define the topology and configuration of resources, simplify orchestration, and reduce the manual tasks prone to errors. By using these tools, organizations can improve their cloud infrastructure management, achieve better control over their resources, and reduce the risk of misconfigurations and security breaches. Additionally, the modularity of templates allows for easy reuse and sharing of code between teams, making it easier to collaborate on infrastructure projects.

It's worth noting that while these tools have their benefits, they can also have a steep learning curve, especially for those new to Infrastructure as Code. However, with practice and familiarity, developers and operations teams can become proficient in creating and managing infrastructure as code with ARM templates and Bicep.

Overall, the use of ARM templates and Bicep is highly recommended for organizations that want to streamline their Azure infrastructure management, reduce the potential for errors, and improve their overall cloud security posture. By embracing Infrastructure as Code, teams can more easily manage the complexities of the cloud and stay ahead of the curve in an ever-changing technology landscape.
