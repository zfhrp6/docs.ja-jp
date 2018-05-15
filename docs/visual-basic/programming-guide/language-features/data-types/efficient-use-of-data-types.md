---
title: データ型の有効な使用方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 6e71c4e2225bbcde3bb2bd20ae098f5600990051
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="d9aeb-102">データ型の有効な使用方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9aeb-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="d9aeb-103">宣言されていない変数とデータ型なしで宣言された変数が割り当てられている、`Object`データ型。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="d9aeb-104">実行速度が低下することができるプログラムを迅速に作成するが容易になります。 可能性がします。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="d9aeb-105">厳密な型指定</span><span class="sxs-lookup"><span data-stu-id="d9aeb-105">Strong Typing</span></span>  
 <span data-ttu-id="d9aeb-106">すべての変数のデータ型の指定と呼びます*厳密な型指定*です。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="d9aeb-107">厳密な型指定を使用すると、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="d9aeb-108">IntelliSense をサポートしている変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="d9aeb-109">これにより、コードに入力すると、そのプロパティおよびその他のメンバーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="d9aeb-110">コンパイラの型チェックの利点がかかります。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="d9aeb-111">これは、実行時のオーバーフローなどのエラーにより失敗するステートメントをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="d9aeb-112">それらをサポートしないオブジェクトに対するメソッドの呼び出しをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="d9aeb-113">コードの実行を高速になります。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="d9aeb-114">最も効率的なデータ型</span><span class="sxs-lookup"><span data-stu-id="d9aeb-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="d9aeb-115">小数を含まない変数の場合は、整数データ型は、非整数型よりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="d9aeb-116">Visual basic で`Integer`と`UInteger`最も効率的な数値型です。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="d9aeb-117">小数値は、`Double`最も効率的なデータ型では、現在のプラットフォーム上のプロセッサの倍精度浮動小数点演算を実行するためです。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="d9aeb-118">ただし、操作を`Double`などの整数型と同様に高速ではない`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="d9aeb-119">データ型の指定</span><span class="sxs-lookup"><span data-stu-id="d9aeb-119">Specifying Data Type</span></span>  
 <span data-ttu-id="d9aeb-120">使用して、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)特定の型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="d9aeb-121">使用して、アクセス レベルを指定することが同時に、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)に示すように、キーワード、次の例です。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="d9aeb-122">文字の変換</span><span class="sxs-lookup"><span data-stu-id="d9aeb-122">Character Conversion</span></span>  
 <span data-ttu-id="d9aeb-123">`AscW`と`ChrW`関数は Unicode に操作します。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="d9aeb-124">優先的に使用する必要があります`Asc`と`Chr`Unicode との間に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9aeb-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9aeb-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9aeb-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="d9aeb-126">データの種類</span><span class="sxs-lookup"><span data-stu-id="d9aeb-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="d9aeb-127">数値のデータ型</span><span class="sxs-lookup"><span data-stu-id="d9aeb-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="d9aeb-128">変数宣言</span><span class="sxs-lookup"><span data-stu-id="d9aeb-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="d9aeb-129">IntelliSense の使用</span><span class="sxs-lookup"><span data-stu-id="d9aeb-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
