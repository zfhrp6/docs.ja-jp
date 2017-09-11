---
title: "方法 : 抽象プロパティを定義する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c6decaae138a21c24e94e2ed74111c860777f64b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="59f44-102">方法 : 抽象プロパティを定義する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="59f44-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="59f44-103">次の例では、[抽象](../../../csharp/language-reference/keywords/abstract.md)プロパティを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="59f44-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="59f44-104">抽象プロパティの宣言では、プロパティ アクセサーは実装されません。クラスがプロパティをサポートしていることは宣言しますが、アクセサーの実装は派生クラスに委ねます。</span><span class="sxs-lookup"><span data-stu-id="59f44-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="59f44-105">基本クラスから継承された抽象プロパティを実装する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="59f44-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="59f44-106">このサンプルは 3 つのファイルで構成され、それぞれ個別にコンパイルされ、生成されたアセンブリが次のコンパイルで参照されます。</span><span class="sxs-lookup"><span data-stu-id="59f44-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="59f44-107">abstractshape.cs: 抽象 `Shape` プロパティを含む `Area` クラス。</span><span class="sxs-lookup"><span data-stu-id="59f44-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="59f44-108">shapes.cs: `Shape` クラスのサブクラス。</span><span class="sxs-lookup"><span data-stu-id="59f44-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="59f44-109">shapetest.cs: いくつかの `Shape` から派生したオブジェクトの面積を表示するテスト プログラム。</span><span class="sxs-lookup"><span data-stu-id="59f44-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="59f44-110">この例をコンパイルするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="59f44-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="59f44-111">これで、実行可能ファイル shapetest.exe が作成されます。</span><span class="sxs-lookup"><span data-stu-id="59f44-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59f44-112">例</span><span class="sxs-lookup"><span data-stu-id="59f44-112">Example</span></span>  
 <span data-ttu-id="59f44-113">このファイルは、`double` 型の `Shape` プロパティを含む `Area` クラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="59f44-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 <span data-ttu-id="59f44-114">[!code-cs[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="59f44-114">[!code-cs[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]</span></span>  
  
-   <span data-ttu-id="59f44-115">プロパティの修飾子は、プロパティ宣言自体に設定されます。</span><span class="sxs-lookup"><span data-stu-id="59f44-115">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="59f44-116">例:</span><span class="sxs-lookup"><span data-stu-id="59f44-116">For example:</span></span>  
  
    ```  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="59f44-117">抽象プロパティ (この例では `Area` など) を宣言する場合は、使用可能なアクセサーを示すだけで、実装はしません。</span><span class="sxs-lookup"><span data-stu-id="59f44-117">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="59f44-118">この例では、[get](../../../csharp/language-reference/keywords/get.md) アクセサーのみが使用可能であるため、プロパティは読み取り専用となります。</span><span class="sxs-lookup"><span data-stu-id="59f44-118">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59f44-119">例</span><span class="sxs-lookup"><span data-stu-id="59f44-119">Example</span></span>  
 <span data-ttu-id="59f44-120">次のコードは、`Shape` の 3 つのサブクラスと、それらがどのように `Area` プロパティをオーバーライドして独自の実装を提供するかを示しています。</span><span class="sxs-lookup"><span data-stu-id="59f44-120">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 <span data-ttu-id="59f44-121">[!code-cs[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="59f44-121">[!code-cs[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="59f44-122">例</span><span class="sxs-lookup"><span data-stu-id="59f44-122">Example</span></span>  
 <span data-ttu-id="59f44-123">次のコードは、`Shape` から派生するオブジェクトをいくつか作成し、それらの面積を出力するテスト プログラムを示しています。</span><span class="sxs-lookup"><span data-stu-id="59f44-123">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 <span data-ttu-id="59f44-124">[!code-cs[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="59f44-124">[!code-cs[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f44-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="59f44-125">See Also</span></span>  
 <span data-ttu-id="59f44-126">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="59f44-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="59f44-127">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="59f44-127">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="59f44-128">[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="59f44-128">[Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span></span>  
 <span data-ttu-id="59f44-129">[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="59f44-129">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 [<span data-ttu-id="59f44-130">方法: コマンド ラインを使用してアセンブリを作成および使用する</span><span class="sxs-lookup"><span data-stu-id="59f44-130">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)

