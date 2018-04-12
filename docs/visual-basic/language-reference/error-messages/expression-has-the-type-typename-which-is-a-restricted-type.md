---
title: '式の種類 &#39; 値が&lt;typename&gt;(& a) あり、制限付きの型から継承されたメンバー &#39; オブジェクト &#39; のアクセスに使用することはできません。 #39 または &#39;です。ValueType &#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30742bd46ccd1a3e5a688ebd2621e2c8a3d50e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="4353b-102">式の種類 &#39; 値が&lt;typename&gt;(& a) あり、制限付きの型から継承されたメンバー &#39; オブジェクト &#39; のアクセスに使用することはできません。 #39 または &#39;です。ValueType &#39;</span><span class="sxs-lookup"><span data-stu-id="4353b-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="4353b-103">式は、共通言語ランタイム (CLR) でボックス化できない型に評価が、ボックス化を必要とするメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4353b-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="4353b-104">*ボックス化* とは、型を `Object` (場合によっては <xref:System.ValueType>) に変換するために不可欠な処理です。</span><span class="sxs-lookup"><span data-stu-id="4353b-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="4353b-105">共通言語ランタイムでは、特定の構造体の型をたとえばボックスことはできません<xref:System.ArgIterator>、 <xref:System.RuntimeArgumentHandle>、および<xref:System.TypedReference>です。</span><span class="sxs-lookup"><span data-stu-id="4353b-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="4353b-106">この式から継承されたメソッドの呼び出しに制限付きの型を使用しようとしました。<xref:System.Object>または<xref:System.ValueType>、など<xref:System.Object.GetHashCode%2A>または<xref:System.Object.ToString%2A>です。</span><span class="sxs-lookup"><span data-stu-id="4353b-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="4353b-107">このメソッドにアクセスする[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]がこのエラーが発生する暗黙的なボックス化変換を試行します。</span><span class="sxs-lookup"><span data-stu-id="4353b-107">To access this method, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="4353b-108">**エラー ID:** BC31393</span><span class="sxs-lookup"><span data-stu-id="4353b-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4353b-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4353b-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="4353b-110">問題の型に評価される式を探します。</span><span class="sxs-lookup"><span data-stu-id="4353b-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="4353b-111">継承されたメソッドを呼び出そうとすると、ステートメントの一部を検索<xref:System.Object>または<xref:System.ValueType>です。</span><span class="sxs-lookup"><span data-stu-id="4353b-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="4353b-112">メソッドの呼び出しを避けるために、ステートメントを書き直してください。</span><span class="sxs-lookup"><span data-stu-id="4353b-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4353b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4353b-113">See Also</span></span>  
 [<span data-ttu-id="4353b-114">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="4353b-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
