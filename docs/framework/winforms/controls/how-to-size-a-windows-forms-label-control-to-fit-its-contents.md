---
title: "方法 : Windows フォーム Label コントロールのサイズを内容に合わせて変更する | Microsoft Docs"
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
  - "キャプション, サイズ変更"
  - "Label コントロール [Windows フォーム], サイズ変更 (内容に合わせた)"
  - "ラベル, サイズ変更 (内容に合わせた)"
  - "サイズ, コントロール"
  - "サイズ変更コントロール"
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : Windows フォーム Label コントロールのサイズを内容に合わせて変更する
Windows フォーム <xref:System.Windows.Forms.Label> コントロールは、単一行または複数行で作成できます。コントロールのサイズは、固定するか、またはキャプションに合わせて自動的に変更できます。  <xref:System.Windows.Forms.Label.AutoSize%2A> プロパティは、キャプションの大きさに合わせてコントロールのサイズを変更するときに役立ちます。キャプションが実行時に変化する場合は、このプロパティを使用すると便利です。  
  
### 内容に合わせて Label コントロールのサイズを動的に変更するには  
  
1.  <xref:System.Windows.Forms.Label.AutoSize%2A> プロパティを `true` に設定します。  
  
 <xref:System.Windows.Forms.Label.AutoSize%2A> プロパティを `false` に設定した場合、<xref:System.Windows.Forms.Label.Text%2A> プロパティに指定したテキストは、可能な場合は次の行に折り返されます。ただし、コントロールのサイズが大きくなることはありません。  
  
## 参照  
 [方法 : Windows フォームの Label コントロールでアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)   
 [Label コントロールの概要](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [Label コントロール](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)