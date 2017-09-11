---
title: "リフレクション (C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fa0aee4a0580ea28e3f0c70528dabaaf6f635f71
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="reflection-c"></a><span data-ttu-id="427d3-102">リフレクション (C#)</span><span class="sxs-lookup"><span data-stu-id="427d3-102">Reflection (C#)</span></span>
<span data-ttu-id="427d3-103">リフレクションは、アセンブリ、モジュール、および型を記述する (<xref:System.Type> 型の) オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="427d3-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="427d3-104">リフレクションを使用すると、動的に型のインスタンスを作成したり、作成したインスタンスを既存のオブジェクトにバインドしたり、さらに既存のオブジェクトから型を取得してそのオブジェクトのメソッドを呼び出したり、フィールドやプロパティにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="427d3-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="427d3-105">コードで属性を使用している場合は、リフレクションを使用してそれらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="427d3-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="427d3-106">詳細については、「[属性](https://msdn.microsoft.com/library/5x6cd29c)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="427d3-106">For more information, see [Attributes](https://msdn.microsoft.com/library/5x6cd29c).</span></span>  
  
 <span data-ttu-id="427d3-107">次の例は、`GetType` メソッドを使用して変数の型を取得する簡単なリフレクションを示しています。このメソッドは、`Object` 基底クラスからすべての型に継承される静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="427d3-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="427d3-108">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="427d3-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="427d3-109">次の例では、リフレクションを使用して、読み込まれたアセンブリの完全名を取得します。</span><span class="sxs-lookup"><span data-stu-id="427d3-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="427d3-110">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="427d3-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="427d3-111">C# の `protected` キーワードと `internal` キーワードは、IL では意味を持たないため、リフレクション API でも使用されません。</span><span class="sxs-lookup"><span data-stu-id="427d3-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="427d3-112">IL では、"*ファミリ*" および "*アセンブリ*" という用語がこれに相当します。</span><span class="sxs-lookup"><span data-stu-id="427d3-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="427d3-113">リフレクションを使用して `internal` メソッドを指定するには、<xref:System.Reflection.MethodBase.IsAssembly%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="427d3-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="427d3-114">`protected internal` メソッドを指定するには、<xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="427d3-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="427d3-115">リフレクションの概要</span><span class="sxs-lookup"><span data-stu-id="427d3-115">Reflection Overview</span></span>  
 <span data-ttu-id="427d3-116">リフレクションは、次の場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="427d3-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="427d3-117">プログラムのメタデータ内の属性にアクセスする必要がある。</span><span class="sxs-lookup"><span data-stu-id="427d3-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="427d3-118">詳細については、「[属性に格納されている情報の取得](../../../standard/attributes/retrieving-information-stored-in-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="427d3-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="427d3-119">アセンブリの型をチェックし、インスタンス化する。</span><span class="sxs-lookup"><span data-stu-id="427d3-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="427d3-120">実行時に新しい型を作成する。</span><span class="sxs-lookup"><span data-stu-id="427d3-120">For building new types at runtime.</span></span> <span data-ttu-id="427d3-121"><xref:System.Reflection.Emit> でクラスを使います。</span><span class="sxs-lookup"><span data-stu-id="427d3-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="427d3-122">遅延バインディングを実行するために、実行時に作成された型でメソッドにアクセスする。</span><span class="sxs-lookup"><span data-stu-id="427d3-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="427d3-123">「[型の動的な読み込みおよび使用](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="427d3-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="427d3-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="427d3-124">Related Sections</span></span>  
 <span data-ttu-id="427d3-125">詳細情報</span><span class="sxs-lookup"><span data-stu-id="427d3-125">For more information:</span></span>  
  
-   [<span data-ttu-id="427d3-126">リフレクション</span><span class="sxs-lookup"><span data-stu-id="427d3-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="427d3-127">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="427d3-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="427d3-128">リフレクションとジェネリック型</span><span class="sxs-lookup"><span data-stu-id="427d3-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="427d3-129">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="427d3-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="427d3-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="427d3-130">See Also</span></span>  
 <span data-ttu-id="427d3-131">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="427d3-131">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="427d3-132">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="427d3-132">Assemblies in the Common Language Runtime</span></span>](https://msdn.microsoft.com/library/k3677y81)

