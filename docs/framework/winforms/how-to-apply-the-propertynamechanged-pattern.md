---
title: "方法 : PropertyNameChanged パターンを適用する | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], プロパティの変更 (コードを使用)"
  - "データ バインド, カスタム コントロール"
  - "PropertyNameChanged パターン, 適用"
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : PropertyNameChanged パターンを適用する
次のコード例では、*PropertyName*Changed パターンをカスタム コントロールに適用する方法を示します。  Windows フォーム データ バインディング エンジンと一緒に使用するカスタム コントロールを実装する場合は、このパターンを適用します。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## コードのコンパイル  
 上記のコード例をコンパイルするには  
  
-   コードを空白のコード ファイルに貼り付けます。  `Main` メソッドを含む Windows フォームで、カスタム コントロールを使用する必要があります。  
  
## 参照  
 [方法 : INotifyPropertyChanged インターフェイスを実装する](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)   
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)