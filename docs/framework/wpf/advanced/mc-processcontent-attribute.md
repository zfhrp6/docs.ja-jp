---
title: "mc:ProcessContent 属性 | Microsoft Docs"
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
  - "mc:ProcessContent 属性"
  - "XAML, mc:ProcessContent 属性"
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# mc:ProcessContent 属性
[mc:Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)の指定によって直接の親要素が [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサで無視された場合でも、関連する親要素によってコンテンツを処理する [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 要素を指定します。  `mc:ProcessContent` 属性はカスタム ネームスペースのマッピングと [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] バージョン管理のための互換性のあるマークアップをサポートします。  
  
## XAML 属性の使用方法  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|**ignorablePrefix**|XML 1.0 仕様ごとの有効なプレフィックス文字列。|  
|**ignorableUri**|XML 1.0 仕様ごとに名前空間を指定する有効な URI。|  
|**ThisElementCanBeIgnored**|基になる型を解決できない場合に、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] プロセッサ実装により無視できる要素。|  
|**\[content\]**|*ThisElementCanBeIgnored* は、無視可能とマークされます。  プロセッサがその要素を無視した場合、*\[content\]* は *object* によって処理されます。|  
  
## 解説  
 既定では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、無視された要素内のコンテンツを無視します。  `mc:ProcessContent` によって特定の要素を指定することにより、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサで無視された要素内のコンテンツを引き続き処理することができます。  これは通常、コンテンツが複数のタグ内で入れ子になっており、無視できるものと無視できないものがそれぞれ少なくとも 1 つある場合に使用されます。  
  
 属性内では、`mc:ProcessContent="ignore:Element1 ignore:Element2"` のようにスペースで区切ることによって複数のプレフィックスを指定できます。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] 名前空間は、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] のこの領域には記載されていないその他の要素や属性を定義します。  詳細については、「[XML マークアップの互換性の仕様](http://go.microsoft.com/fwlink/?LinkId=73824)」を参照してください。  
  
## 参照  
 [mc:Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)