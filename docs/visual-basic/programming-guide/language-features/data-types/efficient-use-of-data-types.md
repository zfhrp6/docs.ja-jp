---
title: "データ型 (Visual Basic) を効率的に使用 |Microsoft ドキュメント"
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
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function, preferred to Asc
- data types [Visual Basic], using efficiently
- optimization, data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function, preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
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
ms.openlocfilehash: ca8d5885aea12a3f1f9cb35f08bf63c1a89e7ebc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="8de62-102">データ型の有効な使用方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8de62-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="8de62-103">宣言されていない変数とデータ型なしで宣言された変数が割り当てられている、`Object`データ型。</span><span class="sxs-lookup"><span data-stu-id="8de62-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="8de62-104">これにより、プログラムの記述を簡単にが実行速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="8de62-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="8de62-105">厳密な型指定</span><span class="sxs-lookup"><span data-stu-id="8de62-105">Strong Typing</span></span>  
 <span data-ttu-id="8de62-106">すべての変数のデータ型の指定と呼ばれます*厳密な型指定*します。</span><span class="sxs-lookup"><span data-stu-id="8de62-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="8de62-107">厳密な型指定を使用すると、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="8de62-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="8de62-108">これにより、IntelliSense での変数をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="8de62-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="8de62-109">これにより、コードに入力すると、そのプロパティおよびその他のメンバーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8de62-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="8de62-110">これは、コンパイラの型チェック利用をします。</span><span class="sxs-lookup"><span data-stu-id="8de62-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="8de62-111">これは、実行時のオーバーフローなどのエラーにより失敗するステートメントを検出します。</span><span class="sxs-lookup"><span data-stu-id="8de62-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="8de62-112">サポートしていないオブジェクトに対するメソッドの呼び出しをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="8de62-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="8de62-113">コードの実行を高速になります。</span><span class="sxs-lookup"><span data-stu-id="8de62-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="8de62-114">最も効率的なデータ型</span><span class="sxs-lookup"><span data-stu-id="8de62-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="8de62-115">小数を含まない変数の場合は、整数データ型は、非整数型よりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="8de62-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="8de62-116">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、`Integer`と`UInteger`は最も効率的な数値型。</span><span class="sxs-lookup"><span data-stu-id="8de62-116">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="8de62-117">小数値`Double`を最も効率的なデータ型は、現在のプラットフォーム上のプロセッサでは、倍精度浮動小数点演算を実行するためです。</span><span class="sxs-lookup"><span data-stu-id="8de62-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="8de62-118">ただし、操作が`Double`などの整数型と同様に高速ではない`Integer`します。</span><span class="sxs-lookup"><span data-stu-id="8de62-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="8de62-119">データ型の指定</span><span class="sxs-lookup"><span data-stu-id="8de62-119">Specifying Data Type</span></span>  
 <span data-ttu-id="8de62-120">使用して、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)特定の型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="8de62-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="8de62-121">同時に使用してアクセス レベルを指定することができます、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワードは、次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="8de62-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="8de62-122">文字の変換</span><span class="sxs-lookup"><span data-stu-id="8de62-122">Character Conversion</span></span>  
 <span data-ttu-id="8de62-123">`AscW`と`ChrW`関数は Unicode に操作します。</span><span class="sxs-lookup"><span data-stu-id="8de62-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="8de62-124">優先的に使用する必要があります`Asc`と`Chr`Unicode との間に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8de62-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de62-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8de62-125">See Also</span></span>  
 <span data-ttu-id="8de62-126"><xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A></span><span class="sxs-lookup"><span data-stu-id="8de62-126"><xref:Microsoft.VisualBasic.Strings.Asc%2A></span></span>   
 <span data-ttu-id="8de62-127"><xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="8de62-127"><xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>   
 <span data-ttu-id="8de62-128"><xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A></span><span class="sxs-lookup"><span data-stu-id="8de62-128"><xref:Microsoft.VisualBasic.Strings.Chr%2A></span></span>   
 <span data-ttu-id="8de62-129"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="8de62-129"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>   
<span data-ttu-id="8de62-130"> [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="8de62-130"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="8de62-131"> [数値データ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="8de62-131"> [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span></span>  
<span data-ttu-id="8de62-132"> [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="8de62-132"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="8de62-133"> [IntelliSense の使用](https://docs.microsoft.com/visualstudio/ide/using-intellisense)</span><span class="sxs-lookup"><span data-stu-id="8de62-133"> [Using IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)</span></span>
