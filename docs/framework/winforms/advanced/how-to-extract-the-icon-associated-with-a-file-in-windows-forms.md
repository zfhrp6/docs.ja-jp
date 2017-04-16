---
title: "方法 : Windows フォームでファイルに関連付けられているアイコンを抽出する | Microsoft Docs"
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
  - "表示 (ListView コントロールにファイル名とファイルの種類のアイコンを) [Windows フォーム]"
  - "抽出 (ファイルの種類に関連付けられているアイコンを) [Windows フォーム]"
  - "ファイル名の拡張子のアイコン [Windows フォーム], 表示 (ListView に)"
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : Windows フォームでファイルに関連付けられているアイコンを抽出する
多くのファイルには、関連付けられたファイルの種類をビジュアルに表すアイコンが埋め込まれています。  たとえば、Microsoft Word 文書には Word 文書として識別されるアイコンが含まれています。  リスト コントロールまたはテーブル コントロールにファイルの一覧を表示するときは、各ファイル名の横にファイルの種類を表すアイコンを表示すると便利な場合があります。  <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> メソッドを使用すると、この操作を簡単に実行できます。  
  
## 使用例  
 次のコード例は、ファイルに関連付けられているアイコンを抽出し、そのアイコンとファイル名を <xref:System.Windows.Forms.ListView> コントロールに表示する方法を示しています。  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## コードのコンパイル  
 この例をコンパイルするには、次の操作を行います。  
  
-   前のコードを Windows フォームに貼り付け、フォームのコンストラクターまたは <xref:System.Windows.Forms.Form.Load> イベント処理メソッドから `ExtractAssociatedIconExample` を呼び出します。  
  
     フォームには <xref:System.IO> 名前空間をインポートする必要があります。  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)