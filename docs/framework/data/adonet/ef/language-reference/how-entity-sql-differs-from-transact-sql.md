---
title: "Entity SQL と Transact-SQL の相違点"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3f80ec1ac51dded1f91d1a18c4d4e24836cf92cd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="8321f-102">Entity SQL と Transact-SQL の相違点</span><span class="sxs-lookup"><span data-stu-id="8321f-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="8321f-103">このトピックの違いを説明する[!INCLUDE[esql](../../../../../../includes/esql-md.md)]と[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="8321f-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="8321f-104">継承とリレーションシップのサポート</span><span class="sxs-lookup"><span data-stu-id="8321f-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-105">エンティティの概念スキーマを直接操作し、継承やリレーションシップなどの概念モデル機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8321f-105"> works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="8321f-106">継承を操作するときは、スーパータイプ インスタンスのコレクションからサブタイプのインスタンスを選択すると便利である場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="8321f-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="8321f-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)で演算子[!INCLUDE[esql](../../../../../../includes/esql-md.md)](のような`oftype`c# シーケンスで) この機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="8321f-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="8321f-108">コレクションのサポート</span><span class="sxs-lookup"><span data-stu-id="8321f-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-109">コレクションをファーストクラスのエンティティとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="8321f-109"> treats collections as first-class entities.</span></span> <span data-ttu-id="8321f-110">例:</span><span class="sxs-lookup"><span data-stu-id="8321f-110">For example:</span></span>  
  
-   <span data-ttu-id="8321f-111">コレクションの式は、`from` 句内で有効です。</span><span class="sxs-lookup"><span data-stu-id="8321f-111">Collection expressions are valid in a `from` clause.</span></span>  
  
