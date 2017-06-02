---
title: "方法 : コマンド ラインから Windows フォーム アプリケーションを作成する | Microsoft Docs"
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
  - "Windows フォーム, アプリケーション開発 (コマンド ラインからの)"
  - "Windows フォーム, 作成 (基本フォームを)"
  - "Windows フォーム, はじめに"
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : コマンド ラインから Windows フォーム アプリケーションを作成する
次の手順では、コマンドラインから Windows フォーム アプリケーションを作成して実行するために完了する必要のある基本的な手順について説明します。  Visual Studio では、これらの手順に対する広範なサポートが用意されています。  「[チュートリアル : 簡単な Windows フォームの作成](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.110\))」も参照してください。  
  
## プロシージャ  
  
#### フォームを作成するには  
  
1.  空のコード ファイルに、次の import ステートメントまたは using ステートメントを入力します。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  フォーム クラスから継承する `Form1` という名前のクラスを宣言します。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  `Form1` の既定のコンストラクターを作成します。  
  
     後続の手順で、コンストラクターにさらにコードを追加します。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  `Main` メソッドをクラスに追加します。  
  
    1.  <xref:System.STAThreadAttribute> を `Main` メソッドに適用し、Windows フォーム アプリケーションがシングル スレッド アパートメントであることを指定します。  
  
    2.  <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> を呼び出して、アプリケーションを Windows XP の外観にします。  
  
    3.  フォームのインスタンスを作成して実行します。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### アプリケーションをコンパイルして実行するには  
  
1.  .NET Framework コマンド プロンプトで、`Form1` クラスを作成したディレクトリに移動します。  
  
2.  フォームをコンパイルします。  
  
    -   C\# を使用している場合は、`csc form1.cs` と入力します。  
  
         `または`  
  
    -   Visual Basic を使用している場合は、`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll` と入力します。  
  
3.  コマンド プロンプトで、`Form1.exe` と入力します。  
  
## コントロールの追加とイベントの処理  
 前の手順は、コンパイルして実行する基本的な Windows フォームを作成する方法を示しました。  次の手順では、コントロールを作成してフォームに追加し、コントロールのイベントを処理する方法を示します。  Windows フォームに追加できるコントロールの詳細については、「[Windows フォーム コントロール](../../../docs/framework/winforms/controls/index.md)」を参照してください。  
  
 Windows フォーム アプリケーションを作成する方法を理解するだけでなく、イベント ベースのプログラミングとユーザー入力を処理する方法を理解する必要があります。  詳細については、「[Windows フォーム内でのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)」および「[ユーザーの入力の処理](../../../docs/framework/winforms/controls/handling-user-input.md)」を参照してください。  
  
#### ボタン コントロールを宣言して、クリック イベントを処理するには  
  
1.  `button1` という名前のボタン コントロールを宣言します。  
  
2.  コンストラクターでボタンを作成し、<xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A>、および <xref:System.Windows.Forms.Control.Text%2A> の各プロパティを設定します。  
  
3.  フォームにボタンを追加します。  
  
     次のコード例は、ボタン コントロールを宣言する方法を示します。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  ボタンで <xref:System.Windows.Forms.Control.Click> イベントを処理するメソッドを作成します。  
  
5.  クリック イベント ハンドラーで、メッセージ "Hello World" と共に <xref:System.Windows.Forms.MessageBox> を表示します。  
  
     次のコード例は、ボタン コントロールのクリック イベントを処理する方法を示します。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <xref:System.Windows.Forms.Control.Click> イベントを作成したメソッドに関連付けます。  
  
     次のコード例は、イベントをメソッドに関連付ける方法を示します。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  前の手順で説明したように、アプリケーションをコンパイルして実行します。  
  
## 使用例  
 次のコード例は、前の手順の完全な例です。  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## コードのコンパイル  
  
-   コードをコンパイルするには、アプリケーションをコンパイルして実行する方法を説明した、前述の手順に従います。  
  
## 参照  
 <xref:System.Windows.Forms.Form>   
 <xref:System.Windows.Forms.Control>   
 [Windows フォームの表示形式の変更](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)   
 [Windows フォーム アプリケーションの拡張](../../../docs/framework/winforms/advanced/index.md)   
 [Windows フォームについて](../../../docs/framework/winforms/getting-started-with-windows-forms.md)