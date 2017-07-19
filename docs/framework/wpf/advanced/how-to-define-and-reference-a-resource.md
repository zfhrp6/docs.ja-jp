---
title: "方法 : リソースを定義および参照する | Microsoft Docs"
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
  - "定義 (リソースを)"
  - "参照 (リソースを)"
  - "リソース, 定義"
  - "リソース, 参照"
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : リソースを定義および参照する
この例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 内の属性を使用して、リソースを定義および参照する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.SolidColorBrush> リソースおよびいくつかの <xref:System.Windows.Style> リソースの、2 つの種類のリソースを定義する例を次に示します。  <xref:System.Windows.Media.SolidColorBrush> リソースの `MyBrush` を使用して、<xref:System.Windows.Media.Brush> 型の値を取得するいくつかのプロパティの値を提供します。  <xref:System.Windows.Style> リソースの `PageBackground`、 `TitleText`、`Label` は、それぞれ特定のコントロール型をターゲットにします。  スタイル リソースをリソース キーで参照し、そのスタイル リソースを使用して [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で定義するいくつかの特定のコントロール要素の <xref:System.Windows.FrameworkElement.Style%2A> プロパティを設定するとき、スタイルは、対象のコントロールのさまざまなプロパティを設定します。  
  
 `Label` スタイルの setter 内のプロパティの 1 つは、先に定義した `MyBrush` リソースも参照していることに注意してください。  これは一般的な手法ですが、リソースは、指定した順に解析されリソース ディクショナリに追加されます。  [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)を使用して別のリソース内から参照する場合、リソースは、ディクショナリ内で見つかった順序で要求されます。  参照するリソースは、そのリソースが要求されるよりも先に、リソース コレクション内ですべて定義しておく必要があります。  必要に応じて、代わりに [DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)を使用してリソースを実行時に参照することで、このリソース参照の厳密な作成手順を回避できますが、この DynamicResource 手法はパフォーマンスを低下させることに注意してください。  詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 [!code-xml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## 参照  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)