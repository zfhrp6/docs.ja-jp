---
title: "関数 &#39; の型を返す&lt;procedurename&gt;&#39; CLS 準拠ではありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords: BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16670521ec09ae9cab28bf6ca4705c131fd84701
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="92e70-102">関数 &#39; の型を返す&lt;procedurename&gt;&#39; CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="92e70-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="92e70-103">A`Function`プロシージャ マークが付いている`<CLSCompliant(True)>`としてマークされている型を返しますが、 `<CLSCompliant(False)>`、マークされていないか修飾されていません、非準拠の型になっているためです。</span><span class="sxs-lookup"><span data-stu-id="92e70-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="92e70-104">プロシージャを[言語への非依存性および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3) (CLS) に準拠させるには、CLS 準拠型のみを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92e70-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="92e70-105">これは、パラメーターの型、戻り値の型、およびすべてのローカル変数の型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="92e70-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="92e70-106">次の [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="92e70-106">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="92e70-107">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="92e70-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="92e70-108">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="92e70-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="92e70-109">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="92e70-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="92e70-110">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="92e70-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="92e70-111">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。</span><span class="sxs-lookup"><span data-stu-id="92e70-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="92e70-112">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92e70-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="92e70-113">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="92e70-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="92e70-114">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="92e70-114">By default, this message is a warning.</span></span> <span data-ttu-id="92e70-115">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92e70-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="92e70-116">**エラー ID:** BC40027</span><span class="sxs-lookup"><span data-stu-id="92e70-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="92e70-117">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="92e70-117">To correct this error</span></span>  
  
-   <span data-ttu-id="92e70-118">場合、`Function`プロシージャがこの特定の型を返す必要があります、削除、<xref:System.CLSCompliantAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="92e70-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="92e70-119">プロシージャは CLS 準拠になりません。</span><span class="sxs-lookup"><span data-stu-id="92e70-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="92e70-120">場合、`Function`プロシージャが CLS に準拠する、最も近い CLS に準拠した型の戻り値の型を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92e70-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="92e70-121">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="92e70-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="92e70-122">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="92e70-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="92e70-123">オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="92e70-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="92e70-124">たとえば、他の多くの環境では `int` は 16 ビットです。</span><span class="sxs-lookup"><span data-stu-id="92e70-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="92e70-125">このようなコンポーネントに 16 ビット整数を返す場合として宣言`Short`の代わりに`Integer`、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コード。</span><span class="sxs-lookup"><span data-stu-id="92e70-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e70-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="92e70-126">See Also</span></span>  
 [<span data-ttu-id="92e70-127">\<経由で PAVE > CLS 準拠コードの記述</span><span class="sxs-lookup"><span data-stu-id="92e70-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
