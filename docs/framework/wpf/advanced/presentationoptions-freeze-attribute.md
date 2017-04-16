---
title: "PresentationOptions:Freeze 属性 | Microsoft Docs"
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
  - "Freezable 要素"
  - "Freeze 属性"
  - "PresentationOptions プレフィックス"
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# PresentationOptions:Freeze 属性
含まれている <xref:System.Windows.Freezable> 要素に対して <xref:System.Windows.Freezable.IsFrozen%2A> 状態を `true` に設定します。  `PresentationOptions:Freeze` 属性を指定していない状態での <xref:System.Windows.Freezable> の既定の動作は、読み込み時には <xref:System.Windows.Freezable.IsFrozen%2A> が `false` となり、実行時には一般的な <xref:System.Windows.Freezable> の動作に依存します。  
  
## XAML 属性の使用方法  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`PresentationOptions`|XML 名前空間プレフィックス。XML 1.0 仕様で定められている有効な任意のプレフィックス文字列を指定できます。  プレフィックス `PresentationOptions` は、このドキュメントでの識別のために使用します。|  
|`freezableElement`|<xref:System.Windows.Freezable> の任意の派生クラスをインスタンス化する要素。|  
  
## 解説  
 `Freeze` 属性は、属性および他のプログラミング要素の中で唯一、`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML 名前空間で定義されています。  `Freeze` 属性がこの特殊な名前空間に置かれているのは、ルート要素宣言の一部として [mc:Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) を使用して、明確に無視可能と指定できるようにするためです。  `Freeze` を無視できるようにする必要があるのは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサの実装の中には、読み込み時に <xref:System.Windows.Freezable> を固定できないものがあるためです。この機能は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の仕様には含まれていません。  
  
 `Freeze` 属性を処理する機能は、コンパイル済みアプリケーション用に [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を処理する [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサに明確に組み込まれています。  この属性はどのクラスによってもサポートされず、属性の構文を拡張または変更することはできません。  独自の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサを実装する場合は、1 つの選択肢として、読み込み時に <xref:System.Windows.Freezable> 要素の `Freeze` 属性を処理する際に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサの固定動作を並行して行うことができます。  
  
 `Freeze` 属性に `true` \(大文字と小文字は区別されません\) 以外の値を指定すると、読み込み時にエラーが発生します。  `Freeze` 属性に `false` を指定してもエラーにはなりませんが、この値は既定値なので、`false` を設定しても何も行われません。  
  
## 参照  
 <xref:System.Windows.Freezable>   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [mc:Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)