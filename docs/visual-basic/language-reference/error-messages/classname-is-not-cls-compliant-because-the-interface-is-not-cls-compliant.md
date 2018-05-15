---
title: '&#39;&lt;classname&gt; &#39;ためには CLS 準拠インターフェイス&#39; &lt;interfacename&gt; &#39; 、implements は CLS 準拠ではありません'
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 4dda0e16a94f43cdb3deeff16fabdd1b10b62526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="1f291-102">&#39;&lt;classname&gt; &#39;ためには CLS 準拠インターフェイス&#39; &lt;interfacename&gt; &#39; 、implements は CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="1f291-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="1f291-103">クラスまたはインターフェイスが `<CLSCompliant(True)>` としてマークされていますが、これらの派生元の型、またはこれらが実装している型が `<CLSCompliant(False)>` としてマークされているか、マークされていません。</span><span class="sxs-lookup"><span data-stu-id="1f291-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="1f291-104">クラスまたはインターフェイスに準拠する、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS) に、継承階層全体は準拠である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f291-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="1f291-105">つまり、直接的または間接的に継承する型をすべて CLS に準拠させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f291-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="1f291-106">同様に、クラスが 1 つ以上のインターフェイスを実装する場合は、そのすべてのインターフェイスの継承階層全体を CLS 準拠にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f291-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="1f291-107">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。</span><span class="sxs-lookup"><span data-stu-id="1f291-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="1f291-108">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f291-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="1f291-109">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="1f291-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="1f291-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="1f291-110">By default, this message is a warning.</span></span> <span data-ttu-id="1f291-111">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f291-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1f291-112">**エラー ID:** BC40029</span><span class="sxs-lookup"><span data-stu-id="1f291-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1f291-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1f291-113">To correct this error</span></span>  
  
-   <span data-ttu-id="1f291-114">CLS 準拠にする必要がある場合は、この型を別の継承階層または実装スキームの中で定義します。</span><span class="sxs-lookup"><span data-stu-id="1f291-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="1f291-115">この型を現在の継承階層または実装スキームに残しておく必要がある場合は、 <xref:System.CLSCompliantAttribute> を定義から削除するか、 `<CLSCompliant(False)>`としてマークします。</span><span class="sxs-lookup"><span data-stu-id="1f291-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
 
