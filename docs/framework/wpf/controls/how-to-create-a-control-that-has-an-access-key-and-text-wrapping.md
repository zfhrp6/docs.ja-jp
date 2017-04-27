---
title: "方法 : アクセス キーおよびテキスト折り返し機能を持つコントロールを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アクセス キー, コントロール"
  - "コントロール, アクセス キー"
  - "コントロール, テキストの折り返し"
  - "キー, コントロール"
  - "テキストの折り返し"
  - "折り返し (テキストを)"
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : アクセス キーおよびテキスト折り返し機能を持つコントロールを作成する
この例では、[アクセス キー](GTMT)を持ち、テキストの折り返しをサポートするコントロールを作成する方法を示します。  これらの概念を示すために、例では <xref:System.Windows.Controls.Label> コントロールを使用します。  
  
## 使用例  
 **ラベルにテキストの折り返し機能を追加する**  
  
 <xref:System.Windows.Controls.Label> コントロールは、テキストの折り返しをサポートしません。  複数行にわたって折り返すラベルが必要な場合は、テキストの折り返しをサポートする別の要素を入れ子にして、その要素をラベルの内部に配置します。  複数のテキスト行にわたって折り返すラベルを <xref:System.Windows.Controls.TextBlock> を使用して作成する方法を次の例に示します。  
  
 <!-- TODO: review snippet reference [!code-xml[Label#5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Label/XAML/Pane1.xaml#5)]  -->
 <!-- TODO: review snippet reference [!code-xml[Label#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Label/CS/Pane1.xaml#5)]  -->  
  
 **アクセス キーとテキストの折り返しをラベルに追加する**  
  
 アクセス キー \(ニーモニック\) を持つ <xref:System.Windows.Controls.Label> が必要な場合は、<xref:System.Windows.Controls.Label> の内部の <xref:System.Windows.Controls.AccessText> を使用します。  
  
 <xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.RadioButton>、<xref:System.Windows.Controls.CheckBox>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.TabItem>、<xref:System.Windows.Controls.Expander>、<xref:System.Windows.Controls.GroupBox> などのコントロールには、既定のコントロール テンプレートがあります。  これらのテンプレートには、<xref:System.Windows.Controls.ContentPresenter> が含まれます。  <xref:System.Windows.Controls.ContentPresenter> で設定できるプロパティの 1 つに <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>\="true" があり、これを使用するとコントロールのアクセス キーを指定できます。  
  
 アクセス キーを持ち、テキストの折り返しをサポートする <xref:System.Windows.Controls.Label> を作成する方法を次の例に示します。  この例では、テキストの折り返しを有効にするために <xref:System.Windows.Controls.AccessText.TextWrapping%2A> プロパティを設定し、下線文字を使用してアクセス キーを示しています。  下線文字のすぐ後にある文字がアクセス キーです。  
  
 <!-- TODO: review snippet reference [!code-xml[Label#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Label/XAML/Pane1.xaml#4)]  -->
 <!-- TODO: review snippet reference [!code-xml[Label#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Label/CS/Pane1.xaml#4)]  -->  
  
## 参照  
 [How to: Set the Target Property of a Label](http://msdn.microsoft.com/ja-jp/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)