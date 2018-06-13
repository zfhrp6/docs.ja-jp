---
title: ローカル メソッド呼び出し
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 366c174a13e9a1a1928ef943febf199ae8485dfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352439"
---
# <a name="local-method-calls"></a><span data-ttu-id="2d5f2-102">ローカル メソッド呼び出し</span><span class="sxs-lookup"><span data-stu-id="2d5f2-102">Local Method Calls</span></span>
<span data-ttu-id="2d5f2-103">ローカル メソッド呼び出しとは、オブジェクト モデル内で実行される呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="2d5f2-104">リモート メソッド呼び出しとは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が SQL に変換し、データベース エンジンに送信して実行される呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="2d5f2-105">ローカル メソッド呼び出しが必要なときに[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL への呼び出しを変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="2d5f2-106">それ以外の場合、<xref:System.InvalidOperationException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="2d5f2-107">例 1</span><span class="sxs-lookup"><span data-stu-id="2d5f2-107">Example 1</span></span>  
 <span data-ttu-id="2d5f2-108">次の例では、`Order` クラスは Northwind サンプル データベースの Orders テーブルに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="2d5f2-109">このクラスには、ローカル インスタンス メソッドが追加されています。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="2d5f2-110">クエリ 1 では、`Order` クラスのコンストラクターがローカルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="2d5f2-111">クエリ 2 では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が `LocalInstanceMethod()` を SQL に変換しようとすると、処理は失敗し、<xref:System.InvalidOperationException> 例外がスローされるはずです。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="2d5f2-112">しかし、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ではローカル メソッド呼び出しがサポートされているため、クエリ 2 で例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="2d5f2-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2d5f2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d5f2-113">See Also</span></span>  
 [<span data-ttu-id="2d5f2-114">背景情報</span><span class="sxs-lookup"><span data-stu-id="2d5f2-114">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
