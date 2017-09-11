---
title: "&quot;&lt;classname&gt;&quot; ため CLS 準拠ではありません、インターフェイス &quot;&lt;interfacename&gt;&quot; その実装は CLS 準拠ではありません |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
dev_langs:
- VB
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
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
ms.openlocfilehash: d2819bf2dc76291cbaf7ca9215608a11b1a98b3a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="6d14d-102">'&lt;classname&gt;' ため CLS 準拠ではありません、インターフェイス '&lt;interfacename&gt;' その実装は CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="6d14d-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="6d14d-103">クラスまたはインターフェイスが `<CLSCompliant(True)>` としてマークされていますが、これらの派生元の型、またはこれらが実装している型が `<CLSCompliant(False)>` としてマークされているか、マークされていません。</span><span class="sxs-lookup"><span data-stu-id="6d14d-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="6d14d-104">クラスまたはインターフェイスに対応して、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、その全体の継承階層を対応にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d14d-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="6d14d-105">つまり、直接的または間接的に継承する型をすべて CLS に準拠させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d14d-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="6d14d-106">同様に、クラスが&1; つ以上のインターフェイスを実装する場合は、そのすべてのインターフェイスの継承階層全体を CLS 準拠にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d14d-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="6d14d-107">適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6d14d-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="6d14d-108">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d14d-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="6d14d-109">適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6d14d-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="6d14d-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="6d14d-110">By default, this message is a warning.</span></span> <span data-ttu-id="6d14d-111">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d14d-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6d14d-112">**エラー ID:** BC40029</span><span class="sxs-lookup"><span data-stu-id="6d14d-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6d14d-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6d14d-113">To correct this error</span></span>  
  
-   <span data-ttu-id="6d14d-114">CLS 準拠にする必要がある場合は、この型を別の継承階層または実装スキームの中で定義します。</span><span class="sxs-lookup"><span data-stu-id="6d14d-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="6d14d-115">この型が現在その継承階層または実装スキーム内に残ることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>その定義からまたはとしてマークして`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6d14d-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d14d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d14d-116">See Also</span></span>  
 [<span data-ttu-id="6d14d-117">\<経由で PAVE > CLS 準拠のコードの記述</span><span class="sxs-lookup"><span data-stu-id="6d14d-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
