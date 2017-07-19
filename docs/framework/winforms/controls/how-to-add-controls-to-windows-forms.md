---
title: "方法 : Windows フォームにコントロールを追加する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 追加"
  - "Windows フォーム コントロール, 追加 (フォームに)"
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームにコントロールを追加する
ほとんどのフォームは、フォームにコントロールを追加してユーザー インターフェイス \(UI\) を定義することによってデザインします。  *コントロール*は、情報の表示やユーザー入力の受け入れに使用する、フォーム上のコンポーネントです。  コントロールの詳細については、「[Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### フォームにコントロールを描画するには  
  
1.  フォームを開きます。  詳細については、「[How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/ja-jp/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)」を参照してください。  
  
2.  **ツールボックス**で、フォームに追加するコントロールをクリックします。  
  
3.  フォーム内で、コントロールの左上隅となる位置をクリックし、コントロールの右下隅となる位置までドラッグします。  
  
     指定したフォームの位置に、指定したサイズのコントロールが追加されます。  
  
    > [!NOTE]
    >  各コントロールには、既定のサイズが定義されています。  **ツールボックス**からフォームにコントロールをドラッグすると、既定のサイズのフォームを追加できます。  
  
### フォームにコントロールをドラッグするには  
  
1.  フォームを開きます。  詳細については、「[How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/ja-jp/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)」を参照してください。  
  
2.  **ツールボックス**で、必要なコントロールをクリックし、フォームにドラッグします。  
  
     指定したフォームの位置に、既定のサイズのコントロールが追加されます。  
  
    > [!NOTE]
    >  **ツールボックス**でコントロールをダブルクリックすると、フォームの左上隅に既定のサイズのコントロールを追加できます。  
  
     実行時に、フォームにコントロールを動的に追加することもできます。  次のコード例では、<xref:System.Windows.Forms.Button> コントロールをクリックしたときに、フォームに <xref:System.Windows.Forms.TextBox> コントロールが追加されるように設定します。  
  
    > [!NOTE]
    >  次のプロシージャでは、**\[Button\]** コントロールである `Button1` が既に配置されているフォームが必要です。  
  
### プログラムによって、フォームにコントロールを追加するには  
  
1.  フォームのクラスでボタンの `Click` イベントを処理するメソッドに、次のようなコードを挿入して、制御変数への参照を追加します。コントロールの `Location` を設定し、コントロールを追加します。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  コントロールの他のプロパティを初期化するコードを追加することもできます。  
  
    > [!IMPORTANT]
    >  悪意のある `UserControl` を参照することにより、ローカル コンピューターがネットワークを通じてセキュリティ上のリスクを負う可能性があります。  このことが問題になるのは、悪意のあるユーザーが有害なカスタム コントロールを作成していて、開発者が自分のプロジェクトに誤ってそれを追加してしまった場合です。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [方法 : Windows フォーム上のコントロールのサイズを変更する](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)   
 [方法 : Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)