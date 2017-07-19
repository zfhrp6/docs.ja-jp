---
title: "キーボード イベントの使用 | Microsoft Docs"
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
  - "イベント [Windows フォーム], キーボード"
  - "キーボード イベント"
  - "キーボード, キーボード イベント"
  - "KeyDown イベント"
  - "KeyPress イベント"
  - "KeyUp イベント"
ms.assetid: d3f3e14b-a459-4ee6-9875-8957e34f8ee9
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# キーボード イベントの使用
多くの Windows フォーム プログラムは、キーボード イベントを処理することによってキーボード入力を処理します。  ここでは、どのような場合に各キーボード イベントを使用するか、また各イベントがどのようなデータを提供するかについての詳細を含め、キーボード イベントの概要について説明します。  「[イベント ハンドラーの概要 \(Windows フォーム\)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\))」、「[イベントの概要 \(Windows フォーム\)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))」も参照してください。  
  
## キーボード イベント  
 Windows フォームは、ユーザーがキーボードのキーを押したときに発生する 2 つのイベントと、キーボードのキーを離したときに発生する 1 つのイベントを提供します。これらのイベントは次のとおりです。  
  
-   <xref:System.Windows.Forms.Control.KeyDown> イベント。キーを押したときに 1 回発生します。  
  
-   <xref:System.Windows.Forms.Control.KeyPress> イベント。ユーザーが同じキーを押したままにすると、繰り返し発生する可能性があります。  
  
-   <xref:System.Windows.Forms.Control.KeyUp> イベント。ユーザーがキーを離したときに 1 回発生します。  
  
 ユーザーがキーを押すと、Windows フォームは、キーボード メッセージが文字キーまたは物理キーのどちらを示しているかに基づいて、発生させるイベントを決定します。  文字キーと物理キーの詳細については、「[キーボード入力のしくみ](../../../docs/framework/winforms/how-keyboard-input-works.md)」を参照してください。  
  
 上の 3 つのキーボード イベントに関する説明を次の表に示します。  
  
|キーボード イベント|説明|結果|  
|----------------|--------|--------|  
|<xref:System.Windows.Forms.Control.KeyDown>|このイベントは、ユーザーが物理キーを押すと発生します。|<xref:System.Windows.Forms.Control.KeyDown> のハンドラーは、次の項目を受け取ります。<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs> パラメーター。このパラメーターは、物理キーボード ボタンを示す <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> プロパティを提供します。</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> プロパティ \(Shift、Ctrl、または Alt キー\)。</li><li><xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> プロパティ \(キー コードと修飾子を組み合わせます\)。  また、<xref:System.Windows.Forms.KeyEventArgs> パラメーターは、次のプロパティを提供します。<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs.Handled%2A> プロパティ。基となるコントロールがキーを受け取らないように設定できます。</li><li><xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> プロパティ。これを使用すると、特定のキーストロークで <xref:System.Windows.Forms.Control.KeyPress> イベントと <xref:System.Windows.Forms.Control.KeyUp> イベントが発生しないようにすることができます。</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyPress>|このイベントは、1 つまたは複数のキーを押すことにより文字が出力された場合に発生します。  たとえば、Shift キーを押しながら小文字の "a" キーを押すと、大文字の "A" が出力されます。|<xref:System.Windows.Forms.Control.KeyPress> は、<xref:System.Windows.Forms.Control.KeyDown> の後に発生します。<br /><br /> <ul><li><xref:System.Windows.Forms.Control.KeyPress> のハンドラーは、次の項目を受け取ります。</li><li><xref:System.Windows.Forms.KeyPressEventArgs> パラメーター。このパラメーターには、押したキーの文字コードが入ります。  この文字コードは、文字キーと修飾子キーの組み合わせごとに一意です。<br /><br />     たとえば、"A" キーは次の文字コードを生成します。<br /><br /> <ul><li>文字コード 65 \(Shift キーまたは Caps Lock キーと一緒に押した場合\)</li><li>97 \(単独で押した場合\)</li><li>1 \(Ctrl キーと一緒に押した場合\)</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyUp>|このイベントは、ユーザーが物理キーを離すと発生します。|<xref:System.Windows.Forms.Control.KeyUp> のハンドラーは、次の項目を受け取ります。<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs> パラメーターの値。次のプロパティを提供します。<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> プロパティ \(物理キーボード ボタンを示します\)。</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> プロパティ \(Shift、Ctrl、または Alt キー\)。</li><li><xref:System.Globalization.SortKey.KeyData%2A> プロパティ \(キー コードと修飾子を組み合わせます\)。</li></ul></li></ul>|  
  
## 参照  
 [Windows フォーム アプリケーションにおけるキーボード入力](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)   
 [キーボード入力のしくみ](../../../docs/framework/winforms/how-keyboard-input-works.md)   
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)