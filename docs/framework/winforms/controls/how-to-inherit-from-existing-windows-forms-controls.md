---
title: "方法 : 既存の Windows フォーム コントロールから継承する | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], 継承"
  - "継承, Windows フォーム カスタム コントロール"
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : 既存の Windows フォーム コントロールから継承する
既存のコントロールの機能を拡張する場合は、継承によって既存のコントロールから派生したコントロールを作成します。  既存のコントロールから継承すると、そのコントロールのすべての機能およびビジュアル プロパティが引き継がれます。  たとえば、<xref:System.Windows.Forms.Button> から継承したコントロールを作成すると、新しいコントロールは標準の <xref:System.Windows.Forms.Button> コントロールと同じ外観を持ち、同じように機能します。  その後で、カスタム メソッドやカスタム プロパティの実装によって、新しいコントロールの機能を拡張または変更できます。  いくつかのコントロールでは、継承したコントロールの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドして、外観を変更することもできます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 継承したコントロールを作成するには  
  
1.  新しい **Windows フォーム アプリケーション** プロジェクトを作成します。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[カスタム コントロール\]** をダブルクリックします。  
  
     新しいカスタム コントロールがプロジェクトに追加されます。  
  
4.  Visual Basic を使用している場合は、**ソリューション エクスプローラー**の上部にある **\[すべてのファイルを表示\]** をクリックします。  CustomControl1.vb を展開し、コード エディターで CustomControl1.Designer.vb を開きます。  
  
5.  C\# を使用している場合は、コード エディターで CustomControl1.cs を開きます。  
  
6.  <xref:System.Windows.Forms.Control> から継承したクラス宣言を見つけます。  
  
7.  基本クラスを継承元のコントロールに変更します。  
  
     たとえば、<xref:System.Windows.Forms.Button> から継承する場合は、クラス宣言を次のように変更します。  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Visual Basic を使用している場合は、CustomControl1.Designer.vb を保存して閉じます。  コード エディターで CustomControl1.vb を開きます。  
  
9. コントロールに含めるカスタム メソッドやカスタム プロパティを実装します。  
  
10. コントロールの外観を変更する場合は、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドします。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Control.OnPaint%2A> をオーバーライドしても、すべてのコントロールの外観を変更できるわけではありません。  描画がすべて Windows によって行われるコントロール \(<xref:System.Windows.Forms.TextBox> など\) は、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドを呼び出さないため、カスタム コードを使用しません。  <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドを使用できるかどうかを確認するには、変更するコントロールのヘルプ ドキュメントを参照してください。  Windows フォーム コントロールの一覧については、「[Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)」を参照してください。  コントロールにメンバー メソッドとして <xref:System.Windows.Forms.Control.OnPaint%2A> がない場合、このメソッドをオーバーライドして外観を変更することはできません。  カスタム描画の詳細については、「[コントロールのカスタム描画およびレンダリング](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)」を参照してください。  
  
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
  
11. 保存してコントロールの動作確認を行います。  
  
## 参照  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [方法 : コントロール クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [方法 : UserControl クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [方法 : Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [チュートリアル : Visual Basic による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [チュートリアル : Visual C\# による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)