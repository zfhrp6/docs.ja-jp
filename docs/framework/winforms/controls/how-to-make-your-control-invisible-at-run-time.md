---
title: "方法 : 実行時にコントロールを非表示にする | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 非表示 (実行時に)"
  - "カスタム コントロール [Windows フォーム], 非表示の"
  - "非表示のコントロール"
  - "実行時に, 非表示 (コントロールを)"
  - "ユーザー コントロール [Windows フォーム], 非表示の"
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 実行時にコントロールを非表示にする
実行時には表示されないユーザー コントロールを作成することが必要な場合もあります。  たとえば、アラーム クロックなどは、音が鳴っている間以外は表示されないのが普通です。  この機能は <xref:System.Windows.Forms.Control.Visible%2A> プロパティによって簡単に実現できます。  <xref:System.Windows.Forms.Control.Visible%2A> プロパティを `true` に設定した場合、コントロールは通常どおりに表示されます。  `false` に設定した場合、コントロールは非表示になります。  コントロールが非表示のときでもコードの実行は継続されますが、ユーザー インターフェイスを介したコントロールとの対話はできません。  ユーザー入力 \(マウス クリックなど\) に応答できる状態でコントロールを非表示にするには、透過的なコントロールを作成します。  詳細については、「[コントロールへの透明な背景の適用](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)」を参照してください。  
  
### 実行時にコントロールを非表示にするには  
  
1.  <xref:System.Windows.Forms.Control.Visible%2A> プロパティを `false` に設定します。  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.Control.Visible%2A>   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [方法 : コントロールに透明な背景を指定する](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)