---
title: "方法 : Windows フォーム ListView コントロール内の項目を選択する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "リスト ビュー, 選択 (項目の)"
  - "一覧, 選択 (項目の)"
  - "ListView コントロール [Windows フォーム], 選択 (項目の)"
  - "選択, リスト ビュー内で"
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : Windows フォーム ListView コントロール内の項目を選択する
次のコード例では、Windows フォームの <xref:System.Windows.Forms.ListView> コントロール内の項目をプログラムで選択します。  項目をプログラムで選択しても、フォーカスは自動的に <xref:System.Windows.Forms.ListView> コントロールには変更されません。  そのため、項目を選択するときは、通常、その項目をフォーカスがある状態に設定します。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   1 つ以上の項目を持つ、`listView1` という名前の <xref:System.Windows.Forms.ListView> コントロール。  
  
-   <xref:System?displayProperty=fullName> 名前空間および <xref:System.Windows.Forms?displayProperty=fullName> 名前空間への参照。  
  
## 参照  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=fullName>