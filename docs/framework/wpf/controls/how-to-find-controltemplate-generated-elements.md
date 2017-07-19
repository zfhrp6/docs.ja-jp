---
title: "方法 : ControlTemplate によって生成された要素を検索する | Microsoft Docs"
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
  - "ControlTemplate [WPF], 検索 (要素を)"
  - "検索 (ControlTemplate 要素を)"
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : ControlTemplate によって生成された要素を検索する
この例では、<xref:System.Windows.Controls.ControlTemplate> によって生成された要素の検索方法について説明します。  
  
## 使用例  
 次の例は、<xref:System.Windows.Controls.Button> クラス用のシンプルな <xref:System.Windows.Controls.ControlTemplate> を作成するスタイルを示しています。  
  
 [!code-xml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 テンプレートの適用後にテンプレート内の要素を検索するには、<xref:System.Windows.Controls.Control.Template%2A> の <xref:System.Windows.FrameworkTemplate.FindName%2A> メソッドを呼び出します。  次の例は、コントロール テンプレート内にある <xref:System.Windows.Controls.Grid> の実際の幅の値を表示するメッセージ ボックスを作成しています。  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## 参照  
 [DataTemplate によって生成された要素を検索する](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [WPF XAML 名前スコープ](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)   
 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)