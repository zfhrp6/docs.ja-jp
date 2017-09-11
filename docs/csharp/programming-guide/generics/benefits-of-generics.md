---
title: "ジェネリックの利点 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: 23
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
ms.openlocfilehash: 8b05a3a695064764618564293e6ccd92e2ce60be
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="benefits-of-generics-c-programming-guide"></a><span data-ttu-id="62264-102">ジェネリックの利点 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="62264-102">Benefits of Generics (C# Programming Guide)</span></span>
<span data-ttu-id="62264-103">ジェネリックを使用することによって、汎用基本データ型 <xref:System.Object> との値で型をキャストして一般化を行う、共通言語ランタイムや C# 言語の以前のバージョンの制限を解決できます。</span><span class="sxs-lookup"><span data-stu-id="62264-103">Generics provide the solution to a limitation in earlier versions of the common language runtime and the C# language in which generalization is accomplished by casting types to and from the universal base type <xref:System.Object>.</span></span> <span data-ttu-id="62264-104">ジェネリック クラスを作成すると、コンパイル時にタイプ セーフなコレクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="62264-104">By creating a generic class, you can create a collection that is type-safe at compile-time.</span></span>  
  
 <span data-ttu-id="62264-105">ジェネリック以外のコレクション クラスを使用する際の制限は、.NET Framework クラス ライブラリの <xref:System.Collections.ArrayList> コレクション クラスを使用する短いプログラムを作成してみるとわかります。</span><span class="sxs-lookup"><span data-stu-id="62264-105">The limitations of using non-generic collection classes can be demonstrated by writing a short program that uses the <xref:System.Collections.ArrayList> collection class from the .NET Framework class library.</span></span> <span data-ttu-id="62264-106"><xref:System.Collections.ArrayList> は、変更なしで参照型や値型を格納できる便利なコレクション クラスです。</span><span class="sxs-lookup"><span data-stu-id="62264-106"><xref:System.Collections.ArrayList> is a highly convenient collection class that can be used without modification to store any reference or value type.</span></span>  
  
 <span data-ttu-id="62264-107">[!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="62264-107">[!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]</span></span>  
  
 <span data-ttu-id="62264-108">ただし、この利便性の一方でマイナス面もあります。</span><span class="sxs-lookup"><span data-stu-id="62264-108">But this convenience comes at a cost.</span></span> <span data-ttu-id="62264-109"><xref:System.Collections.ArrayList> に追加される参照型や値型は暗黙的に <xref:System.Object> にアップキャストされます。</span><span class="sxs-lookup"><span data-stu-id="62264-109">Any reference or value type that is added to an <xref:System.Collections.ArrayList> is implicitly upcast to <xref:System.Object>.</span></span> <span data-ttu-id="62264-110">項目が値型の場合は、リストに追加するときにボックス化し、取得するときにボックス化解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62264-110">If the items are value types, they must be boxed when they are added to the list, and unboxed when they are retrieved.</span></span> <span data-ttu-id="62264-111">キャスト操作も、ボックス化/ボックス化解除操作も、パフォーマンスに悪い影響を及ぼします。特に、ボックス化およびボックス化解除の影響は、大型のコレクションの反復処理が必要な場合に非常に大きくなります。</span><span class="sxs-lookup"><span data-stu-id="62264-111">Both the casting and the boxing and unboxing operations decrease performance; the effect of boxing and unboxing can be very significant in scenarios where you must iterate over large collections.</span></span>  
  
 <span data-ttu-id="62264-112">また、コンパイル時の型チェックがないという制限もあります。<xref:System.Collections.ArrayList> はすべてを <xref:System.Object> にキャストするため、コンパイル時にクライアント コードが次のような処理を行うのを防ぐことができません。</span><span class="sxs-lookup"><span data-stu-id="62264-112">The other limitation is lack of compile-time type checking; because an <xref:System.Collections.ArrayList> casts everything to <xref:System.Object>, there is no way at compile-time to prevent client code from doing something such as this:</span></span>  
  
 <span data-ttu-id="62264-113">[!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="62264-113">[!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]</span></span>  
  
 <span data-ttu-id="62264-114">異種コレクションを作成することは有効であり、意図的に行うこともありますが、その場合、文字列と `ints` を 1 つの <xref:System.Collections.ArrayList> に組み合わせると、プログラミング エラーになる可能性があります。このエラーは、実行時まで検出されません。</span><span class="sxs-lookup"><span data-stu-id="62264-114">Although perfectly acceptable and sometimes intentional if you are creating a heterogeneous collection, combining strings and `ints` in a single <xref:System.Collections.ArrayList> is more likely to be a programming error, and this error will not be detected until runtime.</span></span>  
  
 <span data-ttu-id="62264-115">C# 言語のバージョン 1.0 および 1.1 では、.NET Framework 基本クラス ライブラリのコレクション クラスにおける一般化されたコードの問題は、独自の型に固有のコレクションを記述することによってのみ回避できました。</span><span class="sxs-lookup"><span data-stu-id="62264-115">In versions 1.0 and 1.1 of the C# language, you could avoid the dangers of generalized code in the .NET Framework base class library collection classes only by writing your own type specific collections.</span></span> <span data-ttu-id="62264-116">もちろん、このようなクラスは複数のデータ型で再利用できないため、一般化のメリットがなく、格納する型ごとにクラスを書き直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="62264-116">Of course, because such a class is not reusable for more than one data type, you lose the benefits of generalization, and you have to rewrite the class for each type that will be stored.</span></span>  
  
 <span data-ttu-id="62264-117"><xref:System.Collections.ArrayList> や他の同じようなクラスで実際に必要なのは、クライアント コードで、使用する特定のデータ型をインスタンスごとに指定する方法です。</span><span class="sxs-lookup"><span data-stu-id="62264-117">What <xref:System.Collections.ArrayList> and other similar classes really need is a way for client code to specify, on a per-instance basis, the particular data type that they intend to use.</span></span> <span data-ttu-id="62264-118">このような方法があれば、`T:System.Object` にアップキャストする必要性がなくなり、また、コンパイラが型チェックを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="62264-118">That would eliminate the need for the upcast to `T:System.Object` and would also make it possible for the compiler to do type checking.</span></span> <span data-ttu-id="62264-119">言い換えれば、<xref:System.Collections.ArrayList> には型パラメーターが必要なのです。</span><span class="sxs-lookup"><span data-stu-id="62264-119">In other words, <xref:System.Collections.ArrayList> needs a type parameter.</span></span> <span data-ttu-id="62264-120">これを実現するのがジェネリックです。</span><span class="sxs-lookup"><span data-stu-id="62264-120">That is exactly what generics provide.</span></span> <span data-ttu-id="62264-121">`N:System.Collections.Generic` 名前空間のジェネリック <xref:System.Collections.Generic.List%601> コレクションでは、コレクションに項目を追加するという同じ操作が次のようになります。</span><span class="sxs-lookup"><span data-stu-id="62264-121">In the generic <xref:System.Collections.Generic.List%601> collection, in the `N:System.Collections.Generic` namespace, the same operation of adding items to the collection resembles this:</span></span>  
  
 <span data-ttu-id="62264-122">[!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="62264-122">[!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]</span></span>  
  
 <span data-ttu-id="62264-123">クライアント コードでは、<xref:System.Collections.ArrayList> と比較される <xref:System.Collections.Generic.List%601> と共に追加される構文は、宣言とインスタンス化での型引数だけです。</span><span class="sxs-lookup"><span data-stu-id="62264-123">For client code, the only added syntax with <xref:System.Collections.Generic.List%601> compared to <xref:System.Collections.ArrayList> is the type argument in the declaration and instantiation.</span></span> <span data-ttu-id="62264-124">このようにコーディングは若干複雑になりますが、それと引き換えに、<xref:System.Collections.ArrayList> よりも安全であるだけでなく、特にリスト項目が値型のときには処理時間が大幅に短縮されるリストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="62264-124">In return for this slightly more coding complexity, you can create a list that is not only safer than <xref:System.Collections.ArrayList>, but also significantly faster, especially when the list items are value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62264-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="62264-125">See Also</span></span>  
 <span data-ttu-id="62264-126"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="62264-126"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="62264-127">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="62264-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="62264-128">[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="62264-128">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 <span data-ttu-id="62264-129">[ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md) </span><span class="sxs-lookup"><span data-stu-id="62264-129">[Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md) </span></span>  
 [<span data-ttu-id="62264-130">コレクションのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="62264-130">Collections Best Practices</span></span>](http://go.microsoft.com/fwlink/?LinkId=112403)

