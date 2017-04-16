---
title: "チュートリアル : ステータス バー情報の実行時更新 | Microsoft Docs"
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
  - "パネル, 最新表示 (ステータス バーを)"
  - "ステータス バー, 最新表示 (パネルを)"
  - "ステータス バー, 更新 (実行時に)"
  - "StatusBar コントロール [Windows フォーム], 最新表示 (パネルを)"
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# チュートリアル : ステータス バー情報の実行時更新
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> コントロールと <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールは、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールは、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
 アプリケーション状態やユーザーとの対話に応じて、実行時にステータス バー パネルの内容を更新することが必要な場合があります。  これは、**CapsLock** キー、**NumLock** キー、**ScrollLock** キーなどのキーが有効化されたことをユーザーに通知したり、日付や時刻を便利な情報として表示するためによく使用される方法です。  
  
 <xref:System.Windows.Forms.StatusBarPanel> クラスのインスタンスを使用して時計をホストする例を次に示します。  
  
### ステータス バーを更新できる状態にするには  
  
1.  新しい Windows フォームを作成します。  
  
2.  フォームに <xref:System.Windows.Forms.StatusBar> コントロールを追加します。  詳細については、「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
3.  ステータス バー パネルを <xref:System.Windows.Forms.StatusBar> コントロールに追加します。  詳細については、「[方法 : StatusBar コントロールにパネルを追加する](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)」を参照してください。  
  
4.  フォームに追加した <xref:System.Windows.Forms.StatusBar> コントロールで、<xref:System.Windows.Forms.StatusBar.ShowPanels%2A> プロパティを `true` に設定します。  
  
5.  Windows フォームの <xref:System.Windows.Forms.Timer> コンポーネントをフォームに追加します。  
  
    > [!NOTE]
    >  Windows フォームの <xref:System.Windows.Forms.Timer?displayProperty=fullName> コンポーネントは、Windows フォーム環境向けにデザインされています。  サーバー環境に適したタイマーが必要な場合は、「[Introduction to Server\-Based Timers](http://msdn.microsoft.com/ja-jp/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。  
  
6.  <xref:System.Windows.Forms.Timer.Enabled%2A> プロパティを `true` に設定します。  
  
7.  <xref:System.Windows.Forms.Timer> の <xref:System.Windows.Forms.Timer.Interval%2A> プロパティを 30000 に設定します。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer> コンポーネントの <xref:System.Windows.Forms.Timer.Interval%2A> プロパティは、正確な時間を表示時刻に反映するために、30 秒 \(30,000 ミリ秒\) に設定されます。  
  
### ステータス バーを更新するタイマーを実装するには  
  
1.  次のコードを <xref:System.Windows.Forms.Timer> コンポーネントのイベント ハンドラーに挿入して、<xref:System.Windows.Forms.StatusBar> コントロールのパネルを更新します。  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     この時点でアプリケーションを実行できる状態になるので、テータス バー パネルの時計の動作を確認します。  
  
### アプリケーションをテストするには  
  
1.  アプリケーションをデバッグし、F5 キーを押して実行します。  デバッグの詳細については、「[Visual Studio でのデバッグ](../Topic/Debugging%20in%20Visual%20Studio.md)」を参照してください。  
  
    > [!NOTE]
    >  ステータス バーに時計が表示されるまでに、約 30 秒かかります。  これは、できるだけ正確な時刻を表示するためです。  逆に、時計を早く表示するには、上の手順 7. で <xref:System.Windows.Forms.Timer.Interval%2A> プロパティの設定値を小さくします。  
  
## 参照  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [方法 : StatusBar コントロールにパネルを追加する](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)   
 [方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)   
 [StatusBar コントロールの概要](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)