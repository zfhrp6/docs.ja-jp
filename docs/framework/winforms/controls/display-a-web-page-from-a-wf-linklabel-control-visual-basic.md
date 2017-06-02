---
title: "方法 : Windows フォームの LinkLabel コントロールから Web ページを表示する (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LinkLabel1_LinkClicked"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "例 [Windows フォーム], LinkLabel コントロール"
  - "リンク, Web ページへのフォームからの"
  - "LinkLabel コントロール [Windows フォーム], 例"
  - "Web ページ, 表示"
  - "Windows フォーム, リンク (Web ページに)"
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : Windows フォームの LinkLabel コントロールから Web ページを表示する (Visual Basic)
次の例では、ユーザーが Windows フォームの <xref:System.Windows.Forms.LinkLabel> コントロールをクリックしたときに、既定のブラウザーに Web ページが表示されます。  
  
## 使用例  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `Form1` という Windows フォーム  
  
-   `LinkLabel1` という名前の <xref:System.Windows.Forms.LinkLabel> コントロール。  
  
-   アクティブなインターネット接続  
  
## .NET Framework セキュリティ  
 <xref:System.Diagnostics.Process.Start%2A> メソッドを呼び出すには、完全な信頼が必要です。  詳細については、「<xref:System.Security.SecurityException>」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.LinkLabel>   
 [LinkLabel コントロール](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)