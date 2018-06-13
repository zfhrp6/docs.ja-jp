---
title: extern エイリアス (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: a2803d09ee64af854cad352f6a158fb84bb6d410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217390"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="6d9ff-102">extern エイリアス (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6d9ff-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="6d9ff-103">場合によっては、同じ完全修飾型名を持つ、2 つのバージョンのアセンブリを参照する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="6d9ff-104">たとえば、同じアプリケーション内で、2 つ以上のバージョンのアセンブリを使用する必要が生じることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="6d9ff-105">外部アセンブリ エイリアスを使用すれば、各アセンブリの名前空間を、エイリアスを付けたルート レベルの名前空間内でラップして、それらを同じファイル内で使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d9ff-106">[extern](../../../csharp/language-reference/keywords/extern.md) キーワードは、アンマネージ コードで記述されたメソッドを宣言するために、メソッド修飾子として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="6d9ff-107">同じ完全修飾型名を持つ 2 つのアセンブリを参照するには、コマンド プロンプトで次のようにエイリアスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="6d9ff-108">これにより、外部エイリアス `GridV1` および `GridV2` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="6d9ff-109">これらのエイリアスをプログラム内から使用するには、`extern` キーワードを使用してそれらを参照します。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="6d9ff-110">例:</span><span class="sxs-lookup"><span data-stu-id="6d9ff-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="6d9ff-111">各 extern エイリアスの宣言では、グローバル名前空間に対応する (ただし、グローバル名前空間内にはない) 追加のルート レベル名前空間が導入されています。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="6d9ff-112">そのため、各アセンブリの型は、適切な名前空間エイリアスをルートに持つ完全修飾名を使用して、明確に参照することができます。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="6d9ff-113">前の例では、`GridV1::Grid` が `grid.dll` からのグリッド コントロールで、`GridV2::Grid` が `grid20.dll` からのグリッド コントロールになります。</span><span class="sxs-lookup"><span data-stu-id="6d9ff-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6d9ff-114">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6d9ff-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d9ff-115">参照</span><span class="sxs-lookup"><span data-stu-id="6d9ff-115">See Also</span></span>  
 [<span data-ttu-id="6d9ff-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6d9ff-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6d9ff-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6d9ff-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d9ff-118">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="6d9ff-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6d9ff-119">名前空間キーワード</span><span class="sxs-lookup"><span data-stu-id="6d9ff-119">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="6d9ff-120">:: 演算子</span><span class="sxs-lookup"><span data-stu-id="6d9ff-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="6d9ff-121">-reference (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="6d9ff-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
