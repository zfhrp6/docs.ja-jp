---
title: "方法 : Windows フォームを印刷する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "印刷 [Windows フォーム], 印刷 (フォームの)"
  - "印刷 [Windows フォーム]"
  - "印刷 (フォームの)"
  - "Windows フォーム, 印刷"
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Windows フォームを印刷する
開発プロセスにおいて、多くの場合、Windows フォームのコピーを印刷する必要があります。  現在のフォームのコピーを <xref:System.Drawing.Graphics.CopyFromScreen%2A> メソッドを使用して印刷する方法を次のコード例に示します。  
  
## 使用例  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## コードのコンパイル  
 これは、`Main` メソッドを含むコード全体の例です。  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   プリンターへのアクセス許可がない。  
  
-   プリンターがインストールされていない。  
  
## .NET Framework セキュリティ  
 このコード例を実行するには、現在のコンピューターで使用しているプリンターへのアクセス許可が必要です。  
  
## 参照  
 <xref:System.Drawing.Printing.PrintDocument>   
 [方法 : GDI\+ を使用してイメージをレンダリングする](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)   
 [方法 : Windows フォームでグラフィックスを印刷する](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)