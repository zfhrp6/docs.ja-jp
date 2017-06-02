---
title: "方法 : FlowDocument の列区切り属性を使用する | Microsoft Docs"
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
  - "列区切り属性"
  - "ドキュメント, FlowDocument の列区切り属性"
  - "FlowDocument の列区切り属性"
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : FlowDocument の列区切り属性を使用する
この例では、<xref:System.Windows.Documents.FlowDocument> の列区切り機能の使用方法を説明します。  
  
## 使用例  
 <xref:System.Windows.Documents.FlowDocument> を定義し、<xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>、<xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>、および <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> 属性を設定する例を次に示します。  この <xref:System.Windows.Documents.FlowDocument> には、サンプル コンテンツの単一の段落が含まれています。  
  
 [!code-xml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 描画された <xref:System.Windows.Documents.FlowDocument> の <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>、<xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>、および <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> 属性の効果を次の図に示します。  
  
 ![スクリーンショット: FlowDocument Intra 列](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")