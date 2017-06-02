---
title: "方法 : GroupBox テンプレートを定義する | Microsoft Docs"
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
  - "コントロール, GroupBox"
  - "GroupBox コントロール, 作成 (テンプレートを)"
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : GroupBox テンプレートを定義する
この例では、<xref:System.Windows.Controls.GroupBox> コントロールのテンプレートを作成する方法を示します。  
  
## 使用例  
 次の例で定義する <xref:System.Windows.Controls.GroupBox> コントロール テンプレートでは、<xref:System.Windows.Controls.Grid> コントロールを使用してレイアウトを行います。  このテンプレートは <xref:System.Windows.Controls.BorderGapMaskConverter> を使用して <xref:System.Windows.Controls.GroupBox> の境界線を定義しているので、境界線で <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> コンテンツが隠されることはありません。  
  
 [!code-xml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## 参照  
 <xref:System.Windows.Controls.GroupBox>   
 [GroupBox How\-to Topics](http://msdn.microsoft.com/ja-jp/7692e155-a4c6-428c-b7e0-64b3740daca7)