---
title: Navigate 演算子でリレーションシップをナビゲートする方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: 3db44ccee4420423072fc256dbed888c78fc4417
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="1f3ac-102">Navigate 演算子でリレーションシップをナビゲートする方法</span><span class="sxs-lookup"><span data-stu-id="1f3ac-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="1f3ac-103">このトピックでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して概念モデルに対してコマンドを実行する方法と、<xref:System.Data.Metadata.Edm.RefType> を使用して <xref:System.Data.EntityClient.EntityDataReader> の結果を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f3ac-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="1f3ac-104">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="1f3ac-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="1f3ac-105">追加、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)をプロジェクトに使用してプロジェクトを構成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="1f3ac-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="1f3ac-106">詳細については、次を参照してください。[する方法: Entity Data Model ウィザードを使用して](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)です。</span><span class="sxs-lookup"><span data-stu-id="1f3ac-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="1f3ac-107">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="1f3ac-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="1f3ac-108">例</span><span class="sxs-lookup"><span data-stu-id="1f3ac-108">Example</span></span>  
 <span data-ttu-id="1f3ac-109">次の例でのリレーションシップを移動する方法を示します[!INCLUDE[esql](../../../../../includes/esql-md.md)]を使用して、[移動](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)演算子。</span><span class="sxs-lookup"><span data-stu-id="1f3ac-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="1f3ac-110">`Navigate`演算子は、次のパラメーターを取ります: エンティティ、リレーションシップの種類、リレーションシップの端とのリレーションシップの先頭のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="1f3ac-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="1f3ac-111">必要に応じて、エンティティとリレーションシップ型のインスタンスのみを渡すことができます、`Navigate`演算子。</span><span class="sxs-lookup"><span data-stu-id="1f3ac-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="1f3ac-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f3ac-112">See Also</span></span>  
 [<span data-ttu-id="1f3ac-113">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1f3ac-113">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [<span data-ttu-id="1f3ac-114">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="1f3ac-114">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
