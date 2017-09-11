---
title: "リフレクション (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: acfcb519128de0d616757398c94ec70dc7de6ef1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="reflection-visual-basic"></a><span data-ttu-id="42b48-102">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42b48-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="42b48-103">リフレクション オブジェクトの提供 (型の<xref:System.Type>) アセンブリ、モジュールや型を記述する</xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="42b48-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="42b48-104">リフレクションを使用して、動的に型のインスタンスを作成、既存のオブジェクトにバインドまたは既存のオブジェクトから型を取得し、メソッドの呼び出しまたは、フィールドやプロパティにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="42b48-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="42b48-105">コード内の属性を使用している場合は、リフレクションを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="42b48-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="42b48-106">詳細については、次を参照してください。[属性](https://msdn.microsoft.com/library/5x6cd29c)します。</span><span class="sxs-lookup"><span data-stu-id="42b48-106">For more information, see [Attributes](https://msdn.microsoft.com/library/5x6cd29c).</span></span>  
  
 <span data-ttu-id="42b48-107">静的メソッドを使用してリフレクションの単純な例を次に示します`GetType`- からすべての型によって継承された、`Object`基本クラスの変数の型を取得します。</span><span class="sxs-lookup"><span data-stu-id="42b48-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="42b48-108">出力です。</span><span class="sxs-lookup"><span data-stu-id="42b48-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="42b48-109">次の例では、リフレクションを使用して、読み込まれたアセンブリの完全名を取得します。</span><span class="sxs-lookup"><span data-stu-id="42b48-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="42b48-110">出力です。</span><span class="sxs-lookup"><span data-stu-id="42b48-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="42b48-111">リフレクションの概要</span><span class="sxs-lookup"><span data-stu-id="42b48-111">Reflection Overview</span></span>  
 <span data-ttu-id="42b48-112">リフレクションは、次のような場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="42b48-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="42b48-113">プログラムのメタデータ内の属性にアクセスする必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="42b48-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="42b48-114">詳細については、次を参照してください。[を取得する情報を属性に格納](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)します。</span><span class="sxs-lookup"><span data-stu-id="42b48-114">For more information, see [Retrieving Information Stored in Attributes](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).</span></span>  
  
-   <span data-ttu-id="42b48-115">調べることと、アセンブリ内の型をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="42b48-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="42b48-116">実行時に新しい型を構築します。</span><span class="sxs-lookup"><span data-stu-id="42b48-116">For building new types at runtime.</span></span> <span data-ttu-id="42b48-117"><xref:System.Reflection.Emit>。</xref:System.Reflection.Emit>クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="42b48-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="42b48-118">実行時に作成された型のメソッドへのアクセスの遅延バインディングを実行します。</span><span class="sxs-lookup"><span data-stu-id="42b48-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="42b48-119">トピックを参照して[動的な読み込みおよび使用して型](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc)します。</span><span class="sxs-lookup"><span data-stu-id="42b48-119">See the topic [Dynamically Loading and Using Types](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42b48-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="42b48-120">Related Sections</span></span>  
 <span data-ttu-id="42b48-121">詳細情報</span><span class="sxs-lookup"><span data-stu-id="42b48-121">For more information:</span></span>  
  
-   [<span data-ttu-id="42b48-122">リフレクション</span><span class="sxs-lookup"><span data-stu-id="42b48-122">Reflection</span></span>](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [<span data-ttu-id="42b48-123">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="42b48-123">Viewing Type Information</span></span>](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [<span data-ttu-id="42b48-124">リフレクションとジェネリック型</span><span class="sxs-lookup"><span data-stu-id="42b48-124">Reflection and Generic Types</span></span>](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <span data-ttu-id="42b48-125"><xref:System.Reflection.Emit></xref:System.Reflection.Emit></span><span class="sxs-lookup"><span data-stu-id="42b48-125"><xref:System.Reflection.Emit></span></span>  
  
-   [<span data-ttu-id="42b48-126">属性に格納されている情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="42b48-126">Retrieving Information Stored in Attributes</span></span>](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a><span data-ttu-id="42b48-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="42b48-127">See Also</span></span>  
 <span data-ttu-id="42b48-128">[Visual Basic のプログラミング ガイド](../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="42b48-128">[Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="42b48-129"> [共通言語ランタイムのアセンブリ](https://msdn.microsoft.com/library/k3677y81)</span><span class="sxs-lookup"><span data-stu-id="42b48-129"> [Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)</span></span>
