---
title: 名前 &#39;&lt;名前&gt;&#39; が宣言されていません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a63ae74c7179d71756e2b9b4bf6b41a71ce12a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="58816-102">名前 &#39;&lt;名前&gt;&#39; が宣言されていません</span><span class="sxs-lookup"><span data-stu-id="58816-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="58816-103">ステートメントがプログラミング要素を参照しますが、コンパイラはその正確な名前を持つ要素を見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="58816-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="58816-104">**エラー ID:** BC30451</span><span class="sxs-lookup"><span data-stu-id="58816-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58816-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="58816-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="58816-106">参照元のステートメントで名前のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="58816-106">Check the spelling of the name in the referring statement.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="58816-107">小文字を区別しない、スペルにその他の違いは、完全に別の名前と見なされますが、します。</span><span class="sxs-lookup"><span data-stu-id="58816-107"> is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="58816-108">アンダースコア (`_`) も名前の一部であり、スペルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="58816-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="58816-109">メンバー アクセス演算子があることを確認 (`.`) オブジェクトとメンバーの間です。</span><span class="sxs-lookup"><span data-stu-id="58816-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="58816-110">たとえば、 <xref:System.Windows.Forms.TextBox> という名前の `TextBox1`コントロールがある場合、このコントロールの <xref:System.Windows.Forms.TextBoxBase.Text%2A> プロパティにアクセスするには、「 `TextBox1.Text`」と入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58816-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="58816-111">代わりに「 `TextBox1Text`」と入力した場合、別の名前と見なされます。</span><span class="sxs-lookup"><span data-stu-id="58816-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="58816-112">スペルが正しい、オブジェクト メンバー アクセスの構文が正しい場合は、要素が宣言されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="58816-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="58816-113">詳細については、次を参照してください。[要素の宣言](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="58816-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="58816-114">プログラミング要素が宣言されている場合は、スコープ内にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="58816-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="58816-115">参照元のステートメントがプログラミング要素が宣言領域の外側にある場合は、要素名を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58816-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="58816-116">詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)です。</span><span class="sxs-lookup"><span data-stu-id="58816-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58816-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="58816-117">See Also</span></span>  
 [<span data-ttu-id="58816-118">宣言と定数の概要</span><span class="sxs-lookup"><span data-stu-id="58816-118">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [<span data-ttu-id="58816-119">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="58816-119">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="58816-120">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="58816-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="58816-121">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="58816-121">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
