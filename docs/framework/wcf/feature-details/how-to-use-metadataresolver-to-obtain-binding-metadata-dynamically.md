---
title: '方法 : MetadataResolver を使用してバインディング メタデータを動的に取得する'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: cffe47f301c1943a0d97e3a95a5b7c24979b4f69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490680"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="597ef-102">方法 : MetadataResolver を使用してバインディング メタデータを動的に取得する</span><span class="sxs-lookup"><span data-stu-id="597ef-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="597ef-103">ここでは、<xref:System.ServiceModel.Description.MetadataResolver> クラスを使用してバインディング メタデータを動的に取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="597ef-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="597ef-104">バインディング メタデータを動的に取得するには</span><span class="sxs-lookup"><span data-stu-id="597ef-104">To dynamically obtain binding metadata</span></span>  
  
1.  <span data-ttu-id="597ef-105">メタデータ エンドポイントのアドレスを持つ <xref:System.ServiceModel.EndpointAddress> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="597ef-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  <span data-ttu-id="597ef-106">サービス型とメタデータ エンドポイント アドレスを渡して、<xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="597ef-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="597ef-107">これにより、指定したコントラクトを実装したエンドポイントのコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="597ef-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="597ef-108">メタデータからはバインディング情報のみがインポートされます。コントラクト情報はインポートされません。</span><span class="sxs-lookup"><span data-stu-id="597ef-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="597ef-109">提供されたコントラクトが代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="597ef-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  <span data-ttu-id="597ef-110">これで、サービス エンドポイントのコレクションを反復処理して必要なバインディング情報を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="597ef-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="597ef-111">次のコードは、エンドポイントを反復処理し、現在のエンドポイントに関連付けられたバインディングとアドレスを渡すサービス クライアント オブジェクトを作成し、そのサービスでメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="597ef-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="597ef-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="597ef-112">See Also</span></span>  
 [<span data-ttu-id="597ef-113">メタデータ</span><span class="sxs-lookup"><span data-stu-id="597ef-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
