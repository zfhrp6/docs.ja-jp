---
title: "方法 : キーボード入力を標準コントロールに変更する | Microsoft Docs"
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
  - "キーボード入力, 変更"
  - "キーボード, キーボード入力"
  - "変更 (キーボード入力を)"
  - "Windows フォーム, 変更 (キーボード入力を)"
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : キーボード入力を標準コントロールに変更する
Windows フォームは、キーボードの入力を使用して変更する機能を提供します。  キーの使用とは、メッセージ キューのさらに下のその他のメソッドとイベントが、キーの値を受信しないようにメソッドまたはイベント ハンドラー内のキーを処理することを表します。  キーの変更とは、メッセージ キューのさらに下のメソッドとイベント ハンドラーが、異なるキーの値を受け取るようにキーの値を変更することを表します。  このトピックでは、これらのタスクを実行する方法について説明します。  
  
### キーを使用するには  
  
-   <xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーで、<xref:System.Windows.Forms.KeyPressEventArgs> クラスの <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> プロパティを `true` に設定します。  
  
     または  
  
     <xref:System.Windows.Forms.Control.KeyDown> イベント ハンドラーで、<xref:System.Windows.Forms.KeyEventArgs> クラスの <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> プロパティを `true` に設定します。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Control.KeyDown> イベント ハンドラーで <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> プロパティを設定すると、<xref:System.Windows.Forms.Control.KeyPress> イベントと <xref:System.Windows.Forms.Control.KeyUp> イベントが現在のキー入力から発生しないようにすることができます。  この目的には、<xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> プロパティを使用します。  
  
     次の例は、<xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーによって受信された <xref:System.Windows.Forms.KeyPressEventArgs> の <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> プロパティを検査する `switch` ステートメントの抜粋です。  このコードは、'A' と 'a' 文字のキーを使用します。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### 標準の文字のキーを変更するには  
  
-   <xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーで、<xref:System.Windows.Forms.KeyPressEventArgs> クラスの <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> プロパティを新しい文字のキーの値に設定します。  
  
     次の例は、'B' を 'A' に変更して、'b' を 'a' に変更する `switch` ステートメントの抜粋です。  <xref:System.Windows.Forms.KeyPressEventArgs> パラメーターの <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> のプロパティが `false` に設定され、新しいキーの値が、メッセージ キューの他のメソッドとイベントに反映されることに注意してください。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### 非文字キーを変更するには  
  
-   Windows メッセージを処理する <xref:System.Windows.Forms.Control> メソッドをオーバーライドして、WM\_KEYDOWN または WM\_SYSKEYDOWN のメッセージを検出し、<xref:System.Windows.Forms.Message> パラメーターの <xref:System.Windows.Forms.Message.WParam%2A> プロパティを、新しい非文字キーを表す <xref:System.Windows.Forms.Keys> 値に設定します。  
  
     次のコード例は、F1 から F9 のキーを検出して、F3 キーを押したときに F1 に変更するよう、コントロールの <xref:System.Windows.Forms.Control.PreProcessMessage%2A> メソッドをオーバーライドする方法を示しています、  キーボードのメッセージを代行受信するようにオーバーライドできる <xref:System.Windows.Forms.Control> メソッドの詳細については、「[Windows フォーム アプリケーションにおけるユーザー入力](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)」と「[キーボード入力のしくみ](../../../docs/framework/winforms/how-keyboard-input-works.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## 使用例  
 次のコード例は、前のセクションのコード例の完全なアプリケーションです。  アプリケーションは、<xref:System.Windows.Forms.TextBox> クラスから派生したカスタム コントロールを使用して、キーボードの入力を使用して変更します。  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法の詳細については、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 [Windows フォーム アプリケーションにおけるキーボード入力](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)   
 [Windows フォーム アプリケーションにおけるユーザー入力](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)   
 [キーボード入力のしくみ](../../../docs/framework/winforms/how-keyboard-input-works.md)