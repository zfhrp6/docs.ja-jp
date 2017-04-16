---
title: "方法 : カスタム コントロールでインクを消去する | Microsoft Docs"
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
  - "カスタム コントロール, 消去 (インクを)"
  - "インク, 消去 (カスタム コントロールで)"
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : カスタム コントロールでインクを消去する
<xref:System.Windows.Ink.IncrementalStrokeHitTester> は、現在描画されているストロークが他のストロークと交差しているかどうかを判別します。  これは、ユーザーがストロークの一部を消去する際に使用するコントロールの作成に役立ちます。ユーザーがこの消去処理を <xref:System.Windows.Controls.InkCanvas> で行うには、<xref:System.Windows.Controls.InkCanvas.EditingMode%2A> を <xref:System.Windows.Controls.InkCanvasEditingMode> に設定する必要があります。  
  
## 使用例  
 ユーザーがストロークの一部を消去する際に使用するカスタム コントロールの作成例を次に示します。  この例では、初期化時にインクを含むコントロールを作成します。  インクを収集するコントロールの作成方法については、「[インク入力コントロールの作成](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)」を参照してください。  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]