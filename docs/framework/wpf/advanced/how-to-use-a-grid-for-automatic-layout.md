---
title: "方法 : 自動レイアウト用のグリッドを使用する | Microsoft Docs"
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
  - "自動レイアウト, グリッドの使用"
  - "グリッド, 自動レイアウト"
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 自動レイアウト用のグリッドを使用する
この例では、自動レイアウトの方法でグリッドを使用してローカライズ可能なアプリケーションを作成する方法について説明します。  
  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] のローカライズには時間がかかる場合があります。  ローカライザーは、多くの場合、テキストの翻訳だけでなく要素のサイズ変更や位置変更も行う必要があります。  これまでは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が翻訳された言語を調整する必要がありました。  現在では、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の機能により、調整する必要性の少ない要素をデザインできます。  サイズ変更や位置変更がより簡単になるアプリケーション作成方法は、`auto layout` と呼ばれます。  
  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 例では、グリッドを使用してボタンとテキストを配置する方法を示しています。  セルの高さと幅は `Auto` に設定されているため、イメージを持つボタンを含むセルがイメージに合わせて調整されることに注意してください。  <xref:System.Windows.Controls.Grid> 要素はコンテンツに合わせて調整できるため、ローカライズ可能なアプリケーションの設計に自動レイアウト方法を採用した場合に便利です。  
  
## 使用例  
 グリッドを使用する方法を次の例に示します。  
  
 [!code-xml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 コード サンプルによる出力を次の図に示します。  
  
 ![グリッドの例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob\_grid")  
\[グリッド\]  
  
## 参照  
 [自動レイアウトの使用の概要](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)   
 [自動レイアウトを使用してボタンを作成する](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)