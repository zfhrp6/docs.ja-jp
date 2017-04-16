---
title: "Windows フォームの Button コントロールを選択する方法 | Microsoft Docs"
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
  - "Button コントロール [Windows フォーム], 選択"
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows フォームの Button コントロールを選択する方法
Windows フォームのボタンは、次の方法で選択できます。  
  
-   マウスを使用してボタンをクリックします。  
  
-   コード内でボタンの <xref:System.Windows.Forms.Control.Click> イベントを呼び出します。  
  
-   **Tab** キーを押してボタンにフォーカスを移し、**Space** キーまたは **Enter** キーを押してボタンを選択します。  
  
-   ボタンに対応するアクセス キーを押します \(**Alt** キーを押しながら下線の付いた文字のキーを押します\)。  アクセス キーの詳細については、「[方法 : Windows フォーム コントロールのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)」を参照してください。  
  
-   ボタンがフォームの "承認" ボタンである場合は、Enter キーを押すとそのボタンが選択されます。フォーカスが他のコントロールにあっても、\(そのコントロールが承認ボタン以外のボタン、複数行のテキスト ボックス、または Enter キーをトラップするカスタム コントロールである場合を除き\) この方法でボタンを選択できます。  
  
-   ボタンがフォームの "キャンセル" ボタンである場合は、フォーカスが他のコントロールにあっても、**Esc** キーを押すとボタンが選択されます。  
  
-   <xref:System.Windows.Forms.Button.PerformClick%2A> メソッドを呼び出して、プログラムによってボタンを選択します。  
  
## 参照  
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [方法 : Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)