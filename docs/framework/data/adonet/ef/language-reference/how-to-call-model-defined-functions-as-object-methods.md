---
title: "方法: モデル定義関数をオブジェクト メソッドとして呼び出す"
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
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a934cd8c122a1564c034f8578e8bad680ba919a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a><span data-ttu-id="05629-102">方法: モデル定義関数をオブジェクト メソッドとして呼び出す</span><span class="sxs-lookup"><span data-stu-id="05629-102">How to: Call Model-Defined Functions as Object Methods</span></span>
<span data-ttu-id="05629-103">ここでは、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドまたはカスタム クラスの静的メソッドとして呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="05629-103">This topic describes how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object or as a static method on a custom class.</span></span> <span data-ttu-id="05629-104">A*モデル定義関数*概念モデルで定義されている関数です。</span><span class="sxs-lookup"><span data-stu-id="05629-104">A *model-defined function* is a function that is defined in the conceptual model.</span></span> <span data-ttu-id="05629-105">このトピックで説明する手順は、これらの関数を LINQ to Entities クエリから呼び出すのではなく、直接呼び出す方法を示すものです。</span><span class="sxs-lookup"><span data-stu-id="05629-105">The procedures in the topic describe how to call these functions directly instead of calling them from LINQ to Entities queries.</span></span> <span data-ttu-id="05629-106">Linq to Entities クエリ モデル定義関数を呼び出す方法の詳細については、次を参照してください。[する方法: クエリの Call Model-Defined 関数](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)です。</span><span class="sxs-lookup"><span data-stu-id="05629-106">For information about calling model-defined functions in LINQ to Entities queries, see [How to: Call Model-Defined Functions in Queries](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).</span></span>  
  
 <span data-ttu-id="05629-107">モデル定義関数を <xref:System.Data.Objects.ObjectContext> メソッドとして呼び出す場合も、カスタム クラスの静的メソッドとして呼び出す場合も、ます <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> でメソッドをモデル定義関数にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="05629-107">Whether you call a model-defined function as an <xref:System.Data.Objects.ObjectContext> method or as a static method on a custom class, you must first map the method to the model-defined function with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="05629-108">ただし、<xref:System.Data.Objects.ObjectContext> クラスのメソッドを定義するときには、<xref:System.Data.Objects.ObjectContext.QueryProvider%2A> プロパティを使用して LINQ プロバイダーを公開する必要があります。それに対して、カスタム クラスの静的メソッドを定義するときには、<xref:System.Linq.IQueryable.Provider%2A> プロパティを使用して LINQ プロバイダーを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05629-108">However, when you define a method on the <xref:System.Data.Objects.ObjectContext> class, you must use the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property to expose the LINQ provider, whereas when you define a static method on a custom class, you must use the <xref:System.Linq.IQueryable.Provider%2A> property to expose the LINQ provider.</span></span> <span data-ttu-id="05629-109">詳細については、下の手順の後に示した例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05629-109">For more information, see the examples that follow the procedures below.</span></span>  
  
 <span data-ttu-id="05629-110">下の手順は、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドおよびカスタム クラスの静的メソッドとして呼び出す方法の概要を示したものです。</span><span class="sxs-lookup"><span data-stu-id="05629-110">The procedures below provide high-level outlines for calling a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object and as a static method on a custom class.</span></span> <span data-ttu-id="05629-111">詳細な手順は、その後の例で示します。</span><span class="sxs-lookup"><span data-stu-id="05629-111">The examples that follow provide more detail about the steps in the procedures.</span></span> <span data-ttu-id="05629-112">この手順では、関数を概念モデルで定義済みであると想定します。</span><span class="sxs-lookup"><span data-stu-id="05629-112">The procedures assume that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="05629-113">詳細については、次を参照してください。[する方法: カスタム関数を概念モデルで定義](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)です。</span><span class="sxs-lookup"><span data-stu-id="05629-113">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a><span data-ttu-id="05629-114">モデル定義関数を ObjectContext オブジェクトのメソッドとして呼び出すには</span><span class="sxs-lookup"><span data-stu-id="05629-114">To call a model-defined function as a method on an ObjectContext object</span></span>  
  
1.  <span data-ttu-id="05629-115">ソース ファイルを追加して、部分クラスを拡張します。このクラスは、<xref:System.Data.Objects.ObjectContext> クラスから派生したものであり、Entity Framework ツールによって自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="05629-115">Add a source file to extend the partial class derived from the <xref:System.Data.Objects.ObjectContext> class, auto-generated by the Entity Framework tools.</span></span> <span data-ttu-id="05629-116">CLR スタブを別のソース ファイルで定義すると、ファイルを再生成しても変更内容が失われません。</span><span class="sxs-lookup"><span data-stu-id="05629-116">Defining the CLR stub in a separate source file will prevent the changes from being lost when the file is regenerated.</span></span>  
  
