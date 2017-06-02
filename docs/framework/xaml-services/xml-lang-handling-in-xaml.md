---
title: "xml:lang Handling in XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XAML [XAML Services], xml:lang attribute"
  - "xml:lang attribute [XAML Services]"
  - "RFC 3066 standard [XAML Services]"
  - "standards [XAML Services], RFC 3066"
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
caps.latest.revision: 16
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 15
---
# xml:lang Handling in XAML
`xml:lang` 属性は [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)] の定義済み属性の 1 つであり、XML の要素の言語およびカルチャ情報を宣言します。 属性の意味は XAML でも同じですが、いくつかの追加の考慮事項が適用されます。  
  
## XAML 属性の使用方法  
  
```  
<object xml:lang="rfc3066lang" />  
```  
  
## XAML 値  
  
|||  
|-|-|  
|*rfc3066lang*|[RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) 標準で定義されている文字列。1 つの言語、または言語と地域を表します。 後者の場合は、言語と地域が 1 つのハイフンで区切られます。 値と形式の詳細については、「<xref:System.Windows.Markup.XmlLanguage>」を参照してください。|  
  
## 解説  
 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] における `xml:lang` 属性の定義は、[!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] によって [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)] の "特別な属性" として定義された `xml:lang` から派生したものです。 言語およびカルチャ情報が要素によって処理される方法は、実装に応じて異なる可能性がありますが、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] における `xml:lang` 属性の既定の処理というものは存在しません。  
  
 `xml:lang` 属性の既定値は、属性レベルで空の文字列です。  
  
 `xml:lang` 属性の効果と属性の値が、`xml:lang` 値を処理するシステムによって解釈される場合、これらの効果と値は、通常、子要素に反映されます。  
  
 .NET Framework XAML サービスの XAML ライターによって解釈される場合、`xml:lang` 値によって、基になるオブジェクト表現に <xref:System.Windows.Markup.XmlLanguage> オブジェクトや <xref:System.Globalization.CultureInfo> オブジェクトが作成される可能性があります。ただし、この動作は、`xml:lang` に指定されている値が、それらのクラスを構築するための入力として有効であるかどうかに依存します。  
  
 フレームワークは、<xref:System.Windows.Markup.XmlLangPropertyAttribute> をプロパティに適用することによって、フレームワーク定義プロパティと XML 内の `xml:lang` の意味を関連付けることができます。  
  
## WPF の使用上の注意  
 要素が <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> の派生クラスの場合は、`xml:lang` 属性の代わりに、同等の <xref:System.Windows.FrameworkElement.Language%2A> 依存関係プロパティを使用できます。 別途設定されない限り、<xref:System.Windows.FrameworkElement.Language%2A> プロパティの値は既定で "en\-US" となります。このプロパティの値は、このプロパティを通して、または `xml:lang` 属性を処理することによって設定されます。  
  
## 参照  
 [WPF のグローバリゼーション](../../../ocs/framework/wpf/advanced/globalization-for-wpf.md)