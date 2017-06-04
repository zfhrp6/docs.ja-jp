---
title: "方法 : システム フォント キーを使用する | Microsoft Docs"
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
  - "クラス, SystemFonts"
  - "リソース キー, SystemFonts クラス"
  - "SystemFonts クラス"
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : システム フォント キーを使用する
システム リソースは、システム設定との一貫性のあるビジュアルを作成できるようにするために、数多くのシステム メトリックをリソースとして公開します。  <xref:System.Windows.SystemFonts> は、システム パラメーター値とその値にバインドされるリソース キー \(たとえば <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> と <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>\) の両方を含むクラスです。  
  
 システム フォント メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。  アプリケーションの実行中にフォント メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。  
  
> [!NOTE]
>  動的リソースのプロパティ名には、キーワード *Key* が追加されています。  
  
 システム フォント動的リソースにアクセスして使用し、ボタンのスタイルを設定したり、ボタンをカスタマイズする方法を次の例に示します。  この [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例では、ボタンに <xref:System.Windows.SystemFonts> 値を割り当てるボタン スタイルを作成します。  
  
## 使用例  
 [!code-xml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## 参照  
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [SystemParameters を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)   
 [SystemFonts を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)