-   <span data-ttu-id="8321f-112">`in` サブクエリと `exists` サブクエリは任意のコレクションを使用できるように一般化されています。</span><span class="sxs-lookup"><span data-stu-id="8321f-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="8321f-113">サブクエリは一種のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="8321f-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="8321f-114">`e1 in e2` および `exists(e)` は、これらの演算を実行する [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 構造です。</span><span class="sxs-lookup"><span data-stu-id="8321f-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
-   <span data-ttu-id="8321f-115">`union`、`intersect`、`except` などの集合演算は、現在ではコレクションに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="8321f-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
-   <span data-ttu-id="8321f-116">結合はコレクションに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="8321f-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="8321f-117">式のサポート</span><span class="sxs-lookup"><span data-stu-id="8321f-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="8321f-118">サブクエリ (テーブル) と式 (行と列) があります。</span><span class="sxs-lookup"><span data-stu-id="8321f-118"> has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="8321f-119">コレクションとを入れ子になったコレクションをサポートするために[!INCLUDE[esql](../../../../../../includes/esql-md.md)]はすべてを式。</span><span class="sxs-lookup"><span data-stu-id="8321f-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-120"> は [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] よりもコンポーザブルであり、すべての式をどこにでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="8321f-120"> is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="8321f-121">クエリ式は常に投射型のコレクションとなり、コレクション式が許可されている任意の場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8321f-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="8321f-122">について[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]でサポートされていない式[!INCLUDE[esql](../../../../../../includes/esql-md.md)]を参照してください[サポートされていない式](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="8321f-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="8321f-123">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリはすべて有効です。</span><span class="sxs-lookup"><span data-stu-id="8321f-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="8321f-124">サブクエリの一貫した処理</span><span class="sxs-lookup"><span data-stu-id="8321f-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="8321f-125">テーブルに重点を[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]サブクエリのコンテキストを解釈を実行します。</span><span class="sxs-lookup"><span data-stu-id="8321f-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="8321f-126">内のサブクエリなど、`from`句は、マルチセット (テーブル) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="8321f-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="8321f-127">ただし、`select` 句で使用される同じサブクエリは、スカラー サブクエリと見なされます。</span><span class="sxs-lookup"><span data-stu-id="8321f-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="8321f-128">同様に、サブクエリの左側に使用される、`in`演算子は、スカラー サブクエリの場合は、右側にあるは、サブクエリはマルチセット サブクエリをする必要があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="8321f-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-129"> ではこれらの違いが排除されます。</span><span class="sxs-lookup"><span data-stu-id="8321f-129"> eliminates these differences.</span></span> <span data-ttu-id="8321f-130">式は、使用するコンテキストに依存しない、一貫した方法で解釈されます。</span><span class="sxs-lookup"><span data-stu-id="8321f-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-131">すべてのサブクエリはマルチセット サブクエリと見なします。</span><span class="sxs-lookup"><span data-stu-id="8321f-131"> considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="8321f-132">サブクエリ、スカラー値が必要な場合の[!INCLUDE[esql](../../../../../../includes/esql-md.md)]提供、`anyelement`はコレクション (この場合はサブクエリ) に対して演算を行い、コレクションからシングルトン値を抽出する演算子です。</span><span class="sxs-lookup"><span data-stu-id="8321f-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="8321f-133">サブクエリの暗黙の強制型変換の回避</span><span class="sxs-lookup"><span data-stu-id="8321f-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="8321f-134">サブクエリの一貫した処理に伴う二次的作用として、スカラー値へのサブクエリの暗黙的な変換があります。</span><span class="sxs-lookup"><span data-stu-id="8321f-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="8321f-135">具体的には、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] では、単一フィールドの行のマルチセットはそのフィールドのデータ型を持つスカラー値に暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8321f-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-136"> では、この暗黙の強制型変換をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-136"> does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-137"> では、コレクションからシングルトン値を抽出するための ANYELEMENT 演算子と、クエリ式の実行中に row ラッパーの作成を回避するための `select value` 句が提供されています。</span><span class="sxs-lookup"><span data-stu-id="8321f-137"> provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="8321f-138">SELECT VALUE: 暗黙の row ラッパーの回避</span><span class="sxs-lookup"><span data-stu-id="8321f-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="8321f-139">Select 句、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]サブクエリでは、句で、項目の周辺の row ラッパーを暗黙的に作成します。</span><span class="sxs-lookup"><span data-stu-id="8321f-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="8321f-140">これは、スカラーやオブジェクトのコレクションを作成できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="8321f-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="8321f-141">1 つのフィールドの rowtype と、同じデータ型の単一値の間の暗黙の強制変換を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8321f-141"> allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-142"> には、暗黙の行の構築をスキップする `select value` 句が用意されています。</span><span class="sxs-lookup"><span data-stu-id="8321f-142"> provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="8321f-143">`select value` 句には 1 つの項目のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8321f-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="8321f-144">このような句を使用した場合、`select` 句内の項目には row ラッパーは構築されず、目的の構造を持つコレクションを作成できます。たとえば、`select value a` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="8321f-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-145"> には、任意の行を構築するための行コンストラクターも用意されています。</span><span class="sxs-lookup"><span data-stu-id="8321f-145"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="8321f-146">`select` は、投影の 1 つ以上の要素を受け取り、結果はフィールドを持つデータ レコードになります。次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="8321f-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="8321f-147">左の相関関係と別名定義</span><span class="sxs-lookup"><span data-stu-id="8321f-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="8321f-148">[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] では、1 つのスコープ内の式 (`select` または `from` のような単一句) は同じスコープ内で先に定義された式を参照できません。</span><span class="sxs-lookup"><span data-stu-id="8321f-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="8321f-149">一部の SQL 言語仕様 ([!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] を含む) では、`from` 句でこれらを制限付きでサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8321f-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-150">左の相関関係を一般化、`from`句、およびこれらを取り扱います。</span><span class="sxs-lookup"><span data-stu-id="8321f-150"> generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="8321f-151">`from` 句内の式は、追加の構文を使用せずに、同じ句内で先に作成された定義 (左側の定義) を参照できます。</span><span class="sxs-lookup"><span data-stu-id="8321f-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-152"> では、`group by` 句を伴うクエリにも制限を課しています。</span><span class="sxs-lookup"><span data-stu-id="8321f-152"> also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="8321f-153">内の式、`select`句と`having`のようなクエリ句のみが参考に、`group by`別名を使用してキー。</span><span class="sxs-lookup"><span data-stu-id="8321f-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="8321f-154">次の構成体がで有効では[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]に追加されていないが、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8321f-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="8321f-155">これを [!INCLUDE[esql](../../../../../../includes/esql-md.md)] で実行するには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="8321f-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="8321f-156">テーブル (コレクション) の列 (プロパティ) の参照</span><span class="sxs-lookup"><span data-stu-id="8321f-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="8321f-157">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 内の列の参照は、すべてテーブルの別名を使用して修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8321f-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="8321f-158">次の構成体 (想定される`a`テーブルの有効な列は、 `T`) では有効では、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]ではなく[!INCLUDE[esql](../../../../../../includes/esql-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="8321f-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="8321f-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8321f-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="8321f-160">テーブルの別名は `from` 句では省略できます。</span><span class="sxs-lookup"><span data-stu-id="8321f-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="8321f-161">テーブル名は暗黙的な別名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="8321f-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-162"> では次の形式も使用できます。</span><span class="sxs-lookup"><span data-stu-id="8321f-162"> allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="8321f-163">オブジェクト間の移動</span><span class="sxs-lookup"><span data-stu-id="8321f-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="8321f-164"> ではテーブルの列または行の参照に "." 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="8321f-164"> uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-165"> ではこの表記法を拡張し (プログラミング言語から借用)、オブジェクトのプロパティ間の移動をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8321f-165"> extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="8321f-166">たとえば、`p` が Person 型の式である場合、この人の住所の市区町村を参照するには次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 構文が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8321f-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="8321f-167">\* のサポートなし</span><span class="sxs-lookup"><span data-stu-id="8321f-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="8321f-168">修飾されていないをサポートしています \* 全体の行では、および限定のエイリアスとして構文\\*構文 (t.\\*)、そのテーブルのフィールドのショートカットとして。</span><span class="sxs-lookup"><span data-stu-id="8321f-168"> supports the unqualified \* syntax as an alias for the entire row, and the qualified \\* syntax (t.\\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="8321f-169">さらに、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]では、特殊な count (\\*) 集計で、null 値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8321f-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-170"> では、\* 構造をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-170"> does not support the \* construct.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="8321f-171"> および `select * from T` の形式の `select T1.* from T1, T2...` クエリは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] ではそれぞれ `select value t from T as t` および `select value t1 from T1 as t1, T2 as t2...` として表すことができます。</span><span class="sxs-lookup"><span data-stu-id="8321f-171"> queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="8321f-172">また、これらの構造は継承 (値の置換可能性) に対応していますが、`select *` Variant 型では宣言された型の最上位レベルのプロパティに限定されています。</span><span class="sxs-lookup"><span data-stu-id="8321f-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-173"> は `count(*)` 集計をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-173"> does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="8321f-174">代わりに、`count(0)` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="8321f-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="8321f-175">Group By への変更</span><span class="sxs-lookup"><span data-stu-id="8321f-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-176"> では `group by` キーの別名定義をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8321f-176"> supports aliasing of `group by` keys.</span></span> <span data-ttu-id="8321f-177">内の式、`select`句と`having`句を参照する必要があります、`group by`これらの別名を使用してキー。</span><span class="sxs-lookup"><span data-stu-id="8321f-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="8321f-178">たとえば、次のような [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 構文があるとします。</span><span class="sxs-lookup"><span data-stu-id="8321f-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="8321f-179">これは、次の [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] と同じです。</span><span class="sxs-lookup"><span data-stu-id="8321f-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="8321f-180">コレクションベースの集計</span><span class="sxs-lookup"><span data-stu-id="8321f-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-181"> は、2 種類の集計をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8321f-181"> supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="8321f-182">コレクションベースの集計は、コレクションに対して演算を行い、集計結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="8321f-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="8321f-183">これらはクエリ内の任意の場所で使用でき、`group by` 句を必要としません。</span><span class="sxs-lookup"><span data-stu-id="8321f-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="8321f-184">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8321f-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-185"> は、SQL スタイルの集計もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8321f-185"> also supports SQL-style aggregates.</span></span> <span data-ttu-id="8321f-186">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8321f-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="8321f-187">ORDER BY 句の使用法</span><span class="sxs-lookup"><span data-stu-id="8321f-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="8321f-188"> では、ORDER BY 句は最上位の SELECT .. </span><span class="sxs-lookup"><span data-stu-id="8321f-188"> allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="8321f-189">FROM .. </span><span class="sxs-lookup"><span data-stu-id="8321f-189">FROM ..</span></span> <span data-ttu-id="8321f-190">WHERE ブロックでのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="8321f-190">WHERE block.</span></span> <span data-ttu-id="8321f-191">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、入れ子になった ORDER BY 式を使用でき、それをクエリ内の任意の場所に配置できますが、入れ子になったクエリ内の順序は保持されません。</span><span class="sxs-lookup"><span data-stu-id="8321f-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="8321f-192">識別子</span><span class="sxs-lookup"><span data-stu-id="8321f-192">Identifiers</span></span>  
 <span data-ttu-id="8321f-193">[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] では、識別子の比較は現在のデータベースの照合順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="8321f-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="8321f-194">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の識別子では、常に大文字と小文字は区別されず、アクセントは区別されます (つまり、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] ではアクセントのある文字とアクセントのない文字が区別されます。たとえば、'a' と 'ấ' は等しくありません)。</span><span class="sxs-lookup"><span data-stu-id="8321f-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-195"> は、同じように表示されても別のコード ページに由来する文字の複数のバージョンを別々の文字として扱います。</span><span class="sxs-lookup"><span data-stu-id="8321f-195"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="8321f-196">詳細については、次を参照してください。[入力文字セット](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="8321f-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="8321f-197">Entity SQL では使用できない Transact-SQL 機能</span><span class="sxs-lookup"><span data-stu-id="8321f-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="8321f-198">次の [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 機能は [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8321f-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="8321f-199">DML</span><span class="sxs-lookup"><span data-stu-id="8321f-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-200">現在はサポートされません DML ステートメント (挿入、更新、削除) します。</span><span class="sxs-lookup"><span data-stu-id="8321f-200"> currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="8321f-201">DDL</span><span class="sxs-lookup"><span data-stu-id="8321f-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-202"> の現在のバージョンでは DDL はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-202"> provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="8321f-203">命令型プログラミング</span><span class="sxs-lookup"><span data-stu-id="8321f-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-204"> は [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] とは異なり、命令型プログラミングをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-204"> provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8321f-205">代わりにプログラミング言語を使用します。</span><span class="sxs-lookup"><span data-stu-id="8321f-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="8321f-206">グループ化関数</span><span class="sxs-lookup"><span data-stu-id="8321f-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-207"> ではグループ化関数 (CUBE, ROLLUP、GROUPING_SET など) はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-207"> does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="8321f-208">分析関数</span><span class="sxs-lookup"><span data-stu-id="8321f-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-209"> では分析関数はまだサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-209"> does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="8321f-210">組み込み関数、演算子</span><span class="sxs-lookup"><span data-stu-id="8321f-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-211">サブセットをサポート[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]関数および演算子の組み込みです。</span><span class="sxs-lookup"><span data-stu-id="8321f-211"> supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="8321f-212">これらの演算子と関数の多くは、主要なストア プロバイダーによりサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8321f-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-213">プロバイダー マニフェストで宣言されたストア固有の関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="8321f-213"> uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="8321f-214">さらに、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]組み込みを宣言することができ、既存のユーザー定義ストア関数[!INCLUDE[esql](../../../../../../includes/esql-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="8321f-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="8321f-215">ヒント</span><span class="sxs-lookup"><span data-stu-id="8321f-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-216"> ではクエリ ヒントのメカニズムは提供していません。</span><span class="sxs-lookup"><span data-stu-id="8321f-216"> does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="8321f-217">クエリ結果のバッチ処理</span><span class="sxs-lookup"><span data-stu-id="8321f-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-218"> では、クエリ結果のバッチ処理はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-218"> does not support batching query results.</span></span> <span data-ttu-id="8321f-219">たとえば、次は有効な[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)](バッチとして送信する)。</span><span class="sxs-lookup"><span data-stu-id="8321f-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="8321f-220">ただし、同等の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8321f-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8321f-221"> は、コマンドごとに 1 つの結果生成クエリ ステートメントのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8321f-221"> only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8321f-222">参照</span><span class="sxs-lookup"><span data-stu-id="8321f-222">See Also</span></span>  
 [<span data-ttu-id="8321f-223">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="8321f-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="8321f-224">サポートされていない式</span><span class="sxs-lookup"><span data-stu-id="8321f-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
