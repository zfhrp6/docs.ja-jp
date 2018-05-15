---
title: リフレクション (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: f47f78ff9989fc44ad46b66a447061c3fa84a86e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="fdec7-102">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdec7-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="fdec7-103">リフレクションは、アセンブリ、モジュール、および型を記述する (<xref:System.Type> 型の) オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="fdec7-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="fdec7-104">リフレクションを使用すると、動的に型のインスタンスを作成したり、作成したインスタンスを既存のオブジェクトにバインドしたり、さらに既存のオブジェクトから型を取得してそのオブジェクトのメソッドを呼び出したり、フィールドやプロパティにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="fdec7-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="fdec7-105">コードで属性を使用している場合は、リフレクションを使用してそれらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fdec7-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="fdec7-106">詳細については、「[属性](../../../standard/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdec7-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="fdec7-107">次の例は、`GetType` メソッドを使用して変数の型を取得する簡単なリフレクションを示しています。このメソッドは、`Object` 基底クラスからすべての型に継承される静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fdec7-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="fdec7-108">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fdec7-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="fdec7-109">次の例では、リフレクションを使用して、読み込まれたアセンブリの完全名を取得します。</span><span class="sxs-lookup"><span data-stu-id="fdec7-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="fdec7-110">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fdec7-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="fdec7-111">リフレクションの概要</span><span class="sxs-lookup"><span data-stu-id="fdec7-111">Reflection Overview</span></span>  
 <span data-ttu-id="fdec7-112">リフレクションは、次の場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fdec7-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="fdec7-113">プログラムのメタデータ内の属性にアクセスする必要がある。</span><span class="sxs-lookup"><span data-stu-id="fdec7-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="fdec7-114">詳細については、「[属性に格納されている情報の取得](../../../standard/attributes/retrieving-information-stored-in-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdec7-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="fdec7-115">アセンブリの型をチェックし、インスタンス化する。</span><span class="sxs-lookup"><span data-stu-id="fdec7-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="fdec7-116">実行時に新しい型を作成する。</span><span class="sxs-lookup"><span data-stu-id="fdec7-116">For building new types at runtime.</span></span> <span data-ttu-id="fdec7-117"><xref:System.Reflection.Emit> でクラスを使います。</span><span class="sxs-lookup"><span data-stu-id="fdec7-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="fdec7-118">遅延バインディングを実行するために、実行時に作成された型でメソッドにアクセスする。</span><span class="sxs-lookup"><span data-stu-id="fdec7-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="fdec7-119">「[型の動的な読み込みおよび使用](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdec7-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fdec7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdec7-120">Related Sections</span></span>  
 <span data-ttu-id="fdec7-121">詳細情報</span><span class="sxs-lookup"><span data-stu-id="fdec7-121">For more information:</span></span>  
  
-   [<span data-ttu-id="fdec7-122">リフレクション</span><span class="sxs-lookup"><span data-stu-id="fdec7-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="fdec7-123">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="fdec7-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="fdec7-124">リフレクションとジェネリック型</span><span class="sxs-lookup"><span data-stu-id="fdec7-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="fdec7-125">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="fdec7-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="fdec7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdec7-126">See Also</span></span>  
 [<span data-ttu-id="fdec7-127">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fdec7-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="fdec7-128">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="fdec7-128">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
