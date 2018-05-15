---
title: 非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: ee533df5e06352034b24651b9173a88d090da0a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="9b81e-102">非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません</span><span class="sxs-lookup"><span data-stu-id="9b81e-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="9b81e-103">プロパティ、プロシージャ、またはインターフェイスでイベントとしてマークされている`<CLSCompliant(True)>`インターフェイス自体としてマークされている場合`<CLSCompliant(False)>`またはマークされていません。</span><span class="sxs-lookup"><span data-stu-id="9b81e-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="9b81e-104">インターフェイスに準拠する、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS) に、そのすべてのメンバーは、準拠である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b81e-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="9b81e-105">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。</span><span class="sxs-lookup"><span data-stu-id="9b81e-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="9b81e-106">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b81e-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="9b81e-107">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="9b81e-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="9b81e-108">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="9b81e-108">By default, this message is a warning.</span></span> <span data-ttu-id="9b81e-109">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b81e-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="9b81e-110">**エラー ID:** BC40033</span><span class="sxs-lookup"><span data-stu-id="9b81e-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9b81e-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9b81e-111">To correct this error</span></span>  
  
-   <span data-ttu-id="9b81e-112">CLS 準拠が必要 インターフェイスのソース コードを制御して、マークとしてインターフェイス`<CLSCompliant(True)>`すべてのメンバーに対応している場合。</span><span class="sxs-lookup"><span data-stu-id="9b81e-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="9b81e-113">CLS 準拠する必要があり、インターフェイスのソース コードに制御がない場合、または準拠しているが満たしていない場合は、このメンバーを別のインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="9b81e-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="9b81e-114">このメンバーが、現在インターフェイス内に残ることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>をその定義からとしてマークまたは`<CLSCompliant(False)>`です。</span><span class="sxs-lookup"><span data-stu-id="9b81e-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b81e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b81e-115">See Also</span></span>  
 [<span data-ttu-id="9b81e-116">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b81e-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
