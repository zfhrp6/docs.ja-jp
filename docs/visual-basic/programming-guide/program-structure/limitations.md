---
title: Visual Basic の制限事項
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 57378c3aa18a5cc108c10e8654e55803f3cf9052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649930"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="9f849-102">Visual Basic の制限事項</span><span class="sxs-lookup"><span data-stu-id="9f849-102">Visual Basic Limitations</span></span>
<span data-ttu-id="9f849-103">以前のバージョンの Visual Basic では、変数名、モジュール、およびモジュールのサイズで許可される変数の数の長さなどのコード内の境界が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9f849-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="9f849-104">Visual Basic .net では、これらの制限が緩和されました、記述と、コードの配置をより自由が提供します。</span><span class="sxs-lookup"><span data-stu-id="9f849-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="9f849-105">物理的な制限よりも実行時のメモリ上よりするコンパイル時の考慮事項に依存します。</span><span class="sxs-lookup"><span data-stu-id="9f849-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="9f849-106">万全を期してのプログラミング方法を使用して大規模なアプリケーションを複数のクラスとモジュールに分割する場合は、内部の Visual Basic の制限にぶつかる可能性はほとんどです。</span><span class="sxs-lookup"><span data-stu-id="9f849-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="9f849-107">極端なケースで発生する可能性のあるいくつかの制限を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9f849-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="9f849-108">**名の長さ。**</span><span class="sxs-lookup"><span data-stu-id="9f849-108">**Name Length.**</span></span> <span data-ttu-id="9f849-109">すべての宣言されたプログラミング要素の名前の文字の最大数があります。</span><span class="sxs-lookup"><span data-stu-id="9f849-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="9f849-110">この最大値は、要素名が修飾されている場合に、全体の修飾文字列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9f849-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="9f849-111">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f849-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="9f849-112">**行の長さ。**</span><span class="sxs-lookup"><span data-stu-id="9f849-112">**Line Length.**</span></span> <span data-ttu-id="9f849-113">これは、ソース コードの物理的な行で値 65535 文字の最大です。</span><span class="sxs-lookup"><span data-stu-id="9f849-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="9f849-114">論理ソース コード行を行継続文字を使用する場合は、長いことはできます。</span><span class="sxs-lookup"><span data-stu-id="9f849-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="9f849-115">参照してください[する方法: 分割および連結コード内でステートメント](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f849-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="9f849-116">**配列の次元です。**</span><span class="sxs-lookup"><span data-stu-id="9f849-116">**Array Dimensions.**</span></span> <span data-ttu-id="9f849-117">配列で宣言できるディメンションの最大数があります。</span><span class="sxs-lookup"><span data-stu-id="9f849-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="9f849-118">これにより、配列の要素を指定する使用できるインデックスの数が制限されます。</span><span class="sxs-lookup"><span data-stu-id="9f849-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="9f849-119">参照してください[Visual Basic でのディメンションを配列](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f849-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="9f849-120">**文字列の長さ。**</span><span class="sxs-lookup"><span data-stu-id="9f849-120">**String Length.**</span></span> <span data-ttu-id="9f849-121">1 つの文字列に格納できる Unicode 文字の最大数があります。</span><span class="sxs-lookup"><span data-stu-id="9f849-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="9f849-122">参照してください[文字列データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f849-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="9f849-123">**環境文字列の長さ。**</span><span class="sxs-lookup"><span data-stu-id="9f849-123">**Environment String Length.**</span></span> <span data-ttu-id="9f849-124">これは、コマンドライン引数として使用される任意の環境文字列 32768 文字の最大です。</span><span class="sxs-lookup"><span data-stu-id="9f849-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="9f849-125">これは、すべてのプラットフォームでの制限です。</span><span class="sxs-lookup"><span data-stu-id="9f849-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f849-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f849-126">See Also</span></span>  
 [<span data-ttu-id="9f849-127">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="9f849-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="9f849-128">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="9f849-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
