---
title: "方法 : 既存の Windows フォーム コントロールから継承する"
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
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb50e5b301095cce72e59dc2899d44a47215b536
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>方法 : 既存の Windows フォーム コントロールから継承する
既存のコントロールの機能を拡張する場合は、継承によって既存のコントロールから派生したコントロールを作成できます。 既存のコントロールから継承すると、そのコントロールのすべての機能およびビジュアル プロパティが引き継がれます。 継承するコントロールを作成する場合など、 <xref:System.Windows.Forms.Button>、新しいコントロールにはなりますおよび act とまったく同じ標準<xref:System.Windows.Forms.Button>コントロール。 その後で、カスタム メソッドやカスタム プロパティの実装によって、新しいコントロールの機能を拡張または変更できます。 一部のコントロールで変更することできますも、継承されたコントロールの外観をオーバーライドしてその<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-an-inherited-control"></a>継承したコントロールを作成するには  
  
1.  新しい **Windows フォーム アプリケーション プロジェクト**を作成します。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
3.  **[新しい項目の追加]** ダイアログ ボックスの **[カスタム コントロール]** をダブルクリックします。  
  
     新しいカスタム コントロールがプロジェクトに追加されます。  
  
4.  Visual Basic を使用している場合は、**ソリューション エクスプローラー**の上部にある **[すべてのファイルを表示]** をクリックします。 CustomControl1.vb を展開し、コード エディターで CustomControl1.Designer.vb を開きます。  
  
5.  C# を使用している場合は、コード エディターで CustomControl1.cs を開きます。  
  
6.  継承されるクラス宣言を検索<xref:System.Windows.Forms.Control>です。  
  
7.  基底クラスを継承元のコントロールに変更します。  
  
     継承する場合など<xref:System.Windows.Forms.Button>、クラス宣言を次に変更します。  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Visual Basic を使用している場合は、CustomControl1.Designer.vb を保存して閉じます。 コード エディターで CustomControl1.vb を開きます。  
  
9. コントロールに組み込むカスタム メソッドやカスタム プロパティを実装します。  
  
10. コントロールの外観を変更する場合は、オーバーライド、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。  
  
    > [!NOTE]
    >  オーバーライドする<xref:System.Windows.Forms.Control.OnPaint%2A>すべてのコントロールの外観を変更することはできません。 これらのコントロールを持つすべての Windows が行う、描画 (たとえば、 <xref:System.Windows.Forms.TextBox>) 呼び出すことはありません、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド、なり、しないで使用するカスタム コード。 かどうかを変更する特定のコントロールのヘルプ ドキュメントを参照してください、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは使用できます。 すべての Windows フォーム コントロールの一覧については、「[Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)」を参照してください。 コントロールがない場合<xref:System.Windows.Forms.Control.OnPaint%2A>メンバー メソッドとして一覧に表示できない外観を変更するこのメソッドをオーバーライドしています。 カスタム描画の詳細については、「[コントロールのカスタム描画およびレンダリング](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)」を参照してください。  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. コントロールを保存して、動作確認を行います。  
  
## <a name="see-also"></a>参照  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [方法: コントロール クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [方法: UserControl クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [方法: Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [チュートリアル: Visual Basic による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [チュートリアル: Visual C# による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
