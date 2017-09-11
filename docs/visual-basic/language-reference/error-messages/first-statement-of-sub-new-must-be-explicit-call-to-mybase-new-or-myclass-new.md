---
title: "この &quot;Sub New&quot; の最初のステートメントは &quot;MyBase.New&quot; &quot;mybase.new&quot; または &quot;myclass.new&quot; への明示的な呼び出しをする必要がありますので、&quot;&lt;constructorname&gt;&quot;の基本クラス&quot;&lt;baseclassname&gt;&quot;の&quot;&lt;derivedclassname&gt;&quot; 不使用とマークされた: &quot;&lt;errormessage&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
dev_langs:
- VB
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
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
ms.openlocfilehash: d46192bc9a9f2807f56cbdd7bdd4fd21f6c9a7b0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="17cc9-102">この 'Sub New' の最初のステートメントは 'MyBase.New' 'mybase.new' または 'myclass.new' への明示的な呼び出しをする必要がありますので、'&lt;constructorname&gt;'の基本クラス'&lt;baseclassname&gt;'の'&lt;derivedclassname&gt;' 不使用とマークされた: '&lt;errormessage&gt;'</span><span class="sxs-lookup"><span data-stu-id="17cc9-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="17cc9-103">クラスのコンス トラクターが基本クラスのコンス トラクターを明示的に呼び出していないと、暗黙の型の基本クラス コンス トラクターが付いて、<xref:System.ObsoleteAttribute>属性と、エラーとして扱うディレクティブ</xref:System.ObsoleteAttribute>。</span><span class="sxs-lookup"><span data-stu-id="17cc9-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="17cc9-104">派生クラスのコンス トラクターは、基本クラスのコンス トラクターを呼び出していない[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]パラメーターなしの基本クラス コンス トラクターへの暗黙の呼び出しを生成しようとします。</span><span class="sxs-lookup"><span data-stu-id="17cc9-104">When a derived class constructor does not call a base class constructor, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="17cc9-105">引数を指定せずに呼び出すことができる基本クラスでアクセス可能なコンス トラクターがない場合[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]暗黙の呼び出しを生成することはできません。</span><span class="sxs-lookup"><span data-stu-id="17cc9-105">If there is no accessible constructor in the base class that can be called without arguments, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot generate an implicit call.</span></span> <span data-ttu-id="17cc9-106">この場合、必要なコンス トラクターがでマークされた、<xref:System.ObsoleteAttribute>ため属性[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]それを呼び出すことはできません</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="17cc9-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot call it.</span></span>  
  
 <span data-ttu-id="17cc9-107">使用中と不要になった<xref:System.ObsoleteAttribute>を</xref:System.ObsoleteAttribute>適用することで任意のプログラミング要素をマークすることができます。</span><span class="sxs-lookup"><span data-stu-id="17cc9-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="17cc9-108">これを行う場合は、属性を設定することができます<xref:System.ObsoleteAttribute.IsError%2A>プロパティを`True`または`False`</xref:System.ObsoleteAttribute.IsError%2A>。</span><span class="sxs-lookup"><span data-stu-id="17cc9-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="17cc9-109">`True`に設定した場合、コンパイラは、この要素を使用する試行をエラーとして処理します。</span><span class="sxs-lookup"><span data-stu-id="17cc9-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="17cc9-110">`False`に設定するか、または既定の `False`にする場合、この要素の使用が試行されると、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="17cc9-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="17cc9-111">**エラー ID:** BC30920</span><span class="sxs-lookup"><span data-stu-id="17cc9-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="17cc9-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="17cc9-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="17cc9-113">引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。</span><span class="sxs-lookup"><span data-stu-id="17cc9-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="17cc9-114">`MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。</span><span class="sxs-lookup"><span data-stu-id="17cc9-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cc9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="17cc9-115">See Also</span></span>  
 [<span data-ttu-id="17cc9-116">属性の概要</span><span class="sxs-lookup"><span data-stu-id="17cc9-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
