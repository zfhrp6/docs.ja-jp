---
title: "DomainUpDown コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "DomainUpDown"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DomainUpDown コントロール [Windows フォーム], DomainUpDown コントロールの概要"
  - "スピン ボタン コントロール, スピン ボタンの概要"
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# DomainUpDown コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.DomainUpDown> コントロールは、基本的にはテキスト ボックスと、リストの項目を上下に移動するためのボタンで構成されています。  このコントロールでは、選択肢のリストから 1 つの文字列を表示したり設定したりします。  ユーザーは、上下矢印ボタンをクリックするか、方向キーを押すことで、リストの項目を選択できます。また、リスト項目と一致する文字列を直接入力することもできます。  このコントロールでは、アルファベット順のリストで項目を選択できます。  
  
> [!NOTE]
>  リストを並べ替えるには、<xref:System.Windows.Forms.DomainUpDown.Sorted%2A> プロパティに `true` を設定します。  
  
 このコントロールの機能はリスト ボックスやコンボ ボックスによく似ていますが、このコントロールではわずかなスペースしか使用しません。  
  
## 主要なプロパティ  
 コントロールの主要なプロパティは、<xref:System.Windows.Forms.DomainUpDown.Items%2A>、<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>、および <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> です。  <xref:System.Windows.Forms.DomainUpDown.Items%2A> プロパティには、コントロールに表示する文字列値を持つオブジェクトのリストを格納します。  <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> に `false` を設定すると、このコントロールは、ユーザーが一部を入力した文字列をオート コンプリートし、リストの値と一致させます。  <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> に `true` を設定すると、リストの末尾の項目より後にスクロールすると先頭の項目に移動します。先頭の項目より前にスクロールすると末尾の項目に移動します。  コントロールの主要なメソッドは、<xref:System.Windows.Forms.DomainUpDown.UpButton%2A> および <xref:System.Windows.Forms.DomainUpDown.DownButton%2A> です。  
  
 このコントロールが表示するのは文字列だけです。  数値を表示するコントロールが必要な場合は、<xref:System.Windows.Forms.NumericUpDown> コントロールを使用してください。  詳細については、「[NumericUpDown コントロールの概要](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DomainUpDown>   
 [DomainUpDown コントロール](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)