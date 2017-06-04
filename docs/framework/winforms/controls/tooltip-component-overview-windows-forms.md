---
title: "ToolTip コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "ToolTip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ToolTip コンポーネント [Windows フォーム], ToolTip コンポーネントの概要"
  - "ツールヒント [Windows フォーム], ツールヒントの概要"
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# ToolTip コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.ToolTip> コンポーネントは、ユーザーがコントロールをポイントしたときにテキストを表示します。  ツールヒントは、どのコントロールにも関連付けることができます。  たとえば、ボタンに小さなアイコンを表示し、ツールヒントでボタンの機能を説明することで、フォームのスペースを節約できます。  
  
## ToolTip コンポーネントの操作  
 <xref:System.Windows.Forms.ToolTip> コンポーネントは、Windows フォームなどのコンテナーにある複数のコントロールに `ToolTip` プロパティを提供します。  たとえば、1 つの <xref:System.Windows.Forms.ToolTip> コンポーネントをフォームに配置して、<xref:System.Windows.Forms.TextBox> コントロールをポイントしたときに "ここに名前を入力してください" と表示したり、<xref:System.Windows.Forms.Button> コントロールをポイントしたときに "変更を保存するときはこのボタンをクリックしてください" と表示したりできます。  
  
 <xref:System.Windows.Forms.ToolTip> コンポーネントの主要なメソッドは、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A> および <xref:System.Windows.Forms.ToolTip.GetToolTip%2A> です。  <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> メソッドは、コントロールに対応するツールヒントを設定します。  詳細については、「[方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)」を参照してください。  主要なプロパティは 2 つです。ツールヒントを表示するには <xref:System.Windows.Forms.ToolTip.Active%2A> プロパティを `true` に設定する必要があります。<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> プロパティでは、ツールヒント文字列が表示される時間の長さ、ツールヒントが表示されるまでコントロールをポイントする必要がある時間、および後続のツールヒント ウィンドウが表示されるまでの時間を設定します。  詳細については、「[方法 : Windows フォームの ToolTip コンポーネントの遅延時間を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.ToolTip>   
 [方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)   
 [方法 : Windows フォームの ToolTip コンポーネントの遅延時間を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)