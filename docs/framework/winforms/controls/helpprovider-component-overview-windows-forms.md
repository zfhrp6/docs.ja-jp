---
title: "HelpProvider コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "HelpProvider"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ダイアログ ボックス, 状況依存のヘルプ"
  - "F1 ヘルプ, 追加 (Windows フォームに)"
  - "ヘルプ, 追加 (Windows アプリケーションに)"
  - "HelpProvider コンポーネント [Windows フォーム], HelpProvider コンポーネントの概要"
  - "Windows フォーム, 状況依存のヘルプ"
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# HelpProvider コンポーネントの概要 (Windows フォーム)
Windows フォームの [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) コンポーネントは、HTML Help 1.x ヘルプ ファイル \(HTML Help Workshop で生成した .chm ファイル、または .htm ファイル\) を Windows アプリケーションに関連付けるために使用します。  ヘルプを用意するにはさまざまな方法があります。  
  
-   Windows フォームのコントロールに状況依存のヘルプを用意します。  
  
-   特定のダイアログ ボックスまたはダイアログ ボックス内の特定のコントロールに状況依存のヘルプを用意します。  
  
-   目次、索引、検索機能のメイン ページなど、ヘルプ ファイルの特定の領域を開きます。  
  
## HelpProvider の使用  
 <xref:System.Windows.Forms.HelpProvider> コンポーネントを Windows フォームに追加すると、フォーム上のその他のコントロールで <xref:System.Windows.Forms.HelpProvider> コンポーネントのヘルプ プロパティを公開できます。  これによって、Windows フォーム上にコントロールのヘルプを表示できます。  <xref:System.Windows.Forms.HelpProvider> コンポーネントにヘルプ ファイルを関連付けるには、<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> プロパティを使用します。  <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> を呼び出し、特定のコントロールの <xref:System.Windows.Forms.HelpNavigator> 列挙体の値を指定することによって、提供されるヘルプの種類を指定します。  <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> メソッドを呼び出して、ヘルプのキーワードまたはトピックを指定します。  
  
 また、特定のヘルプ文字列を他のコントロールに関連付けるには、<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> メソッドを使用します。  コントロールにフォーカスがあるときに F1 キーを押すと、コントロールに関連付けた文字列がポップアップ ウィンドウに表示されます。  
  
 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> が設定されていない場合は、<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> を使用してヘルプ テキストを用意する必要があります。  <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> とヘルプ文字列の両方が設定されている場合は、<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> のヘルプが優先されます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.Help.ShowHelp%2A> メソッドまたは <xref:System.Windows.Forms.HelpProvider> コントロールの <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> プロパティでヘルプ ファイルへのパスを指定する場合に相対パスを使用すると、問題が生じることがあります。  したがって、ヘルプ ファイルを指定する場合は、必ず絶対ファイル パスを使用してください。  
  
## 参照  
 [Windows フォーム アプリケーションのヘルプ システム](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)