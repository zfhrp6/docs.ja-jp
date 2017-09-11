---
title: "汎用デリゲート (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
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
ms.openlocfilehash: be067e2a2e2a192da8ccc92b60af81f0999c449a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="c70b5-102">汎用デリゲート (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c70b5-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="c70b5-103">[デリゲート](../../../csharp/language-reference/keywords/delegate.md)はその独自の型パラメーターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="c70b5-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="c70b5-104">ジェネリック デリゲートを参照するコードは、次の例に示すように、ジェネリック クラスをインスタンス化したり、ジェネリック メソッドを呼び出したりするときのように、型引数を指定し、構築されたクローズ型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="c70b5-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 <span data-ttu-id="c70b5-105">[!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c70b5-105">[!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]</span></span>  
  
 <span data-ttu-id="c70b5-106">C# バージョン 2.0 には、メソッド グループ変換という新しい機能があります。これはジェネリック デリゲート型だけでなく具象型にも適用され、前の行を次のような簡素化された構文で記述できます。</span><span class="sxs-lookup"><span data-stu-id="c70b5-106">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 <span data-ttu-id="c70b5-107">[!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c70b5-107">[!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]</span></span>  
  
 <span data-ttu-id="c70b5-108">ジェネリック クラス内で定義されたデリゲートは、クラス メソッドと同様の方法でジェネリック クラスの型パラメーターを利用できます。</span><span class="sxs-lookup"><span data-stu-id="c70b5-108">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 <span data-ttu-id="c70b5-109">[!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c70b5-109">[!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]</span></span>  
  
 <span data-ttu-id="c70b5-110">デリゲートを参照するコードで、次のように、包含クラスの型引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c70b5-110">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 <span data-ttu-id="c70b5-111">[!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c70b5-111">[!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]</span></span>  
  
 <span data-ttu-id="c70b5-112">ジェネリック デリゲートは、典型的な設計パターンに基づいてイベントを定義する場合に特に便利です。sender 引数は厳密に型指定できること、<xref:System.Object> との間でキャストが必要ないことがその理由です。</span><span class="sxs-lookup"><span data-stu-id="c70b5-112">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="c70b5-113">[!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="c70b5-113">[!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70b5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c70b5-114">See Also</span></span>  
 <span data-ttu-id="c70b5-115"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="c70b5-115"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="c70b5-116">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c70b5-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c70b5-117">[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="c70b5-117">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 <span data-ttu-id="c70b5-118">[ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="c70b5-118">[Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md) </span></span>  
 <span data-ttu-id="c70b5-119">[ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md) </span><span class="sxs-lookup"><span data-stu-id="c70b5-119">[Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md) </span></span>  
 <span data-ttu-id="c70b5-120">[ジェネリック インターフェイス](../../../csharp/programming-guide/generics/generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="c70b5-120">[Generic Interfaces](../../../csharp/programming-guide/generics/generic-interfaces.md) </span></span>  
 <span data-ttu-id="c70b5-121">[デリゲート](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="c70b5-121">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 [<span data-ttu-id="c70b5-122">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="c70b5-122">Generics</span></span>](~/docs/standard/generics/index.md)