2.  <span data-ttu-id="05629-117">共通言語ランタイム (CLR) メソッドを、次のことを行う <xref:System.Data.Objects.ObjectContext> クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="05629-117">Add a common language runtime (CLR) method to your <xref:System.Data.Objects.ObjectContext> class that does the following:</span></span>  
  
    -   <span data-ttu-id="05629-118">概念モデルで定義された関数にマップします。</span><span class="sxs-lookup"><span data-stu-id="05629-118">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="05629-119">メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05629-119">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="05629-120">属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間と概念モデルの関数名であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="05629-120">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span> <span data-ttu-id="05629-121">LINQ の関数名解決では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="05629-121">Function name resolution for LINQ is case sensitive.</span></span>  
  
    -   <span data-ttu-id="05629-122"><xref:System.Linq.IQueryProvider.Execute%2A> プロパティによって返される <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> メソッドの結果を返します。</span><span class="sxs-lookup"><span data-stu-id="05629-122">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property.</span></span>  
  
3.  <span data-ttu-id="05629-123">メソッドを <xref:System.Data.Objects.ObjectContext> クラスのインスタンスのメンバーとして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="05629-123">Call the method as a member on an instance of the <xref:System.Data.Objects.ObjectContext> class.</span></span>  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a><span data-ttu-id="05629-124">モデル定義関数をカスタム クラスの静的メソッドとして呼び出すには</span><span class="sxs-lookup"><span data-stu-id="05629-124">To call a model-defined function as static method on a custom class</span></span>  
  
1.  <span data-ttu-id="05629-125">クラスを次のことを行う静的メソッドでアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="05629-125">Add a class to your application with a static method that does the following:</span></span>  
  
    -   <span data-ttu-id="05629-126">概念モデルで定義された関数にマップします。</span><span class="sxs-lookup"><span data-stu-id="05629-126">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="05629-127">メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05629-127">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="05629-128">属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間と概念モデルの関数名であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="05629-128">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span>  
  
    -   <span data-ttu-id="05629-129"><xref:System.Linq.IQueryable> 引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="05629-129">Accepts an <xref:System.Linq.IQueryable> argument.</span></span>  
  
    -   <span data-ttu-id="05629-130"><xref:System.Linq.IQueryProvider.Execute%2A> プロパティによって返される <xref:System.Linq.IQueryable.Provider%2A> メソッドの結果を返します。</span><span class="sxs-lookup"><span data-stu-id="05629-130">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Linq.IQueryable.Provider%2A> property.</span></span>  
  
2.  <span data-ttu-id="05629-131">メソッドをカスタム クラスの静的メソッドのメンバーとして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="05629-131">Call the method as a member a static method on the custom class</span></span>  
  
