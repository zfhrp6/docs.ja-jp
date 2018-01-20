---
title: "データ サービス クライアント ライブラリの生成 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72b75451d69e107b78152b301027f902ff77a25d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="6bf92-102">データ サービス クライアント ライブラリの生成 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="6bf92-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="6bf92-103">実装するデータ サービス、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]によって公開されているデータ モデルを記述したサービス メタデータ ドキュメントを返すことができます、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。</span><span class="sxs-lookup"><span data-stu-id="6bf92-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="6bf92-104">詳細については、次を参照してください。 [OData: サービス メタデータ ドキュメント](http://go.microsoft.com/fwlink/?LinkId=186070)です。</span><span class="sxs-lookup"><span data-stu-id="6bf92-104">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="6bf92-105">使用することができます、**サービス参照の追加**への参照を追加する Visual Studio でのダイアログ、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-ベースのサービスです。</span><span class="sxs-lookup"><span data-stu-id="6bf92-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="6bf92-106">によって返されるメタデータへの参照を追加するこのツールを使用する場合、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]クライアント プロジェクトでのフィードを次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="6bf92-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
-   <span data-ttu-id="6bf92-107">データ サービスからのサービス メタデータ ドキュメントが要求され、返されたメタデータが解釈されます。</span><span class="sxs-lookup"><span data-stu-id="6bf92-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6bf92-108">返されたメタデータは、クライアント プロジェクトに .edmx ファイルとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="6bf92-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="6bf92-109">.edmx ファイルは、Entity Framework で使用される .edmx ファイルと形式が異なるので、Entity Data Model デザイナーを使用して開くことができません。</span><span class="sxs-lookup"><span data-stu-id="6bf92-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="6bf92-110">このメタデータ ファイルは、XML エディターまたは任意のテキスト エディターを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="6bf92-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="6bf92-111">詳細については、次を参照してください、 [ \[MC-EDMX\]: データ サービスのパッケージ形式の Entity Data Model](http://go.microsoft.com/fwlink/?LinkID=178833)仕様。</span><span class="sxs-lookup"><span data-stu-id="6bf92-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
-   <span data-ttu-id="6bf92-112"><xref:System.Data.Services.Client.DataServiceContext> から継承するエンティティ コンテナー クラスとしてサービスの表現が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf92-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="6bf92-113">この生成されたエンティティ コンテナー クラスは、Entity Data Model ツールが生成するエンティティ コンテナーに似ています。</span><span class="sxs-lookup"><span data-stu-id="6bf92-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="6bf92-114">詳細は、[Object Services の概要 (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6bf92-114">For more information, see [Object Services Overview (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span></span>  
  
-   <span data-ttu-id="6bf92-115">サービス メタデータ内で見つかったデータ モデル型のデータ クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf92-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
-   <span data-ttu-id="6bf92-116">`System.Data.Services.Client` アセンブリへの参照がプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6bf92-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="6bf92-117">詳細については、次を参照してください。[する方法: データ サービス参照の追加](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bf92-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="6bf92-118">使用して、クライアント データ サービス クラスを生成することも、 [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)コマンド プロンプト ツールです。</span><span class="sxs-lookup"><span data-stu-id="6bf92-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="6bf92-119">詳細については、次を参照してください。[する方法: 手動で生成クライアント データ サービス クラス](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bf92-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="6bf92-120">クライアント データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="6bf92-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="6bf92-121">使用すると、**サービス参照の追加**Visual Studio でのダイアログまたは`DataSvcUtil.exe`に基づくクライアント データ クラスを生成するツール、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィード、.NET Framework のデータ型はプリミティブ型からの型にマップされます、データ モデル次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6bf92-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="6bf92-122">データ モデル型</span><span class="sxs-lookup"><span data-stu-id="6bf92-122">Data model type</span></span>|<span data-ttu-id="6bf92-123">.NET Framework データ型</span><span class="sxs-lookup"><span data-stu-id="6bf92-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="6bf92-124"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="6bf92-124"><xref:System.Byte> `[]`</span></span>|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 <span data-ttu-id="6bf92-125">詳細については、次を参照してください。 [OData: プリミティブ データ型](http://go.microsoft.com/fwlink/?LinkId=186072)です。</span><span class="sxs-lookup"><span data-stu-id="6bf92-125">For more information, see [OData: Primitive Data Types](http://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf92-126">参照</span><span class="sxs-lookup"><span data-stu-id="6bf92-126">See Also</span></span>  
 [<span data-ttu-id="6bf92-127">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="6bf92-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="6bf92-128">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="6bf92-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
