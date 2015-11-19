{
    "handler": "Microsoft.Compute.MultiVm",
    "version": "0.0.1-preview",
    "parameters": {
        "basics": [
            {
                "name": "adminUsername",
                "type": "Microsoft.Compute.UserNameTextBox",
                "label": "Username",
                "toolTip": "Admin username for the virtual machines.",
                "osPlatform": "Windows"
            },
            {
                "name": "adminPassword",
                "type": "Microsoft.Compute.CredentialsCombo",
                "label": {
                    "password": "Password",
                    "confirmPassword": "Confirm password"
                },
                "toolTip": {
                    "password": "Admin password for the virtual machines."
                },
                "osPlatform": "Windows"
            }
        ],
        "steps": [
            {
                "name": "infrastructureConfig",
                "label": "Infrastructure settings",
                "subLabel": {
                    "preValidation": "Configure the infrastructure settings",
                    "postValidation": "Done"
                },
                "bladeTitle": "Infrastructure settings",
                "elements": [
					{
					  "name": "NodeType",
					  "type": "Microsoft.Common.DropDown",
					  "label": "PI Node Type",
					  "defaultValue": "Single Box",
					  "toolTip": "",
					  "constraints": {
						  "allowedValues": [
						  {
							  "label": "Single Box",
							  "value": 0
						  },
						  {
							  "label": "AF Server",
							  "value": 1
						  },
						  {
							  "label": "PI Data Archive",
							  "value": 2
						  },
						  {
							  "label": "Data Access",
							  "value": 3
						  },
						  {
							  "label": "PI Clients",
							  "value": 4
						  },
						  {
							  "label": "PI Interface/Connector",
							  "value": 5
						  }
						]
					  }
					},
                    {
                        "name": "storageAccount",
                        "type": "Microsoft.Storage.StorageAccountSelector",
                        "label": "Storage account",
                        "defaultValue": {
                            "type": "Standard_LRS"
                        }
                    },
                    {
                        "name": "vmSize",
                        "type": "Microsoft.Compute.SizeSelector",
                        "label": "Virtual machine size",
                        "toolTip": "The size of the virtual machine for the domain controller.",
                        "recommendedSizes": [
                            "Standard_D4",
                            "Standard_DS4",
                            "Standard_DS14"
                        ],
                        "constraints": {
                            "allowedSizes": [
                              "Standard_D1",
                              "Standard_D2",
                              "Standard_D3",
                              "Standard_D4",
                              "Standard_D11",
                              "Standard_D12",
                              "Standard_D13",
                              "Standard_D14",
							  "Standard_DS4",
							  "Standard_DS14"
                            ]
                        },
                        "osPlatform": "Windows",
                        "imageReference": {
                            "publisher": "MicrosoftWindowsServer",
                            "offer": "WindowsServer",
                            "sku": "2012-R2-Datacenter"
                        },
                        "count": "[steps('infrastructureConfig').vmCount]"
                    },
                    {
                      "name": "dnsAndPublicIP",
                      "type": "Microsoft.Network.PublicIpAddressCombo",
                      "label": {
                        "publicIpAddress": "Public IP address",
                        "domainNameLabel": "DNS Prefix"
                      },
                      "toolTip": {
                        "domainNameLabel": "DNS Prefix for the VM public IP addresses."
                      },
                      "defaultValue": {
                        "publicIpAddressName": "publicIP"
                      },
                      "options": {
                        "hideNone": true
                      }
                    }
                ]
            }
        ],
        "outputs": {
            "location": "[location()]",
            "adminUsername": "[steps('basics').adminUsername]",
            "adminPassword": "[steps('basics').adminPassword]",
            "storageAccountNewOrExisting" : "[steps('infrastructureConfig').storageAccount.newOrExisting]",
            "StorageAccountName": "[steps('infrastructureConfig').storageAccount.name]",
            "storageAccountType": "[steps('infrastructureConfig').storageAccount.type]",
			"existingStorageAccountRG": "[steps('infrastructureConfig').storageAccount.resourceGroup]",
            "domainName": "[steps('infrastructureConfig').domainName]",
            "vmSize": "[steps('infrastructureConfig').vmSize]",
            "publicIPAddressName": "[steps('infrastructureConfig').DnsAndPublicIP.name]",
            "dnsNameForPublicIP": "[steps('infrastructureConfig').dnsAndPublicIP.domainNameLabel]",
			"existingIPRGName": "[steps('infrastructureConfig').dnsAndPublicIP.resourceGroup]",
			"publicIPNewOrExisting": "[steps('infrastructureConfig').dnsAndPublicIP.newOrExistingOrNone]"
        }
    }
}
