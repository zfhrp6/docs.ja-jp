---
title: "方法: クエリを使用してモデル定義関数を呼び出す"
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
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 179c00def6b5a810806d536a8728cbbc544b1084
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="eac91-102">方法: クエリを使用してモデル定義関数を呼び出す</span><span class="sxs-lookup"><span data-stu-id="eac91-102">How to: Call Model-Defined Functions in Queries</span></span>
<span data-ttu-id="eac91-103">ここでは、概念モデルで定義されている関数を [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリから呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eac91-103">This topic describes how to call functions that are defined in the conceptual model from within [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="eac91-104">以下に示す手順は、モデル定義関数を [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリから呼び出す方法をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="eac91-104">The procedure below provides a high-level outline for calling a model-defined function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="eac91-105">各手順の詳しい説明は、その後の例で示します。</span><span class="sxs-lookup"><span data-stu-id="eac91-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="eac91-106">この手順では、関数を概念モデルで定義済みであると想定します。</span><span class="sxs-lookup"><span data-stu-id="eac91-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="eac91-107">詳細については、次を参照してください。[する方法: カスタム関数を概念モデルで定義](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)です。</span><span class="sxs-lookup"><span data-stu-id="eac91-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="eac91-108">概念モデルで定義された関数を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="eac91-108">To call a function defined in the conceptual model</span></span>  
  
1.  <span data-ttu-id="eac91-109">概念モデルで定義された関数にマップされているアプリケーションに、共通言語ランタイム (CLR) メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="eac91-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="eac91-110">メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eac91-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="eac91-111">属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間名と関数名であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="eac91-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="eac91-112">LINQ の関数名解決では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="eac91-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2.  <span data-ttu-id="eac91-113">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリを使用して関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eac91-113">Call the function in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eac91-114">例</span><span class="sxs-lookup"><span data-stu-id="eac91-114">Example</span></span>  
 <span data-ttu-id="eac91-115">次の例は、概念モデルで定義されている関数を [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリから呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="eac91-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="eac91-116">この例では、School モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="eac91-116">The example uses the School model.</span></span> <span data-ttu-id="eac91-117">School モデルについては、次を参照してください。 [School サンプル データベースを作成する](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)と[学校 .edmx ファイルを生成する](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758)です。</span><span class="sxs-lookup"><span data-stu-id="eac91-117">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="eac91-118">次の概念モデル関数は、あるインストラクターが雇用されてから経過した年数を返します。</span><span class="sxs-lookup"><span data-stu-id="eac91-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="eac91-119">概念モデルに関数を追加する方法の詳細については、次を参照してください[する方法: カスタム関数を概念モデルで定義](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)。)。</span><span class="sxs-lookup"><span data-stu-id="eac91-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="eac91-120">例</span><span class="sxs-lookup"><span data-stu-id="eac91-120">Example</span></span>  
 <span data-ttu-id="eac91-121">次に、次のメソッドをアプリケーションに追加し、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> を使用して概念モデル関数にマップします。</span><span class="sxs-lookup"><span data-stu-id="eac91-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="eac91-122">例</span><span class="sxs-lookup"><span data-stu-id="eac91-122">Example</span></span>  
 <span data-ttu-id="eac91-123">これで、[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリから概念モデル関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="eac91-123">Now you can call the conceptual model function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="eac91-124">次のコードは、雇用年数が 10 年を超えるすべてのインストラクターを表示するメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eac91-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="eac91-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="eac91-125">See Also</span></span>  
 [<span data-ttu-id="eac91-126">.edmx ファイルの概要</span><span class="sxs-lookup"><span data-stu-id="eac91-126">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="eac91-127">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="eac91-127">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="eac91-128">LINQ to Entities クエリで関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="eac91-128">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="eac91-129">方法: オブジェクトのメソッドとしてのモデル定義関数を呼び出す</span><span class="sxs-lookup"><span data-stu-id="eac91-129">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
