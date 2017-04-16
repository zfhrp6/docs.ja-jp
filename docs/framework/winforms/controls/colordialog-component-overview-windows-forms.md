---
title: "ColorDialog コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "ColorDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "色のダイアログ ボックス, 色のダイアログ ボックスの概要"
  - "ColorDialog コンポーネント, ColorDialog の概要"
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# ColorDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.ColorDialog> コンポーネントは、定義済みダイアログ ボックスです。このダイアログ ボックスでは、パレットから色を選択したりパレットに色を追加したりできます。  このダイアログ ボックスは、他の Windows ベースのアプリケーションで表示される色を選択するためのダイアログ ボックスと同じです。  このコントロールは、独自のダイアログ ボックスを使用しない簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。  
  
 ダイアログ ボックスで選択された色は、<xref:System.Windows.Forms.ColorDialog.Color%2A> プロパティに返されます。  <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> プロパティが `false` に設定されると、\[色の作成\] ボタンが無効になり、ユーザーが使用できる色はパレット内の定義済みの色に制限されます。  <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> プロパティが `true` に設定されると、ユーザーはディザー カラーを選択できなくなります。  ダイアログ ボックスを表示するには、コントロールの <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを呼び出す必要があります。  
  
## 参照  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog コンポーネント](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)   
 [ダイアログ ボックス コントロールおよびコンポーネント](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)   
 [方法 : Windows フォーム ColorDialog コンポーネントの表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)