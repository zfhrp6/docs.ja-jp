---
title: "&quot;&lt;elementname&gt;&quot; は古い (Visual Basic 警告) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
dev_langs:
- VB
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
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
ms.openlocfilehash: 77708f052f7aec7a5da2b24605ba3bd794f83979
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="97b4a-102">'&lt;elementname&gt;' は古い (Visual Basic 警告)</span><span class="sxs-lookup"><span data-stu-id="97b4a-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="97b4a-103">ステートメントでマークされているプログラミング要素にアクセスしようとしました、<xref:System.ObsoleteAttribute>属性と、警告として扱うディレクティブ。</xref:System.ObsoleteAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="97b4a-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="97b4a-104">使用中と不要になった<xref:System.ObsoleteAttribute>を</xref:System.ObsoleteAttribute>適用することで任意のプログラミング要素をマークすることができます。</span><span class="sxs-lookup"><span data-stu-id="97b4a-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="97b4a-105">これを行う場合は、属性を設定することができます<xref:System.ObsoleteAttribute.IsError%2A>プロパティを`True`または`False`</xref:System.ObsoleteAttribute.IsError%2A>。</span><span class="sxs-lookup"><span data-stu-id="97b4a-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="97b4a-106">`True`に設定した場合、コンパイラは、この要素を使用する試行をエラーとして処理します。</span><span class="sxs-lookup"><span data-stu-id="97b4a-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="97b4a-107">`False`に設定するか、または既定の `False`にする場合、この要素の使用が試行されると、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="97b4a-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="97b4a-108">既定では、このメッセージは警告であるため、<xref:System.ObsoleteAttribute.IsError%2A>の<xref:System.ObsoleteAttribute>は`False`</xref:System.ObsoleteAttribute></xref:System.ObsoleteAttribute.IsError%2A>。</span><span class="sxs-lookup"><span data-stu-id="97b4a-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="97b4a-109">警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="97b4a-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="97b4a-110">**エラー ID:** BC40008</span><span class="sxs-lookup"><span data-stu-id="97b4a-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97b4a-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="97b4a-111">To correct this error</span></span>  
  
-   <span data-ttu-id="97b4a-112">ソース コード参照の要素名のスペルが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="97b4a-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b4a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="97b4a-113">See Also</span></span>  
 [<span data-ttu-id="97b4a-114">属性の概要</span><span class="sxs-lookup"><span data-stu-id="97b4a-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

