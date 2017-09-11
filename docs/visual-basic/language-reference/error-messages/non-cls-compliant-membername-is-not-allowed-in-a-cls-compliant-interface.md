---
title: "非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
dev_langs:
- VB
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
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
ms.openlocfilehash: 27e83344c68d73c992d2395ab5d1bfcdb67520b0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="c24c1-102">非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません</span><span class="sxs-lookup"><span data-stu-id="c24c1-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="c24c1-103">プロパティ、プロシージャ、またはインターフェイスのイベントとしてマークされている`<CLSCompliant(True)>`インターフェイス自体としてマークされている場合`<CLSCompliant(False)>`またはマークされていません。</span><span class="sxs-lookup"><span data-stu-id="c24c1-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="c24c1-104">インターフェイスに対応して、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、すべてのメンバーは、対応である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c24c1-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="c24c1-105">適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c24c1-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="c24c1-106">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c24c1-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="c24c1-107">適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c24c1-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="c24c1-108">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="c24c1-108">By default, this message is a warning.</span></span> <span data-ttu-id="c24c1-109">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c24c1-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c24c1-110">**エラー ID:** BC40033</span><span class="sxs-lookup"><span data-stu-id="c24c1-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c24c1-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c24c1-111">To correct this error</span></span>  
  
-   <span data-ttu-id="c24c1-112">CLS 準拠をする必要があり、インターフェイスのソース コードに制御をマークされているインターフェイス`<CLSCompliant(True)>`すべてのメンバーに対応している場合。</span><span class="sxs-lookup"><span data-stu-id="c24c1-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="c24c1-113">CLS 準拠を必要となり、インターフェイスのソース コードを管理していない場合、または準拠しているが明確でない場合は、このメンバーを別のインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="c24c1-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="c24c1-114">このメンバーが、現在のインターフェイス内に残ることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>その定義からまたはとしてマークして`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c24c1-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c24c1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c24c1-115">See Also</span></span>  
 <span data-ttu-id="c24c1-116">[Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c24c1-116">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="c24c1-117"> [\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="c24c1-117"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
