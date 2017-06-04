---
title: "方法 : システム パラメーター キーを使用する | Microsoft Docs"
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
  - "クラス, SystemParameters"
  - "リソース キー, SystemParameters クラス"
  - "SystemParameters クラス"
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : システム パラメーター キーを使用する
システム リソースは、システム設定との一貫性のあるビジュアルを作成できるようにするために、数多くのシステム メトリックをリソースとして公開します。  <xref:System.Windows.SystemParameters> は、システム パラメーター値とそれらの値にバインドされるリソース キー \(<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> など\) の両方を含むクラスです。  システム パラメーター メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。  アプリケーションの実行中にパラメーター メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。  
  
> [!NOTE]
>  動的リソースのプロパティ名には、キーワード *Key* が追加されています。  
  
 システム パラメーター動的リソースにアクセスして、ボタンのスタイルの設定やボタンのカスタマイズに使用する方法を次の例に示します。  この [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例では、ボタンの幅と高さに <xref:System.Windows.SystemParameters> の値を割り当ててボタンのサイズを設定します。  
  
## 使用例  
 [!code-xml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## 参照  
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [SystemFonts を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)   
 [SystemParameters を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)