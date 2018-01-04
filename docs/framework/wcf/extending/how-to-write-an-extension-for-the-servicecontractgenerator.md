---
title: "方法 : ServiceContractGenerator の拡張を記述する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c62aa9ac582e93bb86399472e47c41fdb6fad2d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="1c202-102">方法 : ServiceContractGenerator の拡張を記述する</span><span class="sxs-lookup"><span data-stu-id="1c202-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="1c202-103">このトピックでは、<xref:System.ServiceModel.Description.ServiceContractGenerator> の拡張を記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c202-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="1c202-104">これは、操作の動作に <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> インターフェイスを実装するか、コントラクトの動作に <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> インターフェイスを実装することで可能になります。</span><span class="sxs-lookup"><span data-stu-id="1c202-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="1c202-105">このトピックでは、<xref:System.ServiceModel.Description.IServiceContractGenerationExtension> インターフェイスをコントラクト動作に実装する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1c202-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="1c202-106"><xref:System.ServiceModel.Description.ServiceContractGenerator> は、サービス コントラクト、クライアント型、およびクライアント構成を <xref:System.ServiceModel.Description.ServiceEndpoint>、<xref:System.ServiceModel.Description.ContractDescription>、<xref:System.ServiceModel.Channels.Binding> の各インターフェイスから生成します。</span><span class="sxs-lookup"><span data-stu-id="1c202-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="1c202-107">通常は、サービス メタデータから <xref:System.ServiceModel.Description.ServiceEndpoint>、<xref:System.ServiceModel.Description.ContractDescription>、および <xref:System.ServiceModel.Channels.Binding> インスタンスをインポートし、これらのインスタンスを使用してサービスを呼び出すコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="1c202-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="1c202-108">この例では、<xref:System.ServiceModel.Description.IWsdlImportExtension> の実装を使用して WSDL 注釈を処理し、生成されたコードに関するコメントを生成するために、インポートしたコントラクトにコード生成拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c202-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="1c202-109">ServiceContractGenerator の拡張を記述するには</span><span class="sxs-lookup"><span data-stu-id="1c202-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1.  <span data-ttu-id="1c202-110"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension> を実装します。</span><span class="sxs-lookup"><span data-stu-id="1c202-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="1c202-111">生成されたサービス コントラクトを変更するには、<xref:System.ServiceModel.Description.ServiceContractGenerationContext> メソッドに渡された <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1c202-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2.  <span data-ttu-id="1c202-112">同じクラスに <xref:System.ServiceModel.Description.IWsdlImportExtension> を実装します。</span><span class="sxs-lookup"><span data-stu-id="1c202-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="1c202-113"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> メソッドは、インポートされた <xref:System.ServiceModel.Description.ContractDescription> インスタンスにコード生成拡張を追加することによって、特定の WSDL 拡張 (この場合は WSDL 注釈) を処理できます。</span><span class="sxs-lookup"><span data-stu-id="1c202-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
    ```  
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
       {  
                // Contract documentation  
             if (context.WsdlPortType.Documentation != null)  
             {  
                    context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
             }  
             // Operation documentation  
             foreach (Operation operation in context.WsdlPortType.Operations)  
             {  
                if (operation.Documentation != null)  
                {  
                   OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
                   if (operationDescription != null)  
                   {  
                            operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
                   }  
                }  
             }  
          }  
          public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)   
            {  
                Console.WriteLine("BeforeImport called.");  
            }  
  
          public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)   
            {  
                Console.WriteLine("ImportEndpoint called.");  
            }  
    ```  
  
3.  <span data-ttu-id="1c202-114">クライアント構成に WSDL インポーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="1c202-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4.  <span data-ttu-id="1c202-115">クライアント コードで、`MetadataExchangeClient` を作成して `GetMetadata` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1c202-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5.  <span data-ttu-id="1c202-116">`WsdlImporter` を作成して `ImportAllContracts` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1c202-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6.  <span data-ttu-id="1c202-117">`ServiceContractGenerator` を作成して、コントラクトごとに `GenerateServiceContractType` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1c202-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7.  <span data-ttu-id="1c202-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> を実装する特定のコントラクトのコントラクト動作ごとに、<xref:System.ServiceModel.Description.IServiceContractGenerationExtension> が自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1c202-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="1c202-119">その後、渡された <xref:System.ServiceModel.Description.ServiceContractGenerationContext> をこのメソッドで変更できます。</span><span class="sxs-lookup"><span data-stu-id="1c202-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="1c202-120">この例では、コメントが追加されています。</span><span class="sxs-lookup"><span data-stu-id="1c202-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c202-121">参照</span><span class="sxs-lookup"><span data-stu-id="1c202-121">See Also</span></span>  
 [<span data-ttu-id="1c202-122">メタデータ</span><span class="sxs-lookup"><span data-stu-id="1c202-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="1c202-123">方法 : カスタム WSDL をインポートする</span><span class="sxs-lookup"><span data-stu-id="1c202-123">How to: Import Custom WSDL</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
