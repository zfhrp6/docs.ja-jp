---
title: "この &#39; の最初のステートメント新しいサブ &#39;明示的に呼び出す &#39; にする必要があります。指定されて &#39;または &#39;です。'Mybase.new' &#39;&#39;です。&lt;古い形式&gt;&#39;以外の場合は、基本クラス &#39; で&lt;baseclassname&gt;&#39; の &#39;&lt;derivedclassname&gt;&#39; 旧式とマークされて: &#39;&lt;errormessage&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords: BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8882acd947251d85804fbefd54267ce078e31b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="9929b-102">この &#39; の最初のステートメント新しいサブ &#39;明示的に呼び出す &#39; にする必要があります。指定されて &#39;または &#39;です。'Mybase.new' &#39;&#39;です。&lt;古い形式&gt;&#39;以外の場合は、基本クラス &#39; で&lt;baseclassname&gt;&#39; の &#39;&lt;derivedclassname&gt;&#39; 旧式とマークされて: &#39;&lt;errormessage&gt;&#39;です。</span><span class="sxs-lookup"><span data-stu-id="9929b-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="9929b-103">クラス コンストラクターが基底クラスのコンストラクターを明示的に呼び出さず、暗黙的な基底クラスのコンストラクターが <xref:System.ObsoleteAttribute> 属性およびエラーとして扱うことを示すディレクティブでマークされています。</span><span class="sxs-lookup"><span data-stu-id="9929b-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="9929b-104">派生クラスのコンストラクターが基底クラスのコンストラクターを呼び出さない場合、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では、パラメーターなしの基底クラスのコンストラクターの暗黙的な呼び出しを生成しようとします。</span><span class="sxs-lookup"><span data-stu-id="9929b-104">When a derived class constructor does not call a base class constructor, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="9929b-105">引数を指定せずに呼び出すことができるアクセス可能なコンストラクターが基底クラスにない場合、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では暗黙的な呼び出しを生成できません。</span><span class="sxs-lookup"><span data-stu-id="9929b-105">If there is no accessible constructor in the base class that can be called without arguments, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot generate an implicit call.</span></span> <span data-ttu-id="9929b-106">この場合、必要なコンストラクターが <xref:System.ObsoleteAttribute> 属性でマークされるため、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="9929b-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot call it.</span></span>  
  
 <span data-ttu-id="9929b-107"><xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="9929b-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="9929b-108">これを行う場合、この属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False`のどちらかに設定できます。</span><span class="sxs-lookup"><span data-stu-id="9929b-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="9929b-109">`True`に設定した場合、この要素を使用しようとすると、コンパイラはエラーとして処理します。</span><span class="sxs-lookup"><span data-stu-id="9929b-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="9929b-110">`False`に設定するか、または既定の `False`にする場合、この要素を使用しようとすると、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="9929b-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="9929b-111">**エラー ID:** BC30920</span><span class="sxs-lookup"><span data-stu-id="9929b-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9929b-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9929b-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="9929b-113">引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。</span><span class="sxs-lookup"><span data-stu-id="9929b-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="9929b-114">`MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。</span><span class="sxs-lookup"><span data-stu-id="9929b-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9929b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9929b-115">See Also</span></span>  
 [<span data-ttu-id="9929b-116">属性の概要</span><span class="sxs-lookup"><span data-stu-id="9929b-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
