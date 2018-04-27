---
title: 'コマンド ツリーからの SQL の生成: ベスト プラクティス'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 037d1eaa8d781d012cde7a1bd3b08aa7003edd77
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="4d8a6-102">コマンド ツリーからの SQL の生成: ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="4d8a6-102">Generating SQL from Command Trees - Best Practices</span></span>
<span data-ttu-id="4d8a6-103">出力クエリ コマンド ツリーは、SQL で表現できるクエリに厳密に従って作成されます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="4d8a6-104">ただし、出力コマンド ツリーから SQL を生成する際にプロバイダーの作成者が直面する、一般的な問題がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="4d8a6-105">このトピックでは、これらの問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-105">This topic discusses these challenges.</span></span> <span data-ttu-id="4d8a6-106">これらの問題への対処方法については、次のトピックでサンプル プロバイダーを介して紹介します。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-106">In the next topic, the sample provider shows how to address these challenges.</span></span>  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="4d8a6-107">SQL SELECT ステートメントでの DbExpression ノードのグループ化</span><span class="sxs-lookup"><span data-stu-id="4d8a6-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="4d8a6-108">一般的な SQL ステートメントは、次の形状の入れ子の構造を持ちます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-108">A typical SQL statement has a nested structure of the following shape:</span></span>  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 <span data-ttu-id="4d8a6-109">1 つ以上の句が空でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="4d8a6-110">入れ子の SELECT ステートメントは、どの行にも出現する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-110">A nested SELECT statement could occur in any of the lines.</span></span>  
  
 <span data-ttu-id="4d8a6-111">クエリ コマンド ツリーを SQL SELECT ステートメントに変換すると、すべての関係演算子に対応する 1 つのサブクエリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="4d8a6-112">ただしその結果、入れ子になった不要なサブクエリが生成され、読み取りが困難になります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="4d8a6-113">一部のデータ ストアでは、クエリは十分なパフォーマンスを発揮しません。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-113">On some data stores, the query may perform poorly.</span></span>  
  
 <span data-ttu-id="4d8a6-114">例として、次のクエリ コマンド ツリーについて考えます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-114">As an example, consider the following query command tree</span></span>  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 <span data-ttu-id="4d8a6-115">非効率な変換を行った場合、次のような SQL が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-115">An inefficient translation would produce:</span></span>  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 <span data-ttu-id="4d8a6-116">すべての関係式ノードが新しい SQL SELECT ステートメントになっていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>  
  
 <span data-ttu-id="4d8a6-117">そのため、正確性を維持しながら、可能な限り多くの式ノードを 1 つの SQL SELECT ステートメントに集約することが重要になります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>  
  
 <span data-ttu-id="4d8a6-118">このような集約を上の例に適用した場合、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-118">The result of such aggregation for the example presented above would be:</span></span>  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="4d8a6-119">SQL SELECT ステートメントでの結合のフラット化</span><span class="sxs-lookup"><span data-stu-id="4d8a6-119">Flatten Joins in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="4d8a6-120">複数のノードを 1 つの SQL SELECT ステートメントに集約する処理の 1 つに、1 つの SQL SELECT ステートメントへの複数の結合式の集約があります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="4d8a6-121">DbJoinExpression は、2 つの入力の間の 1 つの結合を表します。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="4d8a6-122">ただし、1 つの SQL SELECT ステートメントの一部として、複数の結合を指定できます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="4d8a6-123">その場合、結合は指定の順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-123">In that case the joins are performed in the order specified.</span></span>  
  
 <span data-ttu-id="4d8a6-124">左辺スパイン結合 (別の結合の左辺の子として表示される結合) は、1 つの SQL SELECT ステートメントに簡単にフラット化できます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="4d8a6-125">たとえば、次のクエリ コマンド ツリーについて考えます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-125">For example, consider the following query command tree:</span></span>  
  
```  
InnerJoin(  
   a = LeftOuterJoin(  
   b = Extent("TableA")  
   c = Extent("TableB")  
   ON b.y = c.x ),  
   d = Extent("TableC")   
   ON a.b.y = d.z  
)  
```  
  
 <span data-ttu-id="4d8a6-126">これは、次のように適切に変換できます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-126">This can be correctly translated into:</span></span>  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 <span data-ttu-id="4d8a6-127">ただし、左辺スパイン結合以外の結合のフラット化は容易ではないので、実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="4d8a6-128">たとえば、次のクエリ コマンド ツリーの結合について考えます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-128">For example, the joins in the following query command tree:</span></span>  
  
