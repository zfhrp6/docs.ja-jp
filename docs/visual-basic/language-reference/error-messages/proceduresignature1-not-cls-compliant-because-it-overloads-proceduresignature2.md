---
title: "&lt;proceduresignature1&gt;はオーバー ロードするため、CLS に準拠していない&lt;proceduresignature2&gt;が異なるか配列パラメーター型の配列または配列パラメーター型のランクのみ |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
dev_langs:
- VB
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
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
ms.openlocfilehash: d106f59e3faa317f67ee92ddcec8416eeff745d4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="c135c-102">&lt;proceduresignature1&gt;はオーバー ロードするため、CLS に準拠していない&lt;proceduresignature2&gt;が異なるか配列パラメーター型の配列または配列パラメーター型のランク</span><span class="sxs-lookup"><span data-stu-id="c135c-102">&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="c135c-103">プロシージャやプロパティとしてマーク`<CLSCompliant(True)>`と別のプロシージャまたはプロパティを上書きされ、パラメーター リストの唯一の違いは、ジャグ配列の入れ子レベルまたは配列のランク。</span><span class="sxs-lookup"><span data-stu-id="c135c-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="c135c-104">次の宣言では、2 番目と&3; 番目の宣言は、このエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="c135c-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="c135c-105">2 番目の宣言元の&1; 次元のパラメーターを変更する`arrayParam`配列の配列にします。</span><span class="sxs-lookup"><span data-stu-id="c135c-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="c135c-106">3 番目の宣言の変更`arrayParam`2 次元配列 (rank 2) にします。</span><span class="sxs-lookup"><span data-stu-id="c135c-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="c135c-107">Visual Basic でこれらの変更の&1; つだけが異なるためのオーバー ロードは、中にこのようなオーバー ロードが準拠していない、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS に) します。</span><span class="sxs-lookup"><span data-stu-id="c135c-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span>  
  
 <span data-ttu-id="c135c-108">適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c135c-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="c135c-109">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c135c-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="c135c-110">適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c135c-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="c135c-111">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="c135c-111">By default, this message is a warning.</span></span> <span data-ttu-id="c135c-112">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c135c-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c135c-113">**エラー ID:** BC40035</span><span class="sxs-lookup"><span data-stu-id="c135c-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c135c-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c135c-114">To correct this error</span></span>  
  
-   <span data-ttu-id="c135c-115">CLS 準拠を必要とする場合は、このページで示されている変更のみよりも多くの方法で互いに異なる、オーバー ロードを定義します。</span><span class="sxs-lookup"><span data-stu-id="c135c-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="c135c-116">このヘルプに示した変更点だけがページで、削除、オーバー ロードが異なることが必要な場合、<xref:System.CLSCompliantAttribute>定義からとしてマーク`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c135c-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c135c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c135c-117">See Also</span></span>  
 <span data-ttu-id="c135c-118">[\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3) </span><span class="sxs-lookup"><span data-stu-id="c135c-118">[\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3) </span></span>  
<span data-ttu-id="c135c-119"> [プロシージャのオーバー ロード](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="c135c-119"> [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md) </span></span>  
<span data-ttu-id="c135c-120"> [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="c135c-120"> [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>
