---
title: "{} エスケープ シーケンスのマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: "21"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: befbf9960afffcd30bc96863dcc00b4acad2c21a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="85a1f-102">{} エスケープ シーケンス/マークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="85a1f-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="85a1f-103">属性値を XAML エスケープ シーケンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="85a1f-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="85a1f-104">エスケープ シーケンスは、リテラルとして解釈する属性内の後続の値を許可します。</span><span class="sxs-lookup"><span data-stu-id="85a1f-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="85a1f-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="85a1f-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="85a1f-106">XAML プロパティ要素の使用</span><span class="sxs-lookup"><span data-stu-id="85a1f-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="85a1f-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="85a1f-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85a1f-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="85a1f-108">*literalValue*</span></span>|<span data-ttu-id="85a1f-109">エスケープ シーケンスに続くリテラル文字列。</span><span class="sxs-lookup"><span data-stu-id="85a1f-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="85a1f-110">通常この文字列が、開くまたは閉じる中かっこ ({または})。</span><span class="sxs-lookup"><span data-stu-id="85a1f-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85a1f-111">コメント</span><span class="sxs-lookup"><span data-stu-id="85a1f-111">Remarks</span></span>  
 <span data-ttu-id="85a1f-112">始め中かっこ ({}) は、XAML でのリテラル文字として使用できるようにする、エスケープ シーケンス ({}) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="85a1f-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="85a1f-113">右中かっこ (}) があるかどうかを判断するには、次の文字をチェックするただし、XAML リーダーは通常、マークアップ拡張機能のエントリ ポイントを表すために始め中かっこ ({}) を使用します。</span><span class="sxs-lookup"><span data-stu-id="85a1f-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="85a1f-114">2 つの中かっこ ({}) は、隣接するが、場合にのみと見なされます、エスケープ シーケンス。</span><span class="sxs-lookup"><span data-stu-id="85a1f-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="85a1f-115">エスケープ シーケンスが発生した場合、XAML リーダーは文字列として残りの文字列を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85a1f-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="85a1f-116">ただし、エスケープ シーケンスを実行する型コンバーターを持つメンバーに適用されている場合、文字列を行うことも型変換と XAML ライターによって解釈されます。</span><span class="sxs-lookup"><span data-stu-id="85a1f-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="85a1f-117">エスケープ シーケンスは、マークアップ拡張機能ではなく、クラスではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="85a1f-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="85a1f-118">ただし、これは、XAML リーダー (カスタム XAML リーダーを含む) が遵守する必要があります規則です。</span><span class="sxs-lookup"><span data-stu-id="85a1f-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="85a1f-119">引用符 (") は、この方法でエスケープ シーケンスとして使用できません。</span><span class="sxs-lookup"><span data-stu-id="85a1f-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="85a1f-120">非プロパティのプロパティの値として、引用符を設定する必要がある場合は、プロパティ要素構文を使用またはプロパティ要素内の文字列として引用符を配置し XML 文字エンティティを使用します。</span><span class="sxs-lookup"><span data-stu-id="85a1f-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="85a1f-121">コンテンツのプロパティの引用符は、コンテンツ全体を指定できます。</span><span class="sxs-lookup"><span data-stu-id="85a1f-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="85a1f-122">エスケープ シーケンス ({}) は、XAML マークアップ拡張機能が表示される場所に名前空間の修飾子を含める必要のある XML 型を指定するときに頻繁に必要です。</span><span class="sxs-lookup"><span data-stu-id="85a1f-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="85a1f-123">これには、等号 (=) の直後に、マークアップ拡張機能と、XAML 属性の値の開始が含まれます。</span><span class="sxs-lookup"><span data-stu-id="85a1f-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="85a1f-124">次の例では、XAML 属性の値の先頭に表示される XML 名前空間のエスケープ シーケンスを示します。</span><span class="sxs-lookup"><span data-stu-id="85a1f-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="85a1f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="85a1f-125">See Also</span></span>  
 [<span data-ttu-id="85a1f-126">XAML の型コンバーターおよびマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="85a1f-126">Type Converters and Markup Extensions for XAML</span></span>](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [<span data-ttu-id="85a1f-127">XML 文字エンティティと XAML</span><span class="sxs-lookup"><span data-stu-id="85a1f-127">XML Character Entities and XAML</span></span>](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