```  
InnerJoin(  
   a = Extent("TableA")   
   b = LeftOuterJoin(  
   c = Extent("TableB")  
   d = Extent("TableC")  
   ON c.y = d.x),  
   ON a.z = b.c.y  
)  
```  
  
 <span data-ttu-id="4d8a6-129">これは、サブクエリを持つ SQL SELECT ステートメントに変換されます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a><span data-ttu-id="4d8a6-130">入力の別名のリダイレクト</span><span class="sxs-lookup"><span data-stu-id="4d8a6-130">Input Alias Redirecting</span></span>  
 <span data-ttu-id="4d8a6-131">入力の別名のリダイレクトについて理解するために、DbFilterExpression、DbProjectExpression、DbCrossJoinExpression、DbJoinExpression、DbSortExpression、DbGroupByExpression、DbApplyExpression、DbSkipExpression などの関係式の構造について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>  
  
 <span data-ttu-id="4d8a6-132">これらの型はそれぞれ、入力コレクションを示す 1 つ以上の入力プロパティを持ちます。各入力に対応するバインディング変数は、コレクションのトラバース時にその入力の各要素を表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="4d8a6-133">バインディング変数は、DbFilterExpression の Predicate プロパティや DbProjectExpression の Projection プロパティなどにおいて、入力要素を参照するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>  
  
 <span data-ttu-id="4d8a6-134">多数の関係式ノードを 1 つの SQL SELECT ステートメントに集約し、関係式の一部 (たとえば、DbProjectExpression の Projection プロパティの一部) である式を評価する場合、複数の式のバインディングを 1 つのエクステントにリダイレクトする必要があるため、使用されるバインディング変数が入力の別名と異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="4d8a6-135">この問題は、別名の名前変更と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-135">This problem is called alias renaming.</span></span>  
  
 <span data-ttu-id="4d8a6-136">このトピックの最初の例について考えてみてください。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-136">Consider the first example in this topic.</span></span> <span data-ttu-id="4d8a6-137">単純な変換を実行して Projection a.x (DbPropertyExpression(a, x)) を変換する場合、バインディング変数に合わせて入力に "a" という別名を設定しているため、`a.x` に変換するのが適切な処理です。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="4d8a6-138">ただし、両方のノードを 1 つの SQL SELECT ステートメントに集約する場合は、入力に "b" という別名が設定されているため、同じ DbPropertyExpression を `b.x` に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>  
  
## <a name="join-alias-flattening"></a><span data-ttu-id="4d8a6-139">結合の別名のフラット化</span><span class="sxs-lookup"><span data-stu-id="4d8a6-139">Join Alias Flattening</span></span>  
 <span data-ttu-id="4d8a6-140">出力コマンド ツリーの他の関係式とは異なり、DbJoinExpression は 2 つの列から成る行として結果の型を出力します。この 2 つの列のそれぞれが、いずれか 1 つの入力に対応しています。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="4d8a6-141">結合から生じたスカラー プロパティにアクセスするために作成された DbPropertyExpresssion は、別の DbPropertyExpresssion に基づいています。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-141">When a DbPropertyExpresssion is built to access a scalar property originating from a join, it is over another DbPropertyExpresssion.</span></span>  
  
 <span data-ttu-id="4d8a6-142">例として、例 2 の "a.b.y" と例 3 の "b.c.y" が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="4d8a6-143">ただし、対応する SQL ステートメントでは、これらは "b.y" になります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="4d8a6-144">この別名の再設定は、結合の別名のフラット化と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-144">This re-aliasing is called join alias flattening.</span></span>  
  
## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="4d8a6-145">列名およびエクステントの別名の名前変更</span><span class="sxs-lookup"><span data-stu-id="4d8a6-145">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="4d8a6-146">結合を持つ SQL SELECT クエリを射影を使用して完成させる必要がある場合、関与するすべての列を入力から列挙する際に、名前の競合が発生することがあります。これは、複数の入力が同じ列名を持っている場合です。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="4d8a6-147">競合を避けるには、列に異なる名前を使用してください。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-147">Use a different name for the column to avoid the collision.</span></span>  
  
 <span data-ttu-id="4d8a6-148">また、結合のフラット化の際にも、関与するテーブル (またはサブクエリ) の別名が競合することがあります。この場合にも名前の変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>  
  
## <a name="avoid-select-"></a><span data-ttu-id="4d8a6-149">SELECT \* の回避</span><span class="sxs-lookup"><span data-stu-id="4d8a6-149">Avoid SELECT \*</span></span>  
 <span data-ttu-id="4d8a6-150">ベース テーブルから選択する際には `SELECT *` を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="4d8a6-151">ストレージ モデルで、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーションは、データベース テーブルに含まれる列のサブセットのみを含めることがあります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="4d8a6-152">この場合、`SELECT *` によって正しくない結果が生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="4d8a6-153">代わりに、関与する式の結果の型の列名を使用して、関与するすべての列を指定してください。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>  
  
## <a name="reuse-of-expressions"></a><span data-ttu-id="4d8a6-154">式の再利用</span><span class="sxs-lookup"><span data-stu-id="4d8a6-154">Reuse of Expressions</span></span>  
 <span data-ttu-id="4d8a6-155">式は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] によって渡されたクエリ コマンド ツリーで再利用できます。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="4d8a6-156">各式は、クエリ コマンド ツリーで 1 回しか使用できないわけではありません。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-156">Do not assume that each expression appears only once in the query command tree.</span></span>  
  
## <a name="mapping-primitive-types"></a><span data-ttu-id="4d8a6-157">プリミティブ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="4d8a6-157">Mapping Primitive Types</span></span>  
 <span data-ttu-id="4d8a6-158">概念 (EDM) 型をプロバイダー型にマップする場合は、さまざまな値に対応できるように、最も幅の広い型 (Int32) にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="4d8a6-159">また、多くの操作で、BLOB の種類と同様に使用できない型へのマッピングをしないでください (たとえば、 `ntext` SQL Server で)。</span><span class="sxs-lookup"><span data-stu-id="4d8a6-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8a6-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d8a6-160">See Also</span></span>  
 [<span data-ttu-id="4d8a6-161">SQL 生成</span><span class="sxs-lookup"><span data-stu-id="4d8a6-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
