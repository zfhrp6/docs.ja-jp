---
title: "方法 : Windows フォームにコントロールを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab92f7a56173ec71642d0cc09f3f81e9859533b4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-to-windows-forms"></a>方法 : Windows フォームにコントロールを追加する
ほとんどのフォームは、フォームのサーフェイスにコントロールを追加してユーザー インターフェイス (UI) を定義するよう設計されています。 A*コントロール*情報の表示や、ユーザー入力をそのまま使用するために使用するフォームのコンポーネントは、します。 コントロールの詳細については、次を参照してください。 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-draw-a-control-on-a-form"></a>フォーム上のコントロールを描画するには  
  
1.  フォームを開きます。 詳細については、次を参照してください。[する方法: デザイナーでの Windows フォームの表示](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)です。  
  
2.  **ツールボックス**フォームに追加するコントロールをクリックします。  
  
3.  フォームに存在するコントロールの左上隅をクリックしを配置するコントロールの右下隅の任意の場所にドラッグします。  
  
     コントロールは、指定した位置とサイズでフォームに追加されます。  
  
    > [!NOTE]
    >  各コントロールには、定義されている既定のサイズがあります。 ドラッグして、コントロールの既定のサイズで、フォームにコントロールを追加することができます、**ツールボックス**をフォームにします。  
  
### <a name="to-drag-a-control-to-a-form"></a>コントロールをフォームにドラッグするには  
  
1.  フォームを開きます。 詳細については、次を参照してください。[する方法: デザイナーでの Windows フォームの表示](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)です。  
  
2.  **ツールボックス**フォームにドラッグしてコントロールをクリックします。  
  
     コントロールは、既定のサイズで指定した場所にあるフォームに追加されます。  
  
    > [!NOTE]
    >  内のコントロールをダブルクリックすることができます、**ツールボックス**を既定のサイズで、フォームの左上隅に追加します。  
  
     実行時に、フォームにコントロールを動的に追加することができますも。 次のコード例で、<xref:System.Windows.Forms.TextBox>コントロールは、フォームに追加するときに、<xref:System.Windows.Forms.Button>コントロールがクリックされました。  
  
    > [!NOTE]
    >  次の手順が必要ですがあるフォーム、**ボタン**コントロール、`Button1`に既に配置されている、します。  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>プログラムによってコントロールをフォームに追加するには  
  
1.  ボタンの処理をメソッドで`Click`フォームのクラスを制御変数への参照を追加するには、次のような挿入コード内のイベント設定コントロールの`Location`、し、コントロールを追加します。  
  
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
    >  悪意のあるを参照して、ローカル コンピューターがネットワーク経由のセキュリティ リスクを公開する可能性があります`UserControl`です。 誤ってそれをプロジェクトに追加した後に、有害なカスタム コントロールを作成する悪意のあるユーザーの場合は問題にならなければのみとなります。  
  
## <a name="see-also"></a>参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)  
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [方法: Windows フォーム上のコントロールのサイズを変更する](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [方法: Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
