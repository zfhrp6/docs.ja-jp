---
title: "FontDialog コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "FontDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "フォント ダイアログ ボックス"
  - "フォント ダイアログ ボックス, Windows フォーム"
  - "FontDialog コンポーネント [Windows フォーム], FontDialog コンポーネントの概要"
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# FontDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.FontDialog> コンポーネントは、定義済みダイアログ ボックスです。このダイアログ ボックスは、現在システムにインストールされているフォントを表示するための、Windows の標準の **\[フォント\]** ダイアログ ボックスです。  このコントロールは、独自のダイアログ ボックスを使用せずにフォント設定を行うための簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。  
  
 既定でこのダイアログ ボックスに表示されるのは、フォント、フォント スタイル、およびサイズを選択するリスト ボックス、取り消し線や下線など、文字飾りを指定するチェック ボックス、書体の種類 \(スクリプト\) を指定するドロップダウン リスト、およびフォントの表示例です。  \[書体の種類\] ボックスを使用すると、指定されたフォントで利用できる他の文字セットを指定できます。たとえば、このドロップダウン リストで、"ヘブライ語" や "日本語" などを選択できます。フォントのダイアログ ボックスを表示するには、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを呼び出します。  
  
## 主要なプロパティ  
 このコンポーネントには、外観を設定するための多数のプロパティがあります。  このダイアログ ボックスの選択項目を設定するのは、<xref:System.Windows.Forms.FontDialog.Font%2A> プロパティと <xref:System.Windows.Forms.FontDialog.Color%2A> プロパティです。  <xref:System.Windows.Forms.FontDialog.Font%2A> プロパティは、フォント、スタイル、サイズ、書体の種類 \(スクリプト\)、および文字飾りを設定します。たとえば、 `Arial, 10pt, style=Italic, Strikeout` と指定します。  
  
## 参照  
 <xref:System.Windows.Forms.FontDialog>   
 [FontDialog コンポーネント](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)