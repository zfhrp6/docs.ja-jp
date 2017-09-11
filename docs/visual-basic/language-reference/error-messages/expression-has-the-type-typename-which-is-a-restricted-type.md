---
title: "式の型が &quot;&lt;typename&gt;&quot; は制限付きの型と &quot;Object&quot; または &quot;ValueType&quot; から継承されたメンバーにアクセスするために使用できない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
dev_langs:
- VB
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
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
ms.openlocfilehash: b89f7e83bf596c52296a090563d0dd0403ace548
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="8c724-102">式の型が '&lt;typename&gt;' は制限付きの型と 'Object' または 'ValueType' から継承したメンバーのアクセスに使用することはできません</span><span class="sxs-lookup"><span data-stu-id="8c724-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="8c724-103">式では、共通言語ランタイム (CLR) でボックス化できない型に評価が、ボックス化を必要とするメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8c724-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="8c724-104">*ボックス化*を型に変換するために必要な処理を指します`Object`または<xref:System.ValueType>.</xref:System.ValueType>に場合によっては、</span><span class="sxs-lookup"><span data-stu-id="8c724-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="8c724-105">共通言語ランタイムでは、特定の構造体の型を次に例をボックスことはできません<xref:System.ArgIterator>、 <xref:System.RuntimeArgumentHandle>、 <xref:System.TypedReference>.</xref:System.TypedReference> </xref:System.RuntimeArgumentHandle> </xref:System.ArgIterator></span><span class="sxs-lookup"><span data-stu-id="8c724-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="8c724-106">この式が制限付きの型を使用して、継承されたメソッドを呼び出すしよう<xref:System.Object>または<xref:System.ValueType>、<xref:System.Object.GetHashCode%2A>または<xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A></xref:System.Object.GetHashCode%2A>など</xref:System.ValueType></xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="8c724-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="8c724-107">このメソッドにアクセスする[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]このエラーが発生する暗黙的なボックス化変換しようとしました。</span><span class="sxs-lookup"><span data-stu-id="8c724-107">To access this method, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="8c724-108">**エラー ID:** BC31393</span><span class="sxs-lookup"><span data-stu-id="8c724-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c724-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8c724-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="8c724-110">問題の型に評価される式を探します。</span><span class="sxs-lookup"><span data-stu-id="8c724-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="8c724-111"><xref:System.Object>または<xref:System.ValueType>.</xref:System.ValueType></xref:System.Object>から継承されたメソッドを呼び出そうとすると、ステートメントの一部を検索します。</span><span class="sxs-lookup"><span data-stu-id="8c724-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="8c724-112">メソッドの呼び出しを回避するステートメントを書き直してください。</span><span class="sxs-lookup"><span data-stu-id="8c724-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c724-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c724-113">See Also</span></span>  
 [<span data-ttu-id="8c724-114">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="8c724-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
