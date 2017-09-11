---
title: "省略可能なパラメーターの省略可能な値の型&lt;parametername&gt; CLS 準拠ではありません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
dev_langs:
- VB
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: 8
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
ms.openlocfilehash: 4954c241b7cb704ebb9373d837bb1e51c1b44115
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a><span data-ttu-id="0bad3-102">省略可能なパラメーターの省略可能な値の型&lt;parametername&gt; CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="0bad3-102">Type of optional value for optional parameter &lt;parametername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="0bad3-103">プロシージャは `<CLSCompliant(True)>` に設定されていますが、非準拠の型が既定値である [Optional](../../../visual-basic/language-reference/modifiers/optional.md) パラメーターが宣言されています。</span><span class="sxs-lookup"><span data-stu-id="0bad3-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="0bad3-104">プロシージャを[言語への非依存性および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3) (CLS) に準拠させるには、CLS 準拠型のみを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bad3-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="0bad3-105">これは、パラメーターの型、戻り値の型、およびすべてのローカル変数の型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="0bad3-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="0bad3-106">また、省略可能なパラメーターの既定値にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="0bad3-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="0bad3-107">次の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="0bad3-107">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="0bad3-108">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="0bad3-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="0bad3-109">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="0bad3-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="0bad3-110">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="0bad3-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="0bad3-111">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="0bad3-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="0bad3-112">適用すると、<xref:System.CLSCompliantAttribute>属性プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0bad3-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0bad3-113">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bad3-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="0bad3-114">適用しない場合<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0bad3-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="0bad3-115">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="0bad3-115">By default, this message is a warning.</span></span> <span data-ttu-id="0bad3-116">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bad3-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0bad3-117">**エラー ID:** BC40042</span><span class="sxs-lookup"><span data-stu-id="0bad3-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0bad3-118">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0bad3-118">To correct this error</span></span>  
  
-   <span data-ttu-id="0bad3-119">省略可能なパラメーターは、この特定の型の既定値である必要があります、 <xref:System.CLSCompliantAttribute>。</xref:System.CLSCompliantAttribute>を削除します。</span><span class="sxs-lookup"><span data-stu-id="0bad3-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="0bad3-120">プロシージャは CLS 準拠になりません。</span><span class="sxs-lookup"><span data-stu-id="0bad3-120">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="0bad3-121">プロシージャを CLS 準拠にする必要がある場合は、この既定値の型を、最も近い CLS 準拠型に変更します。</span><span class="sxs-lookup"><span data-stu-id="0bad3-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="0bad3-122">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0bad3-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="0bad3-123">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0bad3-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="0bad3-124">オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0bad3-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="0bad3-125">たとえば、他の多くの環境では `int` は 16 ビットです。</span><span class="sxs-lookup"><span data-stu-id="0bad3-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="0bad3-126">このようなコンポーネントから 16 ビット整数を受け取る場合、マネージ [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コードでは、`Integer` ではなく `Short` を宣言してください。</span><span class="sxs-lookup"><span data-stu-id="0bad3-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bad3-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bad3-127">See Also</span></span>  
 [<span data-ttu-id="0bad3-128">\<経由で PAVE > CLS 準拠のコードの記述</span><span class="sxs-lookup"><span data-stu-id="0bad3-128">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
