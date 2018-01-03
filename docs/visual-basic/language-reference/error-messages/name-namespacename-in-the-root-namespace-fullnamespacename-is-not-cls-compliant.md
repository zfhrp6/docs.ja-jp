---
title: "名前&lt;namespacename&gt;ルート名前空間に&lt;fullnamespacename&gt; CLS 準拠ではありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a89f8cfe4038a81002777886de1155bea72ba22
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="ab50a-102">名前&lt;namespacename&gt;ルート名前空間に&lt;fullnamespacename&gt; CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="ab50a-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="ab50a-103">アセンブリとしてマークされている`<CLSCompliant(True)>`、ルート名前空間の名前の要素がアンダー スコアで始まるが (`_`)。</span><span class="sxs-lookup"><span data-stu-id="ab50a-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="ab50a-104">プログラミング要素に準拠するためには、1 つまたは複数アンダー スコアを含めることができます、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS) に始めることはできません、アンダー スコアを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab50a-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="ab50a-105">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab50a-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="ab50a-106">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。</span><span class="sxs-lookup"><span data-stu-id="ab50a-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="ab50a-107">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab50a-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="ab50a-108">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="ab50a-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="ab50a-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="ab50a-109">By default, this message is a warning.</span></span> <span data-ttu-id="ab50a-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab50a-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ab50a-111">**エラー ID:** BC40039</span><span class="sxs-lookup"><span data-stu-id="ab50a-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab50a-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ab50a-112">To correct this error</span></span>  
  
-   <span data-ttu-id="ab50a-113">CLS 準拠を必要とする場合は、ルート名前空間の名前を変更してから、その要素のいずれもがアンダー スコアで始まるようにします。</span><span class="sxs-lookup"><span data-stu-id="ab50a-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="ab50a-114">名前空間の名前は変更されていないことを必要とする場合、削除、<xref:System.CLSCompliantAttribute>アセンブリからとしてマークまたは`<CLSCompliant(False)>`です。</span><span class="sxs-lookup"><span data-stu-id="ab50a-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab50a-115">参照</span><span class="sxs-lookup"><span data-stu-id="ab50a-115">See Also</span></span>  
 [<span data-ttu-id="ab50a-116">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="ab50a-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="ab50a-117">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="ab50a-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="ab50a-118">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="ab50a-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 <span data-ttu-id="ab50a-119">[[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="ab50a-119">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span></span>  
 [<span data-ttu-id="ab50a-120">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="ab50a-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="ab50a-121">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="ab50a-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 
