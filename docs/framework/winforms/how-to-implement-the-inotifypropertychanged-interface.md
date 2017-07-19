---
title: "方法 : INotifyPropertyChanged インターフェイスを実装する | Microsoft Docs"
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
  - "INotifyPropertyChanged インターフェイス, 実装"
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : INotifyPropertyChanged インターフェイスを実装する
<xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装する方法を次のコード例に示します。  このインターフェイスを Windows フォーム データ バインディングで使用されるビジネス オブジェクトに実装します。  実装すると、インターフェイスは、ビジネス オブジェクトでのバインド コントロールのプロパティの変更内容と通信します。  
  
## 使用例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## 参照  
 [方法 : PropertyNameChanged パターンを適用する](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [方法 : BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)   
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)