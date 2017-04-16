---
title: "方法 : 装飾を実装する | Microsoft Docs"
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
  - "装飾, 実装"
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 装飾を実装する
この例では、最小限の装飾の実装を示します。  
  
## 実装についてのメモ  
 Adorner 自体には継承されたレンダリング動作は含まれず、Adorner のレンダリングは Adorner の実装者の責任で行う必要がある点について注意が必要です。  レンダリング動作を実装する一般的な方法としては、<xref:System.Windows.UIElement.OnRender%2A> メソッドをオーバーライドし、1 つ以上の <xref:System.Windows.Media.DrawingContext> オブジェクトを使用して、装飾のビジュアルを必要に応じて描画します \(次の例を参照\)。  
  
## 例  
  
### Description  
 抽象型 <xref:System.Windows.Documents.Adorner> クラスから継承されるクラスを実装することにより、カスタムの Adorner が作成されます。  この例の装飾では、<xref:System.Windows.UIElement.OnRender%2A> メソッドをオーバーライドして <xref:System.Windows.UIElement> の四隅を円で装飾します。  
  
### コード  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## 参照  
 [装飾の概要](../../../../docs/framework/wpf/controls/adorners-overview.md)