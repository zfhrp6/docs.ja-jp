---
title: "接続文字列を定義する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 355d313fd607ccf85ba55b09b9ece4d9c88e298f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="ed016-102">接続文字列を定義する方法</span><span class="sxs-lookup"><span data-stu-id="ed016-102">How to: Define the Connection String</span></span>
<span data-ttu-id="ed016-103">このトピックでは、概念モデルに接続するための接続文字列を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed016-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="ed016-104">このトピックの内容がに基づいて、 [AdventureWorks Sales](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)概念モデルです。</span><span class="sxs-lookup"><span data-stu-id="ed016-104">This topic is based on the [AdventureWorks Sales](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) conceptual model.</span></span> <span data-ttu-id="ed016-105">AdventureWorks Sales Model は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ドキュメントのタスク関連のトピック全般で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ed016-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="ed016-106">このトピックは、既に構成されていることを想定しています、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] AdventureWorks Sales Model が定義されているとします。</span><span class="sxs-lookup"><span data-stu-id="ed016-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ed016-107">詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルを手動で定義](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a)です。</span><span class="sxs-lookup"><span data-stu-id="ed016-107">For more information, see [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span></span> <span data-ttu-id="ed016-108">このトピックの手順が記載されても[する方法: Entity Framework プロジェクトを手動で構成](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)です。</span><span class="sxs-lookup"><span data-stu-id="ed016-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed016-109">[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] プロジェクトで [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] ウィザードを使用した場合、自動的に .edmx ファイルが生成され、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するようにプロジェクトが構成されます。</span><span class="sxs-lookup"><span data-stu-id="ed016-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="ed016-110">詳細については、次を参照してください[する方法: Entity Data Model ウィザードを使用する。](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)</span><span class="sxs-lookup"><span data-stu-id="ed016-110">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)</span></span>  
  
### <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="ed016-111">Entity Framework 接続文字列を定義するには</span><span class="sxs-lookup"><span data-stu-id="ed016-111">To define the Entity Framework connection string</span></span>  
  
-   <span data-ttu-id="ed016-112">プロジェクトのアプリケーション構成ファイル (app.config) を開き、次の接続文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="ed016-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>  
  
  
  
     <span data-ttu-id="ed016-113">プロジェクトが、アプリケーション構成ファイルを持たない場合、1 つを選択して、追加できます**新しい項目の追加**から、**プロジェクト** メニューを選択すると、**全般**カテゴリで、選択すると**アプリケーション構成ファイル**、クリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="ed016-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed016-114">参照</span><span class="sxs-lookup"><span data-stu-id="ed016-114">See Also</span></span>  
 [<span data-ttu-id="ed016-115">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="ed016-115">Quickstart</span></span>](http://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [<span data-ttu-id="ed016-116">方法: 新しい .edmx ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="ed016-116">How to: Create a New .edmx File</span></span>](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [<span data-ttu-id="ed016-117">ADO.NET Entity Data Model ツール</span><span class="sxs-lookup"><span data-stu-id="ed016-117">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
