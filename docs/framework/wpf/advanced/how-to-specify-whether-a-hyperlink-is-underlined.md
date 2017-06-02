---
title: "方法: ハイパーリンクに下線を引くかどうかを指定する | Microsoft Docs"
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
  - "クラス, TextDecoration"
  - "ハイパーリンク コントロール型"
  - "TextDecoration クラス"
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法: ハイパーリンクに下線を引くかどうかを指定する
<xref:System.Windows.Documents.Hyperlink> オブジェクトはインラインレベルのフロー コンテンツ要素であり、これを使用すると、フロー コンテンツ内でハイパーリンクをホストできます。  既定では、<xref:System.Windows.Documents.Hyperlink> は、下線を表示するために、<xref:System.Windows.TextDecoration> オブジェクトを使用します。  <xref:System.Windows.TextDecoration> オブジェクトは、インスタンス化するために、パフォーマンスに大きな負荷をかけることがあります。特に、多数の <xref:System.Windows.Documents.Hyperlink> オブジェクトを使用する場合には、大きな負荷をかけます。  <xref:System.Windows.Documents.Hyperlink> 要素を広く使用する場合は、<xref:System.Windows.ContentElement.MouseEnter> イベントのようなイベントが発生したときにだけ下線を表示することを、検討する必要があります。  
  
 次の例では、"My MSN" リンクの下線は動的であり、<xref:System.Windows.ContentElement.MouseEnter> イベントが発生したときにのみ表示されます。  
  
 ![TextDecorations を表示するハイパーリンク](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
TextDecorations が定義されたハイパーリンク  
  
## 使用例  
 下線付きおよび下線なしで定義されている <xref:System.Windows.Documents.Hyperlink> のマークアップのサンプルを次に示します。  
  
 [!code-xml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 次のコード サンプルでは、<xref:System.Windows.Documents.Hyperlink> の下線を <xref:System.Windows.ContentElement.MouseEnter> イベントで表示し、<xref:System.Windows.ContentElement.MouseLeave> イベントで消去する方法を示します。  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## 参照  
 <xref:System.Windows.TextDecoration>   
 <xref:System.Windows.Documents.Hyperlink>   
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [文字の装飾を作成する](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)