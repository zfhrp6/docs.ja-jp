---
title: "名前 &quot;&lt;名前&gt;&quot; が宣言されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
dev_langs:
- VB
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
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
ms.openlocfilehash: 1396f24a34a37db064e73d7e259c04050f409ad2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="e462c-102">名前 '&lt;名前&gt;' が宣言されていません。</span><span class="sxs-lookup"><span data-stu-id="e462c-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="e462c-103">プログラミングの要素をステートメントが、コンパイラはその正確な名前を持つ要素を見つけられないです。</span><span class="sxs-lookup"><span data-stu-id="e462c-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="e462c-104">**エラー ID:** BC30451</span><span class="sxs-lookup"><span data-stu-id="e462c-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e462c-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e462c-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="e462c-106">参照元のステートメントで名前のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="e462c-106">Check the spelling of the name in the referring statement.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="e462c-107">小文字を区別しない、その他の違いが完全に別の名前と見なされますが、します。</span><span class="sxs-lookup"><span data-stu-id="e462c-107"> is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="e462c-108">アンダースコア (`_`) も名前の一部であり、スペルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="e462c-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="e462c-109">メンバー アクセス演算子があることを確認 (`.`) オブジェクトとメンバーの間です。</span><span class="sxs-lookup"><span data-stu-id="e462c-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="e462c-110">ある場合など、<xref:System.Windows.Forms.TextBox>という名前のコントロール`TextBox1`にアクセスするには、その<xref:System.Windows.Forms.TextBoxBase.Text%2A>プロパティを入力する必要があります`TextBox1.Text`</xref:System.Windows.Forms.TextBoxBase.Text%2A></xref:System.Windows.Forms.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="e462c-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="e462c-111">代わりに「 `TextBox1Text`」と入力した場合、別の名前と見なされます。</span><span class="sxs-lookup"><span data-stu-id="e462c-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="e462c-112">スペルが正しい、オブジェクト メンバー アクセスの構文が正しい場合は、要素が宣言されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e462c-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="e462c-113">詳細については、次を参照してください。[宣言された要素](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="e462c-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="e462c-114">プログラミングの要素が宣言された場合は、スコープ内にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e462c-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="e462c-115">参照元のステートメントがプログラミングの要素が宣言されている領域の外側にある場合は、要素名を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e462c-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="e462c-116">詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)します。</span><span class="sxs-lookup"><span data-stu-id="e462c-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e462c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e462c-117">See Also</span></span>  
 <span data-ttu-id="e462c-118">[宣言と定数の概要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md) </span><span class="sxs-lookup"><span data-stu-id="e462c-118">[Declarations and Constants Summary](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md) </span></span>  
<span data-ttu-id="e462c-119"> [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="e462c-119"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="e462c-120"> [宣言された要素名](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="e462c-120"> [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="e462c-121"> [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="e462c-121"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
