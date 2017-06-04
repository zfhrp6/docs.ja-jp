---
title: "方法 : 分析のヒントに従ってインクを分析する | Microsoft Docs"
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
  - "AnalysisHintNode オブジェクト"
  - "分析 (インクを)"
  - "インク, AnalysisHintNode オブジェクト"
  - "インク, 分析"
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : 分析のヒントに従ってインクを分析する
<xref:System.Windows.Ink.AnalysisHintNode> は、結合先の <xref:System.Windows.Ink.InkAnalyzer> にヒントを提供します。  ヒントは、<xref:System.Windows.Ink.AnalysisHintNode> の <xref:System.Windows.Ink.ContextNode.Location%2A> プロパティで指定された領域に適用され、インク アナライザーに追加のコンテキストを提供します。これにより、認識の正確さが向上します。  <xref:System.Windows.Ink.InkAnalyzer> は、ヒントの領域内から取得したインクを分析するときにこのコンテキスト情報を適用します。  
  
## 使用例  
 インク入力を受け入れるフォームの <xref:System.Windows.Ink.AnalysisHintNode> オブジェクトを複数使用するアプリケーションを次の例に示します。  このアプリケーションは、<xref:System.Windows.Ink.AnalysisHintNode.Factoid%2A> プロパティを使用して、フォームの各エントリにコンテキスト情報を提供します。  このアプリケーションは、バックグラウンド分析を使用してインクを分析し、ユーザーがインクの追加を停止した 5 秒後にフォームのすべてのインクを消去します。  
  
 [!code-xml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]