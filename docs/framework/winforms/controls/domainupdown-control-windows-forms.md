---
title: "DomainUpDown コントロール (Windows フォーム) | Microsoft Docs"
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
  - "DomainUpDown コントロール [Windows フォーム]"
  - "スピン ボタン コントロール"
  - "スピン ボタン コントロール, アップダウン コントロール"
  - "アップダウン コントロール"
  - "アップダウン コントロール, スピン ボタン コントロール"
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# DomainUpDown コントロール (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.DomainUpDown> コントロールの外観は、テキスト ボックスと、リストの項目を上下に移動するためのボタンで構成されています。  このコントロールでは、選択肢のリストから 1 つの文字列を表示したり設定したりします。  ユーザーは、上下矢印ボタンをクリックするか、方向キーを押すことで、リストの項目を選択できます。また、リスト項目と一致する文字列を直接入力することもできます。  このコントロールでは、アルファベット順のリストで項目を選択できます。  リストを並べ替えるには、<xref:System.Windows.Forms.DomainUpDown.Sorted%2A> プロパティに `true` を設定します。このコントロールの機能はリスト ボックスやコンボ ボックスによく似ていますが、このコントロールではわずかなスペースしか使用しません。  
  
 コントロールの主要なプロパティは、<xref:System.Windows.Forms.DomainUpDown.Items%2A>、<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>、および <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> です。  <xref:System.Windows.Forms.DomainUpDown.Items%2A> プロパティには、コントロールに表示する文字列値を持つオブジェクトのリストを格納します。  <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> に `false` を設定すると、このコントロールは、ユーザーが一部を入力した文字列をオート コンプリートし、リストの値と一致させます。  <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> に `true` を設定すると、リストの末尾の項目より後にスクロールすると先頭の項目に移動します。先頭の項目より前にスクロールすると末尾の項目に移動します。  コントロールの主要なメソッドは、<xref:System.Windows.Forms.DomainUpDown.UpButton%2A> および <xref:System.Windows.Forms.DomainUpDown.DownButton%2A> です。  
  
 このコントロールが表示するのは文字列だけです。  数値を表示するコントロールが必要な場合は、<xref:System.Windows.Forms.NumericUpDown> コントロールを使用してください。  詳細については、「[NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)」を参照してください。  
  
## このセクションの内容  
 [DomainUpDown コントロールの概要](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 ユーザーが参照して選択できるテキスト文字列の一覧を表示する、<xref:System.Windows.Forms.DomainUpDown> コントロールの全般的な概念を説明します。  
  
 [方法 : Windows フォーム DomainUpDown コントロールにプログラムで項目を追加する](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <xref:System.Windows.Forms.DomainUpDown> コントロールで表示するテキスト文字列を指定する方法について説明します。  
  
 [方法 : Windows フォームの DomainUpDown コントロールから項目を削除する](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <xref:System.Windows.Forms.DomainUpDown> コントロールの項目をコードで削除する方法について説明します。  
  
## 関連項目  
 <xref:System.Windows.Forms.DomainUpDown>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
## 関連項目  
 [Windows フォームで使用できるコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 使用方法に関する情報へのリンクを含む、Windows フォーム コントロールの完全なリストを提供します。