## <a name="example"></a><span data-ttu-id="05629-132">例</span><span class="sxs-lookup"><span data-stu-id="05629-132">Example</span></span>  
 <span data-ttu-id="05629-133">**モデル定義関数を ObjectContext オブジェクトのメソッドとして呼び出す**</span><span class="sxs-lookup"><span data-stu-id="05629-133">**Calling a Model-Defined Function as a Method on an ObjectContext Object**</span></span>  
  
 <span data-ttu-id="05629-134">次の例で、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドとして呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="05629-134">The following example demonstrates how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object.</span></span> <span data-ttu-id="05629-135">この例では、 [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)です。</span><span class="sxs-lookup"><span data-stu-id="05629-135">The example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span>  
  
 <span data-ttu-id="05629-136">指定製品の製品収益を返す下の概念モデル関数について考察してください </span><span class="sxs-lookup"><span data-stu-id="05629-136">Consider the conceptual model function below that returns product revenue for a specified product.</span></span> <span data-ttu-id="05629-137">(関数を概念モデルに追加する方法の詳細については、次を参照してください[する方法: カスタム関数を概念モデルで定義](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)。)。</span><span class="sxs-lookup"><span data-stu-id="05629-137">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a><span data-ttu-id="05629-138">例</span><span class="sxs-lookup"><span data-stu-id="05629-138">Example</span></span>  
 <span data-ttu-id="05629-139">次のコードでは、メソッドを上の概念モデル関数にマップする `AdventureWorksEntities` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="05629-139">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="05629-140">例</span><span class="sxs-lookup"><span data-stu-id="05629-140">Example</span></span>  
 <span data-ttu-id="05629-141">次のコードでは、上のメソッドを呼び出して、指定製品の製品収益を表示します。</span><span class="sxs-lookup"><span data-stu-id="05629-141">The following code calls the method above to display the product revenue for a specified product:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="05629-142">例</span><span class="sxs-lookup"><span data-stu-id="05629-142">Example</span></span>  
 <span data-ttu-id="05629-143">次の例で、コレクション (<xref:System.Linq.IQueryable%601> オブジェクトとして) を返すモデル定義関数を呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="05629-143">The following example demonstrates how to call a model-defined function that returns a collection (as an <xref:System.Linq.IQueryable%601> object).</span></span> <span data-ttu-id="05629-144">指定された製品 ID に関して `SalesOrderDetails` をすべて返す下の概念モデル関数について考察してください。</span><span class="sxs-lookup"><span data-stu-id="05629-144">Consider the conceptual model function below that returns all the `SalesOrderDetails` for a given product ID.</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a><span data-ttu-id="05629-145">例</span><span class="sxs-lookup"><span data-stu-id="05629-145">Example</span></span>  
 <span data-ttu-id="05629-146">次のコードでは、メソッドを上の概念モデル関数にマップする `AdventureWorksEntities` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="05629-146">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="05629-147">例</span><span class="sxs-lookup"><span data-stu-id="05629-147">Example</span></span>  
 <span data-ttu-id="05629-148">次のコードは、メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="05629-148">The following code calls the method.</span></span> <span data-ttu-id="05629-149">返された <xref:System.Linq.IQueryable%601> クエリがさらに絞り込まれて、各 `SalesOrderDetail` のライン合計を返すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="05629-149">Note that the returned <xref:System.Linq.IQueryable%601> query is further refined to return line totals for each `SalesOrderDetail`.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="05629-150">例</span><span class="sxs-lookup"><span data-stu-id="05629-150">Example</span></span>  
 <span data-ttu-id="05629-151">**モデル定義関数をカスタム クラスの静的メソッドとして呼び出す**</span><span class="sxs-lookup"><span data-stu-id="05629-151">**Calling a Model-Defined Function as a Static Method on a Custom Class**</span></span>  
  
 <span data-ttu-id="05629-152">次の例で、モデル定義関数をカスタム クラスの静的メソッドとして呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="05629-152">The next example demonstrates how to call a model-defined function as a static method on a custom class.</span></span> <span data-ttu-id="05629-153">この例では、 [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)です。</span><span class="sxs-lookup"><span data-stu-id="05629-153">The example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05629-154">ユーザーが、モデル定義関数をカスタム クラスの静的メソッドとして呼び出すときには、モデル定義関数はコレクションを受け取って、コレクションの値の集計結果を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="05629-154">When you call a model-defined function as a static method on a custom class, the model-defined function must accept a collection and return an aggregation of values in the collection.</span></span>  
  
 <span data-ttu-id="05629-155">SalesOrderDetail コレクションの製品収益を返す下の概念モデル関数について考察してください </span><span class="sxs-lookup"><span data-stu-id="05629-155">Consider the conceptual model function below that returns product revenue for a SalesOrderDetail collection.</span></span> <span data-ttu-id="05629-156">(関数を概念モデルに追加する方法の詳細については、次を参照してください。[する方法: カスタム関数を概念モデルで定義](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)。)。</span><span class="sxs-lookup"><span data-stu-id="05629-156">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).).</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="05629-157">例</span><span class="sxs-lookup"><span data-stu-id="05629-157">Example</span></span>  
 <span data-ttu-id="05629-158">次のコードでは、上の概念モデル関数にマップする静的メソッドを持つアプリケーションにクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="05629-158">The following code adds a class to your application that contains a static method that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="05629-159">例</span><span class="sxs-lookup"><span data-stu-id="05629-159">Example</span></span>  
 <span data-ttu-id="05629-160">次のコードでは、上のメソッドを呼び出して、SalesOrderDetail コレクションの製品収益を表示します。</span><span class="sxs-lookup"><span data-stu-id="05629-160">The following code calls the method above to display the product revenue for a SalesOrderDetail collection:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="05629-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="05629-161">See Also</span></span>  
 [<span data-ttu-id="05629-162">.edmx ファイルの概要</span><span class="sxs-lookup"><span data-stu-id="05629-162">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="05629-163">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="05629-163">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="05629-164">LINQ to Entities クエリで関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="05629-164">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
