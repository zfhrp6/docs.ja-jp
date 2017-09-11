---
title: "名前&lt;namespacename&gt;ルート名前空間に&lt;fullnamespacename&gt; CLS 準拠ではありません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
dev_langs:
- VB
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: 10
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
ms.openlocfilehash: 0d31657a958581b91cb448b78b8f55f8aadfe7c9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="0b75b-102">名前&lt;namespacename&gt;ルート名前空間に&lt;fullnamespacename&gt; CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="0b75b-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="0b75b-103">アセンブリとしてマークされている`<CLSCompliant(True)>`、ルート名前空間の名前の要素がアンダー スコアで始まりますが、(`_`)。</span><span class="sxs-lookup"><span data-stu-id="0b75b-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="0b75b-104">プログラミング要素に準拠しているが、1 つまたは複数アンダー スコアを含めることができます、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) に始めることはできません、アンダー スコアでします。</span><span class="sxs-lookup"><span data-stu-id="0b75b-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="0b75b-105">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="0b75b-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="0b75b-106">適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0b75b-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0b75b-107">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0b75b-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="0b75b-108">適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0b75b-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="0b75b-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="0b75b-109">By default, this message is a warning.</span></span> <span data-ttu-id="0b75b-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b75b-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0b75b-111">**エラー ID:** BC40039</span><span class="sxs-lookup"><span data-stu-id="0b75b-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0b75b-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0b75b-112">To correct this error</span></span>  
  
-   <span data-ttu-id="0b75b-113">CLS 準拠を必要とする場合は、アンダー スコアでその要素のいずれもが開始されるようにルート名前空間の名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="0b75b-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="0b75b-114">名前空間の名前は変更しないことが必要な場合は、削除、<xref:System.CLSCompliantAttribute>アセンブリから、またはマークしてとして`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0b75b-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b75b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b75b-115">See Also</span></span>  
 <span data-ttu-id="0b75b-116">[Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0b75b-116">[Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="0b75b-117"> [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="0b75b-117"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="0b75b-118"> [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md) </span><span class="sxs-lookup"><span data-stu-id="0b75b-118"> [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md) </span></span>  
<span data-ttu-id="0b75b-119"> [[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="0b75b-119"> [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="0b75b-120"> [宣言された要素名](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="0b75b-120"> [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="0b75b-121"> [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="0b75b-121"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="0b75b-122"> [\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="0b75b-122"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
