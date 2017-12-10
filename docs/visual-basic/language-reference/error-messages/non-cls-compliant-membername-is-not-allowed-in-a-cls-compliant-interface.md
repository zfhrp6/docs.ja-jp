---
title: "非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords: BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2811958df5bd0b023a2ce3b02abf85b5a23c58f6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="41ee6-102">非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません</span><span class="sxs-lookup"><span data-stu-id="41ee6-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="41ee6-103">プロパティ、プロシージャ、またはインターフェイスでイベントとしてマークされている`<CLSCompliant(True)>`インターフェイス自体としてマークされている場合`<CLSCompliant(False)>`またはマークされていません。</span><span class="sxs-lookup"><span data-stu-id="41ee6-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="41ee6-104">インターフェイスに準拠する、[言語非依存および言語非依存コンポーネント](../../../../docs/standard/language-independence-and-language-independent-components.md)(CLS) に、そのすべてのメンバーは、準拠である必要があります。</span><span class="sxs-lookup"><span data-stu-id="41ee6-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="41ee6-105">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。</span><span class="sxs-lookup"><span data-stu-id="41ee6-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="41ee6-106">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41ee6-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="41ee6-107">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="41ee6-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="41ee6-108">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="41ee6-108">By default, this message is a warning.</span></span> <span data-ttu-id="41ee6-109">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41ee6-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="41ee6-110">**エラー ID:** BC40033</span><span class="sxs-lookup"><span data-stu-id="41ee6-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41ee6-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="41ee6-111">To correct this error</span></span>  
  
-   <span data-ttu-id="41ee6-112">CLS 準拠が必要 インターフェイスのソース コードを制御して、マークとしてインターフェイス`<CLSCompliant(True)>`すべてのメンバーに対応している場合。</span><span class="sxs-lookup"><span data-stu-id="41ee6-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="41ee6-113">CLS 準拠する必要があり、インターフェイスのソース コードに制御がない場合、または準拠しているが満たしていない場合は、このメンバーを別のインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="41ee6-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="41ee6-114">このメンバーが、現在インターフェイス内に残ることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>をその定義からとしてマークまたは`<CLSCompliant(False)>`です。</span><span class="sxs-lookup"><span data-stu-id="41ee6-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ee6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="41ee6-115">See Also</span></span>  
 [<span data-ttu-id="41ee6-116">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="41ee6-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="41ee6-117">\<経由で PAVE > CLS 準拠コードの記述</span><span class="sxs-lookup"><span data-stu-id="41ee6-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
