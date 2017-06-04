---
title: "方法 : SystemFonts を使用する | Microsoft Docs"
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
  - "フォント, システム フォント"
  - "システム フォント"
  - "SystemFonts クラス"
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 方法 : SystemFonts を使用する
この例では、ボタンをスタイル設定またはカスタマイズするために <xref:System.Windows.SystemFonts> クラスの静的リソースを使用する方法を示します。  
  
## 使用例  
 システム リソースは、システム設定との一貫性のあるビジュアルを作成できるようにするために、いくつかのシステムによって決定される値をリソースおよびプロパティの両方として公開します。  <xref:System.Windows.SystemFonts> は、システム フォント値を静的プロパティとして含む他、実行時にこれらの値に動的にアクセスするためのリソース キーを参照するプロパティを含むクラスです。  たとえば、<xref:System.Windows.SystemFonts.CaptionFontFamily%2A> は <xref:System.Windows.SystemFonts> 値であり、<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> は対応するリソース キーです。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、<xref:System.Windows.SystemFonts> のメンバーを、静的プロパティまたは動的リソース参照 \(キーとして静的プロパティ値を使用\) として使用できます。  アプリケーションの実行中にフォント メトリックを自動的に更新する場合は、動的リソース参照を使用します。それ以外の場合は、静的な値参照を使用します。  
  
> [!NOTE]
>  リソース キーの名前は、プロパティ名に "Key" というサフィックスが付いたものになります。  
  
 静的な値である <xref:System.Windows.SystemFonts> のプロパティにアクセスして使用し、ボタンのスタイルを設定したり、ボタンをカスタマイズしたりする方法を次の例に示します。  このマークアップの例では、ボタンに <xref:System.Windows.SystemFonts> 値を割り当てます。  
  
 [!code-xml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 コードで <xref:System.Windows.SystemFonts> の値を使用する場合は、静的な値も動的リソース参照も使用する必要はありません。  代わりに、<xref:System.Windows.SystemFonts> クラスのキー以外のプロパティを使用します。  キー以外のプロパティは静的プロパティのように定義されますが、システムでホストされた [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の実行時の動作では、リアルタイムでプロパティが再評価され、ユーザーによるシステム値の変更が正しく反映されます。  ボタンのフォント設定を指定する方法を次の例に示します。  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## 参照  
 <xref:System.Windows.SystemFonts>   
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [SystemParameters を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)   
 [システム フォント キーを使用する](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)   
 [x:Static のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-static-markup-extension.md)   
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)