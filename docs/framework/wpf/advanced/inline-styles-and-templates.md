---
title: "インライン スタイルおよびテンプレート | Microsoft Docs"
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
  - "インライン スタイル"
  - "インライン テンプレート"
  - "スタイル, inline"
  - "テンプレート, inline"
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# インライン スタイルおよびテンプレート
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、<xref:System.Windows.Style> オブジェクトとテンプレート オブジェクト \(<xref:System.Windows.FrameworkTemplate> サブクラス\) を、要素の外観をリソースで定義する方法として提供するので、これらのオブジェクトは複数回数使用できます。  このため、型 <xref:System.Windows.Style> および型 <xref:System.Windows.FrameworkTemplate> を取る [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の属性は、ほとんどの場合、新たにインラインで定義するのではなく、既存のスタイルとテンプレートへのリソース参照を作成します。  
  
## インライン スタイルおよびテンプレートの制限  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、スタイル プロパティとテンプレート プロパティを、技術的に次のいずれかの方法で設定できます。  属性構文を使用して、リソース内で定義されたスタイルを参照できます。たとえば、`<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>` とします。  または、プロパティ要素構文を使用して、スタイル インラインを定義できます。次はその例です。  
  
 `<` *object* `>`  
  
 `<` *object* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *object* `.Style>`  
  
 `</` *object* `>`  
  
 属性の使用方法は、さらに一般的です。  インラインで定義され、リソースでは定義されないスタイルは、必然的に、含まれる要素のみに有効範囲が限定されます。また、リソース キーを持たないため、簡単には再利用できません。  一般に、リソースで定義されるスタイルは、汎用性と有用性が高く、コードでのプログラム ロジックとマークアップでのデザインを分離する一般的な [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プログラミング モデルの方針により合っています。  
  
 通常、その場所でスタイルまたはテンプレートを使用するだけの場合でも、スタイルやテンプレートをインラインで設定する必要はありません。  ほとんどの要素は、スタイルまたはテンプレートを取ることができ、また、コンテンツ プロパティとコンテンツ モデルをサポートします。  スタイルまたはテンプレートで作成する論理ツリーを一度使用するだけの場合、マークアップで、同等の子要素によってコンテンツ プロパティを直接設定するだけの方がよりいっそう簡単です。  これは、スタイル機構とテンプレート機構を完全にバイパスします。  
  
 オブジェクトを返すマークアップ拡張機能によって有効となる他の構文も、スタイルおよびテンプレートには可能です。  考えられるシナリオを持つ 2 つの拡張機能として、[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) と <xref:System.Windows.Data.Binding> があります。  
  
## 参照  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)