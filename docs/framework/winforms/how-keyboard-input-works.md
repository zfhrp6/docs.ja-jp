---
title: "キーボード入力のしくみ | Microsoft Docs"
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
  - "キーボード入力, キーボード入力の概要"
  - "キーボード, キーボード入力"
  - "Windows フォーム, キーボード入力"
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# キーボード入力のしくみ
Windows フォームは、Windows メッセージに応答してキーボード イベントを発生させることにより、キーボード入力を処理します。  多くの Windows フォーム アプリケーションは、キーボード イベントを処理することによってキーボード入力を排他的に処理します。  しかし、高度なキーボード入力のシナリオ \(キーがコントロールに到達する前にキーを受け取るなど\) を実装するためには、キーボード メッセージのしくみについて理解することが必要です。  このトピックでは Windows フォームが認識するキー データの種類について説明し、キーボード メッセージをルーティングする方法について概要を説明します。  キーボード イベントの詳細については、「[キーボード イベントの使用](../../../docs/framework/winforms/using-keyboard-events.md)」を参照してください。  
  
## キーの種類  
 Windows フォームはキーボード入力を、ビット単位の <xref:System.Windows.Forms.Keys> 列挙値で表現される仮想キー コードとして識別します。  <xref:System.Windows.Forms.Keys> 列挙値を使用すると、入力された一連のキーを組み合わせて単一の値にできます。  これらの値は WM\_KEYDOWN および WM\_SYSKEYDOWN の Windows メッセージに付随する値になります。  ほとんどの物理的なキー入力は、<xref:System.Windows.Forms.Control.KeyDown> イベントまたは <xref:System.Windows.Forms.Control.KeyUp> イベントを処理することで検出できます。  文字キーは <xref:System.Windows.Forms.Keys> 列挙値のサブセットであり、WM\_CHAR および WM\_SYSCHAR の Windows メッセージに付随する値になります。  キー入力の組み合わせが文字になった場合は、<xref:System.Windows.Forms.Control.KeyPress> イベントを処理することでその文字を検出できます。  または、Visual Basic プログラミング インターフェイスによって公開される <xref:Microsoft.VisualBasic.Devices.Keyboard> を使用して、どのキーが押されたかの判断と、キーの送信を行うという方法もあります。  詳細については、「[Accessing the Keyboard](../Topic/Accessing%20the%20Keyboard%20\(Visual%20Basic\).md)」を参照してください。  
  
## キーボード イベントの順序  
 先に説明したとおり、コントロール上では 3 つのキーボード関連のイベントが発生します。  イベントは一般に次の順序で発生します。  
  
1.  ユーザーが "a" のキーを押すと、キーが前処理され、ディスパッチされて、<xref:System.Windows.Forms.Control.KeyDown> イベントが発生します。  
  
2.  ユーザーが "a" のキーを押し続けると、キーが前処理され、ディスパッチされて、<xref:System.Windows.Forms.Control.KeyPress> イベントが発生します。  
  
     このイベントはユーザーがキーを押し続けているとき複数回発生します。  
  
3.  ユーザーが "a" のキーを離すと、キーが前処理され、ディスパッチされて、<xref:System.Windows.Forms.Control.KeyUp> イベントが発生します。  
  
## キーの前処理  
 他のメッセージと同様に、キーボード メッセージもフォームやコントロールの <xref:System.Windows.Forms.Control.WndProc%2A> メソッドで処理されます。  ただし、キーボード メッセージが処理される前に、<xref:System.Windows.Forms.Control.PreProcessMessage%2A> メソッドが 1 つ以上のメソッドを呼び出します。これらのメソッドをオーバーライドすることで、特別な文字キーと物理キーの処理が可能になります。  これらのメソッドをオーバーライドすると、コントロールがメッセージを処理する前に、特定のキーを検出してフィルターできます。  次の表に、実行される処理と、そのとき呼び出されるメソッドを \(メソッドが呼び出される順に\) 示します。  
  
### KeyDown イベントの前処理  
  
|動作|メソッド|説明|  
|--------|----------|--------|  
|アクセラレータやメニュー ショートカットなどのコマンド キーの確認。|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|このメソッドはコマンド キーを処理します。コマンド キーは通常のキーよりも優先順位が上です。  このメソッドが `true` を返した場合、キー メッセージはディスパッチされず、キー イベントも発生しません。  `false` を返した場合は、<xref:System.Windows.Forms.Control.IsInputKey%2A> が呼び出されます。|  
|前処理を必要とする特別なキーか、または <xref:System.Windows.Forms.Control.KeyDown> イベントを発生させ、コントロールにディスパッチされる通常の文字キーかどうかの確認。|<xref:System.Windows.Forms.Control.IsInputKey%2A>|メソッドが `true` を返した場合は、コントロールが通常の文字であることを意味するため、<xref:System.Windows.Forms.Control.KeyDown> イベントが発生します。  `false` を返した場合は、<xref:System.Windows.Forms.Control.ProcessDialogKey%2A> が呼び出されます。 **Note:**  コントロールがキーまたはキーの組み合わせを確実に取得するためには、<xref:System.Windows.Forms.Control.PreviewKeyDown> イベントを処理し、そのキーの <xref:System.Windows.Forms.PreviewKeyDownEventArgs> の <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> に `true` を設定します。|  
|移動キー \(Esc、Tab、Return、または方向キー\) の確認。|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|このメソッドはコントロール内で特別な機能 \(コントロールとその親コントロールの間のフォーカスの切り替えなど\) を実行する物理キーを処理します。  このコントロールがキーを処理しない場合は、親コントロールで <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> が呼び出されます。それでも処理しなければ、コントロールの呼び出しが階層構造の最上階のコントロールまで続けられます。  このメソッドが `true` を返した場合、前処理は完了し、キー イベントは生成されません。  `false` を返した場合は、<xref:System.Windows.Forms.Control.KeyDown> イベントが発生します。|  
  
