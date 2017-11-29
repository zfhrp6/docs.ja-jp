---
title: "XAML における xml:space の処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a5048cbad1d2ea914d041ac3c87a43223b208c3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="6ff06-102">XAML における xml:space の処理</span><span class="sxs-lookup"><span data-stu-id="6ff06-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="6ff06-103">`xml:space`属性はオブジェクト要素内で重要な空白の処理の動作を宣言する XML 定義の属性です。</span><span class="sxs-lookup"><span data-stu-id="6ff06-103">The `xml:space` attribute is an XML-defined attribute that declares the significant whitespace processing behavior within an object element.</span></span> <span data-ttu-id="6ff06-104">この動作は、要素内に含まれるすべてのコンテンツ (内部テキ スト) に関連する場所`xml:space`が宣言されているし、もスコープの子要素にします。</span><span class="sxs-lookup"><span data-stu-id="6ff06-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="6ff06-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="6ff06-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="6ff06-106">\- または</span><span class="sxs-lookup"><span data-stu-id="6ff06-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="6ff06-107">コメント</span><span class="sxs-lookup"><span data-stu-id="6ff06-107">Remarks</span></span>  
 <span data-ttu-id="6ff06-108">定義、`xml:space`からその 2 つの値を含む XAML の属性が派生した`xml:space`for XML の W3C 仕様で「特別な属性」として定義されています。</span><span class="sxs-lookup"><span data-stu-id="6ff06-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="6ff06-109">既定値、`xml:space`属性は、リテラル値`"default"`です。</span><span class="sxs-lookup"><span data-stu-id="6ff06-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="6ff06-110">値の`"default"`、または`xml:space`が反映されていません、すべてのトピックで定義されているの重要なホワイト スペースの解析中の動作は、既定の処理[XAML での空白の処理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ff06-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant whitespace parsing is the default handling, as defined in the topic [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="6ff06-111">オブジェクトの要素コンテンツ内の空白を保持するために指定`xml:space="preserve"`に、そのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6ff06-111">To preserve whitespace within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="6ff06-112">ほとんどの解釈、`xml:space`のスコープの子要素には属性の効果と属性の値。</span><span class="sxs-lookup"><span data-stu-id="6ff06-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="6ff06-113">空白の XAML の処理の詳細については、次を参照してください。 [XAML での空白の処理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ff06-113">For a complete discussion of whitespace processing in XAML, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff06-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ff06-114">See Also</span></span>  
 [<span data-ttu-id="6ff06-115">XAML での空白の処理</span><span class="sxs-lookup"><span data-stu-id="6ff06-115">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [<span data-ttu-id="6ff06-116">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="6ff06-116">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
