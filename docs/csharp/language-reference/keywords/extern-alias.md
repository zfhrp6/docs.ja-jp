---
title: "extern エイリアス (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- alias_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
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
ms.openlocfilehash: 66b399aaf6d4b3ba27957f3eadad3c1079ed2e90
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="77c72-102">extern エイリアス (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="77c72-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="77c72-103">場合によっては、同じ完全修飾型名を持つ、2 つのバージョンのアセンブリを参照する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="77c72-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="77c72-104">たとえば、同じアプリケーション内で、2 つ以上のバージョンのアセンブリを使用する必要が生じることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="77c72-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="77c72-105">外部アセンブリ エイリアスを使用すれば、各アセンブリの名前空間を、エイリアスを付けたルート レベルの名前空間内でラップして、それらを同じファイル内で使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="77c72-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77c72-106">[extern](../../../csharp/language-reference/keywords/extern.md) キーワードは、アンマネージ コードで記述されたメソッドを宣言するために、メソッド修飾子として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="77c72-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="77c72-107">同じ完全修飾型名を持つ 2 つのアセンブリを参照するには、コマンド プロンプトで次のようにエイリアスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77c72-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="77c72-108">これにより、外部エイリアス `GridV1` および `GridV2` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="77c72-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="77c72-109">これらのエイリアスをプログラム内から使用するには、`extern` キーワードを使用してそれらを参照します。</span><span class="sxs-lookup"><span data-stu-id="77c72-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="77c72-110">例:</span><span class="sxs-lookup"><span data-stu-id="77c72-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="77c72-111">各 extern エイリアスの宣言では、グローバル名前空間に対応する (ただし、グローバル名前空間内にはない) 追加のルート レベル名前空間が導入されています。</span><span class="sxs-lookup"><span data-stu-id="77c72-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="77c72-112">そのため、各アセンブリの型は、適切な名前空間エイリアスをルートに持つ完全修飾名を使用して、明確に参照することができます。</span><span class="sxs-lookup"><span data-stu-id="77c72-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="77c72-113">前の例では、`GridV1::Grid` が `grid.dll` からのグリッド コントロールで、`GridV2::Grid` が `grid20.dll` からのグリッド コントロールになります。</span><span class="sxs-lookup"><span data-stu-id="77c72-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="77c72-114">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="77c72-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77c72-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="77c72-115">See Also</span></span>  
 <span data-ttu-id="77c72-116">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="77c72-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="77c72-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="77c72-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="77c72-118">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="77c72-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="77c72-119">[名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="77c72-119">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 <span data-ttu-id="77c72-120">[:: 演算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span><span class="sxs-lookup"><span data-stu-id="77c72-120">[:: Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span></span>  
 [<span data-ttu-id="77c72-121">-reference (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="77c72-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)

