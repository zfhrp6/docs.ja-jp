---
title: "名前&lt;membername&gt; CLS 準拠ではありません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
dev_langs:
- VB
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
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
ms.openlocfilehash: cbe0a8db6d801a0d083a6828af75342f15f0178d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="0a8d2-102">名前&lt;membername&gt; CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="0a8d2-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="0a8d2-103">アセンブリとしてマークされている`<CLSCompliant(True)>`晒すことにアンダー スコアで始まる名前を持つメンバー (`_`)。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="0a8d2-104">プログラミング要素に準拠しているが、1 つまたは複数アンダー スコアを含めることができます、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) に始めることはできません、アンダー スコアでします。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="0a8d2-105">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="0a8d2-106">適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0a8d2-107">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="0a8d2-108">適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="0a8d2-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-109">By default, this message is a warning.</span></span> <span data-ttu-id="0a8d2-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0a8d2-111">**エラー ID:** BC40031</span><span class="sxs-lookup"><span data-stu-id="0a8d2-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a8d2-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0a8d2-112">To correct this error</span></span>  
  
-   <span data-ttu-id="0a8d2-113">ソース コードに制御がある場合は、メンバーの名前を変更して、アンダー スコアで始まらないようにします。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="0a8d2-114">メンバーの名前は変更しないことが必要な場合は、削除、<xref:System.CLSCompliantAttribute>その定義から、またはマークとしてして`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="0a8d2-115">アセンブリをマークすることも`<CLSCompliant(True)>`です。</span><span class="sxs-lookup"><span data-stu-id="0a8d2-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8d2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a8d2-116">See Also</span></span>  
 <span data-ttu-id="0a8d2-117">[宣言された要素名](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="0a8d2-117">[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="0a8d2-118"> [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="0a8d2-118"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="0a8d2-119"> [\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="0a8d2-119"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
