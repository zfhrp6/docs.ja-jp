---
title: "クエリ プランのキャッシュ (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3b7a607d7bda72f1ce79405053f165e163c45386
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="b0adb-102">クエリ プランのキャッシュ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b0adb-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="b0adb-103">クエリの実行が試行されると、クエリ パイプラインではそのクエリ プランのキャッシュを検索し、同じクエリが既にコンパイルされ使用可能になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0adb-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="b0adb-104">使用可能になっている場合は、新しいクエリを構築する代わりに、キャッシュされたプランを再利用します。</span><span class="sxs-lookup"><span data-stu-id="b0adb-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="b0adb-105">クエリ プランのキャッシュ内に一致するものが見つからない場合は、クエリがコンパイルされ、キャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="b0adb-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="b0adb-106">クエリはその [!INCLUDE[esql](../../../../../../includes/esql-md.md)] テキストとパラメーターのコレクション (名前と型) によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="b0adb-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="b0adb-107">テキストの比較では、常に大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="b0adb-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b0adb-108">構成</span><span class="sxs-lookup"><span data-stu-id="b0adb-108">Configuration</span></span>  
 <span data-ttu-id="b0adb-109">クエリ プランのキャッシュは <xref:System.Data.EntityClient.EntityCommand> を使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="b0adb-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="b0adb-110"><xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType> でクエリ プランのキャッシュを有効または無効にするには、このプロパティを `true` または `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b0adb-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="b0adb-111">2 回以上使用する予定がない個別の動的クエリ プランのキャッシュを無効にすると、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="b0adb-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="b0adb-112"><xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A> を使用してクエリ プランのキャッシュを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="b0adb-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="b0adb-113">推奨される使用方法</span><span class="sxs-lookup"><span data-stu-id="b0adb-113">Recommended Practice</span></span>  
 <span data-ttu-id="b0adb-114">一般的に、動的クエリは避けてください。</span><span class="sxs-lookup"><span data-stu-id="b0adb-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="b0adb-115">次の動的クエリ例は、検証を行わずにユーザー入力をそのまま受け入れるので、SQL インジェクション攻撃に対して脆弱です。</span><span class="sxs-lookup"><span data-stu-id="b0adb-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="b0adb-116">動的に生成されたクエリを使用する場合は、再利用される可能性の低いキャッシュ エントリのためにメモリが不必要に消費されないように、クエリ プランのキャッシュを無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b0adb-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="b0adb-117">静的クエリおよびパラメーター化クエリに対してクエリ プランをキャッシュすると、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="b0adb-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="b0adb-118">以下は、静的クエリの例です。</span><span class="sxs-lookup"><span data-stu-id="b0adb-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="b0adb-119">クエリ プランのキャッシュでクエリを適切に一致させるには、次の要件に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0adb-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
-   <span data-ttu-id="b0adb-120">クエリ テキストは定数パターンにする必要があり、最も望ましいのは定数文字列またはリソースです。</span><span class="sxs-lookup"><span data-stu-id="b0adb-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
-   <span data-ttu-id="b0adb-121">ユーザーが指定した値を渡す必要があるときは、<xref:System.Data.EntityClient.EntityParameter> または <xref:System.Data.Objects.ObjectParameter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="b0adb-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="b0adb-122">クエリ プランのキャッシュ内のスロットを必要以上に消費する次のようなクエリ パターンは避けます。</span><span class="sxs-lookup"><span data-stu-id="b0adb-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
-   <span data-ttu-id="b0adb-123">テキストの大文字または小文字の変更</span><span class="sxs-lookup"><span data-stu-id="b0adb-123">Changes to letter case in the text.</span></span>  
  
-   <span data-ttu-id="b0adb-124">空白への変更</span><span class="sxs-lookup"><span data-stu-id="b0adb-124">Changes to white space.</span></span>  
  
-   <span data-ttu-id="b0adb-125">リテラル値への変更</span><span class="sxs-lookup"><span data-stu-id="b0adb-125">Changes to literal values.</span></span>  
  
-   <span data-ttu-id="b0adb-126">コメント内のテキストの変更</span><span class="sxs-lookup"><span data-stu-id="b0adb-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0adb-127">参照</span><span class="sxs-lookup"><span data-stu-id="b0adb-127">See Also</span></span>  
 [<span data-ttu-id="b0adb-128">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="b0adb-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
