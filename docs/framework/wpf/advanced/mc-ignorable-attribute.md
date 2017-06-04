---
title: "mc:Ignorable 属性 | Microsoft Docs"
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
  - "mc XML 名前空間プレフィックス"
  - "mc:Ignorable 属性"
  - "mc:ProcessContent 属性"
  - "XAML, mc:Ignorable 属性"
  - "XAML, mc:ProcessContent 属性"
  - "XML, mc 名前空間プレフィックス"
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# mc:Ignorable 属性
マークアップ ファイル内で検出された [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間プレフィックスのうち、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサで無視してよいものを指定します。  `mc:Ignorable` 属性はカスタム ネームスペースのマッピングと [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] バージョン管理のための互換性のあるマークアップをサポートします。  
  
## XAML 属性の使用方法 \(1 つのプレフィックス\)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## XAML 属性の使用方法 \(2 つのプレフィックス\)  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|**ignorablePrefix、ignorablePrefix1* など*|XML 1.0 仕様ごとの有効なプレフィックス文字列。|  
|**ignorableUri**|XML 1.0 仕様ごとに名前空間を指定する有効な URI。|  
|**ThisElementCanBeIgnored**|基になる型を解決できない場合に、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] プロセッサ実装により無視できる要素。|  
  
## 解説  
 この `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間プレフィックスは、互換性のある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の名前空間 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] を割り当てるときに使用する推奨プレフィックス規則です。  
  
 要素名のプレフィックス部分が `mc:Ignorable` として識別される要素または属性は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサで処理されるとき、エラーを発生しません。  その属性を基になる型またはプログラミング構成体に解決できない場合、その要素は無視されます。  ただし、無視された要素は、その未処理の影響である追加要素の要件に関して、追加の解析エラーを生成する可能性もあるので注意してください。  たとえば、特定の要素のコンテンツ モデルが 1 つだけの子要素を必要とするときに、指定された子要素が `mc:Ignorable` プレフィックスにあると型に解決できないので、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサはエラーを発生させる場合があります。  
  
 `mc:Ignorable` は、識別子文字列への名前空間の割り当てにのみ適用されます。  `mc:Ignorable` は、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 名前空間およびアセンブリ \(または、既定でアセンブリとして現在実行可能なファイル\) を指定する、アセンブリへの名前空間の割り当てには適用されません。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサを実装する場合、プロセッサの実装では、`mc:Ignorable` として識別されるプレフィックスが修飾する要素または属性の型解決について、解析エラーまたは処理エラーを発生させることはできません。  ただし、プロセッサの実装では例外が発生することもあり、この例外は、前述した 1 つの子要素の例のように、要素の読み込みまたは処理の失敗の 2 次的な結果です。  
  
 既定では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、無視された要素内のコンテンツを無視します。  ただし、追加属性、つまり [mc:ProcessContent 属性](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)を指定して、次に使用可能な親要素による無視された要素内のコンテンツの継続処理を要求できます。  
  
 複数のプレフィックスは、たとえば、`mc:Ignorable="ignore1 ignore2"` のように 1 つ以上の空白文字を区切り記号として使用して、属性内で指定できます。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] 名前空間は、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] のこの領域には記載されていないその他の要素や属性を定義します。  詳細については、「[XML マークアップの互換性の仕様](http://go.microsoft.com/fwlink/?LinkId=73824)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Markup.XamlReader>   
 [PresentationOptions:Freeze 属性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)