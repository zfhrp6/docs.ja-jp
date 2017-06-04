---
title: "方法 : Windows フォーム GroupBox コントロールを使用してコントロールをグループ化する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], グループ化"
  - "GroupBox コントロール [Windows フォーム], グループ化 (コントロールを)"
  - "Windows フォーム コントロール, グループ化"
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Windows フォーム GroupBox コントロールを使用してコントロールをグループ化する
Windows フォームの <xref:System.Windows.Forms.GroupBox> コントロールを使用すると、他のコントロールをグループ化できます。  コントロールのグループ化には、次の 3 つの利点があります。  
  
-   関連しているフォーム要素を視覚的にグループ化して、わかりやすいユーザー インターフェイスを提供します。  
  
-   オプション ボタンなどをグループ化してプログラミングできます。  
  
-   デザイン時に複数のコントロールをまとめて移動できます。  
  
### コントロールのグループを作成するには  
  
1.  フォームに <xref:System.Windows.Forms.GroupBox> コントロールを配置します。  
  
2.  グループ ボックスにほかのコントロールを追加し、それぞれグループ ボックス内に配置します。  
  
     既存のコントロールをグループ ボックスに追加する場合は、追加するすべてのコントロールを選択し、クリップボードに切り取ります。次に、<xref:System.Windows.Forms.GroupBox> コントロールを選択し、コントロールをグループ ボックスに貼り付けます。  コントロールをグループ ボックスにドラッグすることもできます。  
  
3.  グループ ボックスの <xref:System.Windows.Forms.GroupBox.Text%2A> プロパティに適切なキャプションを設定します。  
  
## 参照  
 <xref:System.Windows.Forms.GroupBox>   
 [GroupBox コントロール](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)