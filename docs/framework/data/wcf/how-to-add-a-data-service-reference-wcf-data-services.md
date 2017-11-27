---
title: "方法: データ サービス参照を追加する (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8fb075bdb17f0d562d752bc4125141bb0bb2ab9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="47131-102">方法: データ サービス参照を追加する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="47131-102">How to: Add a Data Service Reference (WCF Data Services)</span></span>
<span data-ttu-id="47131-103">使用することができます、**サービス参照の追加**への参照を追加する Visual Studio でのダイアログ[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="47131-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="47131-104">参照をデータ サービスに追加すると、Visual Studio で開発したクライアント アプリケーションのデータ サービスに容易にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="47131-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="47131-105">この手順を完了すると、データ サービスから取得されたメタデータに基づいてデータ クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="47131-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="47131-106">詳細については、次を参照してください。[データ サービス クライアント ライブラリを生成する](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="47131-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>  
  
### <a name="to-add-a-data-service-reference"></a><span data-ttu-id="47131-107">データ サービス参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="47131-107">To add a data service reference</span></span>  
  
1.  <span data-ttu-id="47131-108">(オプション) データ サービスがソリューションの一部ではなく、実行していない場合は、データ サービスを開始して、データ サービスの URI を記録します。</span><span class="sxs-lookup"><span data-stu-id="47131-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>  
  
2.  <span data-ttu-id="47131-109">クライアント プロジェクトを右クリックし、**サービス参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="47131-109">Right-click the client project and then select **Add Service Reference**.</span></span>  
  
3.  <span data-ttu-id="47131-110">データ サービスが、現在のソリューションの一部の場合は、クリックして**Discover**です。</span><span class="sxs-lookup"><span data-stu-id="47131-110">If the data service is part of the current solution, click **Discover**.</span></span>  
  
     <span data-ttu-id="47131-111">または</span><span class="sxs-lookup"><span data-stu-id="47131-111">-or-</span></span>  
  
     <span data-ttu-id="47131-112">**アドレス**ボックスに、データ サービスのベース URL を入力するように`http://localhost:1234/Northwind.svc`、クリックして**移動**です。</span><span class="sxs-lookup"><span data-stu-id="47131-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>  
  
4.  <span data-ttu-id="47131-113">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47131-113">Click **OK**.</span></span>  
  
     <span data-ttu-id="47131-114">新しいコード ファイルが追加されます。このコード ファイルには、データ サービス リソースにアクセスし、オブジェクトとしてデータ サービス リソースと対話するデータ クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="47131-114">This adds a new code file that contains the data classes that are used to access and interact with data service resources as objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47131-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="47131-115">See Also</span></span>  
 [<span data-ttu-id="47131-116">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="47131-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
