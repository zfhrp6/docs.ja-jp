---
title: LINQ to SQL の主な機能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 719c2e5c97d3f8c64de53831ac50b2e7156a38fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356419"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="5a3c7-102">LINQ to SQL の主な機能</span><span class="sxs-lookup"><span data-stu-id="5a3c7-102">What You Can Do With LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5a3c7-103"> は、SQL 開発者が期待するすべての主要な機能に対応しています。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-103"> supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="5a3c7-104">情報の照会、テーブルへの情報の挿入、およびテーブルの情報の更新と削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="5a3c7-105">選択</span><span class="sxs-lookup"><span data-stu-id="5a3c7-105">Selecting</span></span>  
 <span data-ttu-id="5a3c7-106">選択 (*射影*) は、 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリを任意のプログラミング言語で記述し、そのクエリを実行して結果を取得することにより実現されます。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-106">Selecting (*projection*) is achieved by just writing a [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5a3c7-107"> 自体は、必要なすべての操作を、使い慣れた SQL の操作に変換します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-107"> itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="5a3c7-108">詳細については、「 [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-108">For more information, see [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="5a3c7-109">次の例では、ロンドン在住の顧客の会社名を取得し、コンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="5a3c7-110">挿入</span><span class="sxs-lookup"><span data-stu-id="5a3c7-110">Inserting</span></span>  
 <span data-ttu-id="5a3c7-111">SQL の `Insert`を実行するには、前もって作成したオブジェクト モデルにオブジェクトを追加し、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の <xref:System.Data.Linq.DataContext>を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="5a3c7-112">`Customers` を使って、新規の顧客の情報を <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>テーブルに追加する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="5a3c7-113">Updating</span><span class="sxs-lookup"><span data-stu-id="5a3c7-113">Updating</span></span>  
 <span data-ttu-id="5a3c7-114">データベース エントリの `Update` (更新) を実行するには、目的の項目をまず取得し、それをオブジェクト モデル内で直接編集します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="5a3c7-115">オブジェクトを変更した後で、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の <xref:System.Data.Linq.DataContext> を呼び出してデータベースを更新します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="5a3c7-116">ロンドン出身のすべての顧客を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="5a3c7-117">その後で、市の名前を "London" から "London - Metro" に変更します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="5a3c7-118">最後に、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出して、変更をデータベースに送信します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="5a3c7-119">Deleting</span><span class="sxs-lookup"><span data-stu-id="5a3c7-119">Deleting</span></span>  
 <span data-ttu-id="5a3c7-120">項目を `Delete` (削除) するには、項目を所属先のコレクションから削除してから、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の <xref:System.Data.Linq.DataContext> を呼び出して、変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5a3c7-121"> 連鎖削除操作は認識されません。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-121"> does not recognize cascade-delete operations.</span></span> <span data-ttu-id="5a3c7-122">制約を持つテーブルの行を削除する場合を参照してください[する方法: 行をデータベースから削除](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="5a3c7-123">次の例では、 `CustomerID` が `98128` の顧客をデータベースから取得します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="5a3c7-124">次に、顧客の行が取得されたことを確認した後で、 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> を呼び出して、このオブジェクトをコレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="5a3c7-125">最後に、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出して、削除をデータベースに転送します。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5a3c7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a3c7-126">See Also</span></span>  
 [<span data-ttu-id="5a3c7-127">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5a3c7-127">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="5a3c7-128">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="5a3c7-128">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="5a3c7-129">はじめに</span><span class="sxs-lookup"><span data-stu-id="5a3c7-129">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
