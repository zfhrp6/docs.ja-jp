---
title: "方法 : LINQ の結合を使用してデータを結合する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 432be646ce4353fd4627a34f363e7562f6181e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="f2702-102">方法 : LINQ の結合を使用してデータを結合する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2702-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="f2702-103">Visual Basic では、`Join`と`Group Join`コレクション間で共通の値に基づく複数のコレクションの内容を結合するために句をクエリします。</span><span class="sxs-lookup"><span data-stu-id="f2702-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="f2702-104">これらの値と呼ばれる*キー*値。</span><span class="sxs-lookup"><span data-stu-id="f2702-104">These values are known as *key* values.</span></span> <span data-ttu-id="f2702-105">リレーショナル データベースの概念に慣れている開発者が認識されます、`Join`としては INNER JOIN 句と`Group Join`として、実際には、左外部結合句。</span><span class="sxs-lookup"><span data-stu-id="f2702-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="f2702-106">このトピックの例を使用してデータを結合する方法はいくつかを示す、`Join`と`Group Join`クエリ句。</span><span class="sxs-lookup"><span data-stu-id="f2702-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="f2702-107">プロジェクトを作成し、サンプル データを追加</span><span class="sxs-lookup"><span data-stu-id="f2702-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="f2702-108">サンプル データと種類を含むプロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="f2702-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="f2702-109">このトピックのサンプルを実行するには、Visual Studio を開き、新しい Visual Basic コンソール アプリケーション プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="f2702-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="f2702-110">Visual Basic で作成された Module1.vb ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2702-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="f2702-111">このトピックの使用中で、サンプル、`Person`と`Pet`型と、次のコード例からのデータ。</span><span class="sxs-lookup"><span data-stu-id="f2702-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="f2702-112">既定値にこのコードをコピー `Module1` Visual Basic で作成されたモジュール。</span><span class="sxs-lookup"><span data-stu-id="f2702-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="f2702-113">Join 句を使用して、内部結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="f2702-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="f2702-114">内部結合は、2 つのコレクションからのデータ。</span><span class="sxs-lookup"><span data-stu-id="f2702-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="f2702-115">指定したキー値が一致するアイテムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f2702-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="f2702-116">ない、一致する項目、他のコレクションのいずれかのコレクションから項目が除外されます。</span><span class="sxs-lookup"><span data-stu-id="f2702-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="f2702-117">Visual basic での LINQ は内部結合を実行するための 2 つのオプションを提供します。 暗黙の結合と、明示的な結合します。</span><span class="sxs-lookup"><span data-stu-id="f2702-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="f2702-118">暗黙の結合で結合するコレクションの指定、`From`句に一致するキー フィールドを指定して、`Where`句。</span><span class="sxs-lookup"><span data-stu-id="f2702-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="f2702-119">Visual Basic は、暗黙的に指定されたキー フィールドに基づく 2 つのコレクションを結合します。</span><span class="sxs-lookup"><span data-stu-id="f2702-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="f2702-120">使用して、明示的な結合を指定することができます、`Join`句どのキーが結合に使用するフィールドを明確にするときにします。</span><span class="sxs-lookup"><span data-stu-id="f2702-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="f2702-121">ここで、`Where`もクエリの結果をフィルター処理する句を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2702-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="f2702-122">Join 句を使用して、Inner Join を実行するには</span><span class="sxs-lookup"><span data-stu-id="f2702-122">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="f2702-123">次のコードを追加、`Module1`両方暗黙的および明示的な内部結合の例を参照するプロジェクトのモジュール。</span><span class="sxs-lookup"><span data-stu-id="f2702-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="f2702-124">Group Join 句を使用して、左外部結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="f2702-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="f2702-125">左外部結合には、結合および結合の右側にあるコレクションからの値が一致するのみの左側にあるコレクションからすべての項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2702-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="f2702-126">左側のコレクション内で一致する項目を持たない結合の右側にあるコレクションから項目は、クエリの結果から除外されます。</span><span class="sxs-lookup"><span data-stu-id="f2702-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="f2702-127">`Group Join`句実行すると、実際には、左外部結合します。</span><span class="sxs-lookup"><span data-stu-id="f2702-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="f2702-128">LEFT OUTER JOIN と通常呼ばれるものと新機能の違い、`Group Join`される句を返します、`Group Join`左側にあるコレクション内の各項目の結合の右側にあるコレクションから句のグループの結果。</span><span class="sxs-lookup"><span data-stu-id="f2702-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="f2702-129">リレーショナル データベースでは、LEFT OUTER JOIN は、クエリ内の各項目の結果をグループに属していない結果には、結合に両方のコレクションから一致する項目が含まれています。 を返します。</span><span class="sxs-lookup"><span data-stu-id="f2702-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="f2702-130">この場合、結合の左側のコレクションからアイテムは、右側のコレクションから一致する項目ごとに繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="f2702-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="f2702-131">これがどのように、次の手順を完了したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2702-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="f2702-132">結果を取得することができます、`Group Join`それぞれグループ化されたクエリの結果の項目を返すようにクエリを拡張することによってグループ化されていない結果としてクエリ。</span><span class="sxs-lookup"><span data-stu-id="f2702-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="f2702-133">これを実現するにはに対するクエリを実行することを確認する必要がある、`DefaultIfEmpty`グループ化されたコレクションのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="f2702-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="f2702-134">これにより、結合の左側のコレクションから項目が右側のコレクションから一致する結果があるない場合でも、クエリ結果に含まれるもします。</span><span class="sxs-lookup"><span data-stu-id="f2702-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="f2702-135">コードは、結合の右側のコレクションに一致する値がない場合は、既定の結果値を提供するクエリを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="f2702-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="f2702-136">Group Join 句を使用して左外部結合を実行するには</span><span class="sxs-lookup"><span data-stu-id="f2702-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="f2702-137">次のコードを追加、`Module1`モジュールで、プロジェクトの両方のグループ化された左外部結合とグループに属していない左外部結合の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2702-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="f2702-138">複合キーを使用して、結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="f2702-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="f2702-139">使用することができます、`And`でキーワード、`Join`または`Group Join`句に一致するときに使用する複数のキー フィールドを識別する値の結合するコレクション。</span><span class="sxs-lookup"><span data-stu-id="f2702-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="f2702-140">`And`キーワードは、すべての指定キー フィールドに結合する項目の一致する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="f2702-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="f2702-141">複合キーを使用して結合を実行するには</span><span class="sxs-lookup"><span data-stu-id="f2702-141">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="f2702-142">次のコードを追加、`Module1`複合キーを使用する結合の例を参照するプロジェクトのモジュール。</span><span class="sxs-lookup"><span data-stu-id="f2702-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a><span data-ttu-id="f2702-143">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="f2702-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="f2702-144">例を実行するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="f2702-144">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="f2702-145">置換、`Sub Main`で、`Module1`をこのトピックの例を実行する次のコード プロジェクト内のモジュール。</span><span class="sxs-lookup"><span data-stu-id="f2702-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  <span data-ttu-id="f2702-146">F5 キーを押してサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f2702-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2702-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2702-147">See Also</span></span>  
 [<span data-ttu-id="f2702-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="f2702-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="f2702-149">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="f2702-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="f2702-150">Join 句</span><span class="sxs-lookup"><span data-stu-id="f2702-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="f2702-151">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="f2702-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="f2702-152">From 句</span><span class="sxs-lookup"><span data-stu-id="f2702-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="f2702-153">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="f2702-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="f2702-154">クエリ</span><span class="sxs-lookup"><span data-stu-id="f2702-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="f2702-155">LINQ によるデータ変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="f2702-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
