---
title: "方法 : SystemParameters を使用する | Microsoft Docs"
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
  - "SystemParameters クラス"
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 方法 : SystemParameters を使用する
この例では、ボタンのスタイルを設定したりボタンをカスタマイズするために、<xref:System.Windows.SystemParameters> のプロパティにアクセスして使用する方法を示します。  
  
## 使用例  
 システム リソースは、システム設定との一貫性のあるビジュアルを作成できるようにするために、いくつかのシステムに基づく設定をリソースとして公開します。  <xref:System.Windows.SystemParameters> は、システム パラメーターの値プロパティ、それらの値にバインドされるリソース キーの両方を含むクラスです。  たとえば、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> は <xref:System.Windows.SystemParameters> プロパティ値であり、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> は対応するリソース キーです。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、<xref:System.Windows.SystemParameters> のメンバーを、静的プロパティまたは動的リソース参照 \(キーとして静的プロパティ値を使用\) として使用できます。  アプリケーションの実行中にシステムに基づく値を自動的に更新する場合は、動的リソース参照を使用します。それ以外の場合は、静的参照を使用します。  リソース キーの名前は、プロパティ名に `Key` というサフィックスが付いたものになります。  
  
 <xref:System.Windows.SystemParameters> の静的な値にアクセスして使用し、ボタンのスタイルを設定したり、ボタンをカスタマイズする方法を次の例に示します。  このマークアップ例では、ボタンに <xref:System.Windows.SystemParameters> 値を適用してボタンのサイズを設定します。  
  
 [!code-xml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 コードで <xref:System.Windows.SystemParameters> の値を使用する場合は、静的参照も動的リソース参照も使用する必要がありません。  代わりに、<xref:System.Windows.SystemParameters> クラスの値を使用します。  キー以外のプロパティは静的プロパティのように定義されますが、システムでホストされた [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の実行時の動作では、リアルタイムでプロパティが再評価され、ユーザーによるシステム値の変更が正しく反映されます。<xref:System.Windows.SystemParameters> 値を使用してボタンの幅と高さを設定する方法を次の例に示します。  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## 参照  
 <xref:System.Windows.SystemParameters>   
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [SystemFonts を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)   
 [システム パラメーター キーを使用する](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)