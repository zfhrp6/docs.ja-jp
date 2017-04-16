---
title: "ColorConvertedBitmap のマークアップ拡張機能 | Microsoft Docs"
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
  - "ColorConvertedBitmap マークアップ拡張機能"
  - "XAML, ColorConvertedBitmap マークアップ拡張機能"
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# ColorConvertedBitmap のマークアップ拡張機能
埋め込まれたプロファイルのないビットマップ ソースを指定する方法を提供します。  カラー コンテキスト\/プロファイルは、イメージ リソース [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] と同じように [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] で指定されます。  
  
## XAML 属性の使用方法  
  
```  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`imageSource`|プロファイルになっていないビットマップの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。|  
|`sourceIIC`|ソース プロファイル構成の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。|  
|`destinationIIC`|変換先プロファイル構成の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。|  
  
## 解説  
 このマークアップ拡張機能は、<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A> などの関連するイメージ ソース プロパティ値のセットを塗りつぶすためのものです。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。  `ColorConvertedBitmap` \(または `ColorConvertedBitmapExtension`\) は、プロパティ要素構文では使用できません。これは、値は初期コンストラクターの値としてのみ設定でき、拡張機能の識別子に従う文字列であるためです。  
  
 `ColorConvertedBitmap` はマークアップ拡張機能です。  一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のすべてのマークアップ拡張機能では、それぞれの属性構文で { と } の 2 つの記号を使用します。これは規約であり、これに従って [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、マークアップ拡張機能で属性を処理する必要があることを認識します。  詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)