### KeyPress イベントの前処理  
  
|動作|メソッド|説明|  
|--------|----------|--------|  
|キーがコントロールによって処理される通常の文字であるかどうかの確認|<xref:System.Windows.Forms.Control.IsInputChar%2A>|文字が通常の文字である場合は、このメソッドが `true` を返し、<xref:System.Windows.Forms.Control.KeyPress> イベントが発生します。それ以上の処理は行われません。  通常の文字でない場合は、<xref:System.Windows.Forms.Control.ProcessDialogChar%2A> が呼び出されます。|  
|文字がニーモニック \(ボタン上の &OK など\) かどうかの確認|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|このメソッドも <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> と同様に、コントロールの階層構造を上に移動しながら呼び出されます。  コントロールがコンテナー コントロールである場合は、自身とその子コントロールから <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> を呼び出すことによってニーモニックを確認します。  <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> が `true` を返した場合、<xref:System.Windows.Forms.Control.KeyPress> イベントは発生しません。|  
  
## キーボード メッセージの処理  
 キーボード メッセージは、フォームまたはコントロールの <xref:System.Windows.Forms.Control.WndProc%2A> メソッドに到達した後、オーバーライド可能な一連のメソッドによって処理されます。  これらの各メソッドは、キーボード メッセージが処理され、コントロールがそれを使用したかどうかを示す <xref:System.Boolean> 値を返します。  いずれかのメソッドが `true` を返した場合は、メッセージが処理されたと判断されるため、ベース コントロールまたは親コントロールにメッセージが渡されることはありません。  そうでない場合は、メッセージがメッセージ キューに残り、場合によってはそのコントロールのベースまたは親に含まれる別のメソッドで処理されます。  次の表に、キーボード メッセージを処理するメソッドを示します。  
  
|メソッド|説明|  
|----------|--------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|このメソッドは、コントロールの <xref:System.Windows.Forms.Control.WndProc%2A> メソッドが受信するすべてのキーボード メッセージを処理します。|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|このメソッドは、キーボード メッセージを親コントロールに送信します。  <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> が `true` を返した場合、キー イベントは生成されません。そうでない場合は <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> が呼び出されます。|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|このメソッドは必要に応じて <xref:System.Windows.Forms.Control.KeyDown>、<xref:System.Windows.Forms.Control.KeyPress>、および <xref:System.Windows.Forms.Control.KeyUp> のイベントを発生させます。|  
  
## キーボード メソッドのオーバーライド  
 キーボード メッセージを処理するためにオーバーライドできるメソッドは多数ありますが、どのメソッドを選ぶかが非常に重要です。  次の表に、実行するタスクと、キーボード メソッドをオーバーライドする最善の方法を示します。  メソッドのオーバーライドの詳細については、「[NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)」を参照してください。  
  
|タスク|メソッド|  
|---------|----------|  
|移動キーを受け取って <xref:System.Windows.Forms.Control.KeyDown> イベントを発生させる。  たとえば、テキスト ボックス内で Tab や Return を処理するなど。|<xref:System.Windows.Forms.Control.IsInputKey%2A> をオーバーライドします。 **Note:**  または、<xref:System.Windows.Forms.Control.PreviewKeyDown> イベントを処理し、そのキーの <xref:System.Windows.Forms.PreviewKeyDownEventArgs> の <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> に `true` を設定します。|  
|コントロールで特別な入力処理や移動処理を実行する。  たとえば、リスト コントロールで方向キーを使用して選択項目を変更するなど。|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A> をオーバーライドします。|  
|移動キーを受け取って <xref:System.Windows.Forms.Control.KeyPress> イベントを発生させる。  たとえば、スピン ボックス コントロールで方向キーを複数回押して、項目の移動を加速するなど。|<xref:System.Windows.Forms.Control.IsInputChar%2A> をオーバーライドします。|  
|<xref:System.Windows.Forms.Control.KeyPress> イベントの間に、特別な入力処理や移動処理を実行する。  たとえば、リスト コントロール内で "r" キーを押し続けると、r の文字で始まる項目にスキップするなど。|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A> をオーバーライドします。|  
|カスタムなニーモニックの処理を実行する。たとえば、ツール バーに配置されたオーナー描画ボタンのニーモニックを処理するなど。|<xref:System.Windows.Forms.Control.ProcessMnemonic%2A> をオーバーライドします。|  
  
## 参照  
 <xref:System.Windows.Forms.Keys>   
 <xref:System.Windows.Forms.Control.WndProc%2A>   
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>   
 [My.Computer.Keyboard Object](../../../ocs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)   
 [Accessing the Keyboard](../Topic/Accessing%20the%20Keyboard%20\(Visual%20Basic\).md)   
 [キーボード イベントの使用](../../../docs/framework/winforms/using-keyboard-events.md)