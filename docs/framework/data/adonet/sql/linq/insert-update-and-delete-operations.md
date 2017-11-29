---
title: "挿入、更新、および削除の各操作"
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
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: adbe7faa50b06c330b942b451d5a4a0bd832cde3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="a9dc6-102">挿入、更新、および削除の各操作</span><span class="sxs-lookup"><span data-stu-id="a9dc6-102">Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="a9dc6-103">オブジェクト モデルに対してオブジェクトの追加、変更、および削除を行うには、`Insert` で `Update`、`Delete`、および [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の各操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-103">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="a9dc6-104">既定では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって SQL に対する操作が変換され、変更内容がデータベースに送信されます。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a9dc6-105">オブジェクトに加えた変更を永続化の操作と最大限の柔軟性を提供します。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-105"> offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="a9dc6-106">クエリによって取得するか新規に作成することによりエンティティ オブジェクトが使用可能になった後で、通常のオブジェクトと同じようにそれらのオブジェクトをアプリケーションで変更できます。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-106">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="a9dc6-107">つまり、その値を変更することができます、コレクションに追加することができます、それらをコレクションから削除することができます。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-107">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a9dc6-108"> では変更履歴が保持されるため、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、変更内容をデータベースに送信できます。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-108"> tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a9dc6-109"> は連鎖削除操作をサポートせず、認識もしません。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-109"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="a9dc6-110">設定する必要がありますに対して制約を持つテーブルの行を削除する場合、`ON DELETE CASCADE`データベース内の外部キー制約での規則や独自のコードを使用して、まず親オブジェクトが削除されないようにする子オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-110">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="a9dc6-111">それ以外の場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="a9dc6-112">詳細については、次を参照してください。[する方法: 行をデータベースから削除](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-112">For more information, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="a9dc6-113">次の例では、Northwind サンプル データベースの `Customer` クラスと `Order` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-113">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="a9dc6-114">簡潔にするため、ここではクラス定義を省いています。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-114">Class definitions are not shown for brevity.</span></span>  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 <span data-ttu-id="a9dc6-115"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、変更内容をデータベースに送信する SQL コマンドが [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって自動的に生成され、実行されます。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-115">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9dc6-116">独自に作成したロジック (通常はストアド プロシージャ) を使用して、この動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-116">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="a9dc6-117">詳細については、次を参照してください。[をオーバーライドする既定の動作の開発者の責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-117">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>  
>   
>  <span data-ttu-id="a9dc6-118">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している開発者は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用して、この用途のストアド プロシージャを開発できます。</span><span class="sxs-lookup"><span data-stu-id="a9dc6-118">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for this purpose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9dc6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9dc6-119">See Also</span></span>  
 [<span data-ttu-id="a9dc6-120">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="a9dc6-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="a9dc6-121">カスタマイズの挿入、更新、および Delete 操作</span><span class="sxs-lookup"><span data-stu-id="a9dc6-121">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
