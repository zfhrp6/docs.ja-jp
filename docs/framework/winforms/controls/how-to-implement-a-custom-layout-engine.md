---
title: "方法 : カスタム レイアウト エンジンを実装する | Microsoft Docs"
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
  - "FlowLayoutPanel コントロール [Windows フォーム], レイアウト エンジン"
  - "レイアウト エンジン, カスタム"
  - "レイアウト エンジン, 実装"
  - "LayoutEngine クラス"
  - "TableLayoutPanel コントロール [Windows フォーム], レイアウト エンジン"
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : カスタム レイアウト エンジンを実装する
単純なフロー レイアウトを実行するカスタム レイアウト エンジンを作成する方法を次のコード例に示します。  このコード例では、`DemoFlowPanel` という名前のパネル コントロールを実装します。このパネル コントロールは <xref:System.Windows.Forms.Control.LayoutEngine%2A> プロパティをオーバーライドして `DemoFlowLayout` クラスのインスタンスを提供します。  
  
## 使用例  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## 参照  
 <xref:System.Windows.Forms.Layout.LayoutEngine>   
 <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=fullName>