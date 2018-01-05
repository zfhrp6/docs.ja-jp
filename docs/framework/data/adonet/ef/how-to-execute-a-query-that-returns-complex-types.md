---
title: "複合型を返すクエリの実行方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0d39052b9ba818e74b28de2f4f0097d2b3299889
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="2daea-102">複合型を返すクエリの実行方法</span><span class="sxs-lookup"><span data-stu-id="2daea-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="2daea-103">このトピックでは、複合型プロパティを含むエンティティ型オブジェクトを返す [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2daea-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="2daea-104">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="2daea-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="2daea-105">追加、 [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)をプロジェクトに使用してプロジェクトを構成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="2daea-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="2daea-106">詳細については、次を参照してください。[する方法: Entity Data Model ウィザードを使用して](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)です。</span><span class="sxs-lookup"><span data-stu-id="2daea-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="2daea-107">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="2daea-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="2daea-108">モデルを表示する .edmx ファイルをダブルクリックして、[モデル ブラウザー ウィンドウ](http://msdn.microsoft.com/en-us/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd)エンティティ デザイナーのです。</span><span class="sxs-lookup"><span data-stu-id="2daea-108">Double click the .edmx file to display the model in the [Model Browser window](http://msdn.microsoft.com/en-us/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="2daea-109">エンティティ デザイナー画面で、選択、`Email`と`Phone`のプロパティ、`Contact`エンティティ型、し、右クリックして選択**新しい複合型にリファクター**です。</span><span class="sxs-lookup"><span data-stu-id="2daea-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="2daea-110">選択した場合は、新しい複合型`Email`と`Phone`にプロパティを追加、**モデル ブラウザー**です。</span><span class="sxs-lookup"><span data-stu-id="2daea-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="2daea-111">複合型で、既定の名前が指定されていること: 型の名前を変更`EmailPhone`で、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2daea-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="2daea-112">また、新しい `ComplexProperty` プロパティが `Contact` エンティティ型に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2daea-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="2daea-113">プロパティの名前を `EmailPhoneComplexType.` に変更します。</span><span class="sxs-lookup"><span data-stu-id="2daea-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="2daea-114">作成して、Entity Data Model ウィザードを使用した複合型の変更については、次を参照してください[する方法: 複合型プロパティへの既存のプロパティをリファクター](http://msdn.microsoft.com/en-us/5b2eb3b3-693d-42cb-b43a-405812d677eb)と[する方法: 作成との複合型の変更。](http://msdn.microsoft.com/en-us/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="2daea-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/en-us/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](http://msdn.microsoft.com/en-us/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2daea-115">例</span><span class="sxs-lookup"><span data-stu-id="2daea-115">Example</span></span>  
 <span data-ttu-id="2daea-116">次の例のコレクションを返すクエリを実行する`Contact`オブジェクトし、の 2 つのプロパティを表示、`Contact`オブジェクト:`ContactID`との値、`EmailPhoneComplexType`複合型。</span><span class="sxs-lookup"><span data-stu-id="2daea-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
