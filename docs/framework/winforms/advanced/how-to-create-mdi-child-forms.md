---
title: "方法 : MDI 子フォームを作成する | Microsoft Docs"
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
  - "子フォーム"
  - "MDI, 作成 (フォームを)"
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 方法 : MDI 子フォームを作成する
MDI 子フォームは、ユーザー操作の中心であるため、[マルチ ドキュメント インターフェイス \(MDI\) アプリケーション](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)の重要な要素です。  
  
 次の手順では、ほとんどのワード プロセッシング アプリケーションに似ている <xref:System.Windows.Forms.RichTextBox> コントロールを表示する MDI 子フォームを作成します。  <xref:System.Windows.Forms> コントロールを、<xref:System.Windows.Forms.DataGridView> コントロールやコントロールを組み合わせたその他のコントロールで置き換えることで、さまざまな可能性のある MDI 子ウィンドウ \(およびその拡張としての MDI アプリケーション\) を作成できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### MDI 子フォームを作成するには  
  
1.  新しい Windows フォーム プロジェクトを作成します。  フォームの **\[プロパティ\] ウィンドウ**で、<xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定し、`WindowsState` プロパティを `Maximized` に設定します。  
  
     これによって、フォームが子ウィンドウの MDI コンテナーとして指定されます。  
  
2.  `Toolbox` から、<xref:System.Windows.Forms.MenuStrip> コントロールをフォームにドラッグします。  `Text` プロパティを **\[ファイル\]** に設定します。  
  
3.  **\[項目\]** プロパティの隣にある省略記号 \(...\) をクリックして、**\[追加\]** をクリックし、2 つの子ツール ストリップのメニュー項目を追加します。  これらの項目の `Text` プロパティを **\[新規\]** と **\[ウィンドウ\]** に設定します。  
  
4.  **\[ソリューション エクスプローラー\]** で、プロジェクトを右クリックして、**\[追加\]** をポイントし、**\[新しい項目の追加\]** を選択します。  
  
5.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[テンプレート\]** ペインから **\[Windows フォーム\]** \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 内\) または **\[Windows フォーム アプリケーション \(.NET\)\]** \([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] 内\) を選択します。  **\[名前\]** ボックスで、フォーム Form2 の名前を付けます。  **\[開く\]** ボタンをクリックして、フォームをプロジェクトに追加します。  
  
    > [!NOTE]
    >  この手順で作成した、MDI 子フォームは、標準の Windows フォームです。  そのため、フォームの透明度を制御できる <xref:System.Windows.Forms.Form.Opacity%2A> プロパティを持っています。  ただし、<xref:System.Windows.Forms.Form.Opacity%2A> プロパティは最上位レベルのウィンドウ用に設計されています。  描画に関する問題が発生する可能性があるため、MDI 子フォームと共に使用しないでください。  
  
     このフォームは、MDI 子フォーム用のテンプレートになります。  
  
     **Windows フォーム デザイナー**が開き、Form2 を表示します。  
  
6.  **\[ツールボックス\]** から、**\[RichTextBox\]** コントロールをフォームにドラッグします。  
  
7.  **\[プロパティ\]** ウィンドウで、`Anchor` プロパティを **\[上、左\]** に設定し、`Dock` プロパティを **\[塗りつぶし\]** に設定します。  
  
     これにより、フォームがサイズ変更された場合でも、<xref:System.Windows.Forms.RichTextBox> コントロールが MDI 子フォームの領域を完全に塗りつぶします。  
  
8.  **\[新規\]** メニュー項目をダブルクリックして、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成します。  
  
9. ユーザーが **\[新規\]** メニュー項目をクリックしたときに新しい MDI 子フォームを作成するには、次のようなコードを挿入します。  
  
    > [!NOTE]
    >  次の例では、イベント ハンドラーが `MenuItem2` の <xref:System.Windows.Forms.Control.Click> イベントを処理します。  アプリケーションのアーキテクチャの仕様によっては、**\[新規\]** メニュー項目が `MenuItem2` でない可能性があります。  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] で、次の `#include` ディレクティブを Form1.h の先頭に追加します。  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. **\[プロパティ\]** ウィンドウの上部にあるドロップダウンリストで、**\[ファイル\]** メニュー ストリップに該当するメニュー ストリップを選択し、<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> プロパティを Window <xref:System.Windows.Forms.ToolStripMenuItem> に設定します。  
  
     これにより、**\[ウィンドウ\]** メニューで開いている MDI 子ウィンドウと、アクティブな子ウィンドウの横にチェック マークが付いている一覧が維持されます。  
  
11. F5 キーを押してアプリケーションを実行します。  **\[ファイル\]** メニューから **\[新規\]** を選択して、**\[ウィンドウ\]** メニュー項目で追跡される新しい MDI 子フォームを作成できます。  
  
    > [!NOTE]
    >  MDI 子フォームが \(通常はメニュー項目のメニュー構造を持つ\) <xref:System.Windows.Forms.MainMenu> コンポーネントを持っていて、\(通常はメニュー項目のメニュー構造を持つ\) <xref:System.Windows.Forms.MainMenu> コンポーネントを持つ MDI 親フォーム内で開いている場合、<xref:System.Windows.Forms.MenuItem.MergeType%2A> プロパティ \(およびオプションで <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> プロパティ\) を設定した場合に、メニュー項目が自動的にマージされます。  両方の <xref:System.Windows.Forms.MainMenu> コンポーネント、および子フォームのすべてのメニュー項目の <xref:System.Windows.Forms.MenuItem.MergeType%2A> プロパティを <xref:System.Windows.Forms.MenuMerge> に設定します。  また、<xref:System.Windows.Forms.MenuItem.MergeOrder%2A> プロパティを設定し、両方のメニューのメニュー項目が指定した順序で表示されるようにします。  さらに、MDI 親フォームを閉じた時に、MDI 親の <xref:System.Windows.Forms.Form.Closing> イベントが発生する前に、各 MDI 子フォームが <xref:System.Windows.Forms.Form.Closing> イベントを発生させます。  MDI 子の <xref:System.Windows.Forms.Form.Closing> イベントをキャンセルしても、MDI 親の <xref:System.Windows.Forms.Form.Closing> イベントの発生を防ぐことはできません。ただし、MDI 親の <xref:System.Windows.Forms.Form.Closing> イベントの <xref:System.ComponentModel.CancelEventArgs> 引数は `true` に設定されます。  <xref:System.ComponentModel.CancelEventArgs> 引数を `false` に設定することで、MDI 親レポートとすべての MDI 子フォームを強制的に閉じることができます。  
  
## 参照  
 [マルチ ドキュメント インターフェイス \(MDI\) アプリケーション](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)   
 [方法 : MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [方法 : アクティブな MDI 子フォームを特定する](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)   
 [方法 : アクティブな MDI 子フォームにデータを送信する](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)   
 [方法 : MDI 子フォームを配置する](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)