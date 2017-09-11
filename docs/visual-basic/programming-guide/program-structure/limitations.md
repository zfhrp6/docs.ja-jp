---
title: "Visual Basic の制限事項 |Microsoft ドキュメント"
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
helpviewer_keywords:
- limits
- limitations, Visual Basic
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a3bd551ade2f0c55cd943cfbd353b09dfede4063
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-limitations"></a><span data-ttu-id="22f20-102">Visual Basic の制限事項</span><span class="sxs-lookup"><span data-stu-id="22f20-102">Visual Basic Limitations</span></span>
<span data-ttu-id="22f20-103">以前のバージョンの[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]モジュール、およびモジュールのサイズで許可される変数の数、変数名の長さなどのコード内の境界を適用します。</span><span class="sxs-lookup"><span data-stu-id="22f20-103">Earlier versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="22f20-104">[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]、記述し、コードを配置するをより自由を与える、これらの制限は緩和されています。</span><span class="sxs-lookup"><span data-stu-id="22f20-104">In [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="22f20-105">物理的な制限よりも実行時のメモリ上よりするコンパイル時の考慮事項に依存します。</span><span class="sxs-lookup"><span data-stu-id="22f20-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="22f20-106">ごくわずかな内部が発生する可能性があるかどうかは、慎重なプログラミングの方法を使用して大規模なアプリケーションを複数のクラスと、モジュールに分割[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]制限します。</span><span class="sxs-lookup"><span data-stu-id="22f20-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] limitation.</span></span>  
  
 <span data-ttu-id="22f20-107">極端なケースで発生する可能性のあるいくつかの制限を次に示します。</span><span class="sxs-lookup"><span data-stu-id="22f20-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="22f20-108">**名の長さ。**</span><span class="sxs-lookup"><span data-stu-id="22f20-108">**Name Length.**</span></span> <span data-ttu-id="22f20-109">これは、プログラミングのすべての宣言された要素の名前を文字の最大数です。</span><span class="sxs-lookup"><span data-stu-id="22f20-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="22f20-110">この最大値は、要素名が修飾されている場合に、全体の修飾文字列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="22f20-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="22f20-111">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="22f20-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="22f20-112">**行の長さ。**</span><span class="sxs-lookup"><span data-stu-id="22f20-112">**Line Length.**</span></span> <span data-ttu-id="22f20-113">これは、ソース コードの物理的な行で 65535 文字の最大です。</span><span class="sxs-lookup"><span data-stu-id="22f20-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="22f20-114">論理ソース コード行は行継続文字を使用する場合は、長くすることはできます。</span><span class="sxs-lookup"><span data-stu-id="22f20-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="22f20-115">参照してください[方法: 分割およびコード内でステートメントを連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="22f20-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="22f20-116">**配列の次元。**</span><span class="sxs-lookup"><span data-stu-id="22f20-116">**Array Dimensions.**</span></span> <span data-ttu-id="22f20-117">これは、配列の場合、宣言するディメンションの最大数です。</span><span class="sxs-lookup"><span data-stu-id="22f20-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="22f20-118">これにより、配列要素を指定してインデックスの数が制限されます。</span><span class="sxs-lookup"><span data-stu-id="22f20-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="22f20-119">参照してください[Visual Basic における次元の配列](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)します。</span><span class="sxs-lookup"><span data-stu-id="22f20-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="22f20-120">**文字列の長さ。**</span><span class="sxs-lookup"><span data-stu-id="22f20-120">**String Length.**</span></span> <span data-ttu-id="22f20-121">これは、1 つの文字列に格納できる Unicode 文字の最大数です。</span><span class="sxs-lookup"><span data-stu-id="22f20-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="22f20-122">参照してください[文字列データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)します。</span><span class="sxs-lookup"><span data-stu-id="22f20-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="22f20-123">**環境文字列長。**</span><span class="sxs-lookup"><span data-stu-id="22f20-123">**Environment String Length.**</span></span> <span data-ttu-id="22f20-124">コマンドライン引数として使用される任意の環境文字列の 32768 文字の最大値があります。</span><span class="sxs-lookup"><span data-stu-id="22f20-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="22f20-125">これは、すべてのプラットフォームでの制限です。</span><span class="sxs-lookup"><span data-stu-id="22f20-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f20-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="22f20-126">See Also</span></span>  
 <span data-ttu-id="22f20-127">[プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="22f20-127">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="22f20-128"> [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span><span class="sxs-lookup"><span data-stu-id="22f20-128"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span></span>
