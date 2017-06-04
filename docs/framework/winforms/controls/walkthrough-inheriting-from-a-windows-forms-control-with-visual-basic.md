---
title: "チュートリアル : Visual Basic による Windows フォーム コントロールからの継承 | Microsoft Docs"
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
  - "継承, control"
  - "継承, カスタム コントロール"
  - "継承, チュートリアル"
  - "Windows フォーム コントロール, 継承"
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# チュートリアル : Visual Basic による Windows フォーム コントロールからの継承
[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] では、*継承*によって強力なカスタム コントロールを作成できます。  継承を使用すると、標準の Windows フォーム コントロールの固有の機能をすべて保持しながら、カスタム機能も組み込んだコントロールを作成できます。  このチュートリアルでは、`ValueButton` という名前の簡単な継承コントロールを作成します。  このボタンは、標準の Windows フォーム <xref:System.Windows.Forms.Button> コントロールの機能を継承し、`ButtonValue` というカスタム プロパティを公開します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 新しいプロジェクトを作成するときには、その名前を指定することにより、ルート名前空間、アセンブリ名、およびプロジェクト名を設定し、既定のコンポーネントが正しい名前空間に含まれるようにします。  
  
#### ValueButtonLib コントロール ライブラリおよび ValueButton コントロールを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックして **\[新しいプロジェクト\]** ダイアログ ボックスを開きます。  
  
2.  \[[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] プロジェクト\] ボックスの一覧の **\[Windows フォーム コントロール ライブラリ\]** プロジェクト テンプレートを選択し、**\[プロジェクト名\]** ボックスに「`ValueButtonLib`」と入力します。  
  
     プロジェクト名 `ValueButtonLib` は、既定でルート名前空間にも割り当てられます。  ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。  たとえば、`ValueButton` という名前のコンポーネントが 2 つのアセンブリに含まれる場合は、`ValueButtonLib.ValueButton` という形で目的の `ValueButton` コンポーネントを指定できます。  詳細については、「[Visual Basic における名前空間](../Topic/Namespaces%20in%20Visual%20Basic.md)」を参照してください。  
  
3.  **ソリューション エクスプローラー**で、**\[UserControl1.vb\]** を右クリックし、ショートカット メニューの **\[名前の変更\]** をクリックします。  ファイル名を「`ValueButton.vb`」に変更します。  コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかを確認するダイアログ ボックスが表示されたら、**\[はい\]** をクリックします。  
  
4.  **ソリューション エクスプローラー**の **\[すべてのファイルを表示\]** をクリックします。  
  
5.  **\[ValueButton.vb\]** ノードを開き、デザイナー生成のコード ファイルである **ValueButton.Designer.vb** を表示します。  **コード エディター**でこのファイルを開きます。  
  
6.  `Class` ステートメント、`Partial Public Class ValueButton` を検索し、このコントロールが継承した型を <xref:System.Windows.Forms.UserControl> から <xref:System.Windows.Forms.Button> に変更します。  これによって、継承されたコントロールは <xref:System.Windows.Forms.Button> コントロールのすべての機能を継承できます。  
  
7.  `InitializeComponent` メソッドを見つけ、<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> プロパティを割り当てる行を削除します。  このプロパティは、<xref:System.Windows.Forms.Button> コントロールには存在しません。  
  
8.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックしてプロジェクトを保存します。  
  
     ビジュアル デザイナーは使用できなくなりました。  <xref:System.Windows.Forms.Button> コントロールは独自の描画を実行するため、デザイナーでは表示を変更できません。  ビジュアル表示は、コードで変更しない限り、継承元のクラス \(つまり、<xref:System.Windows.Forms.Button>\) とまったく同じです。  
  
> [!NOTE]
>  UI 要素のないコンポーネントをデザイン サーフェイスに追加することはできます。  
  
## 継承したコントロールへのプロパティの追加  
 継承した Windows フォーム コントロールの可能な用途の 1 つとして、標準の Windows フォーム コントロールと同じ外観と操作性を持ちながらカスタム プロパティを公開するコントロールを作成できます。  ここでは、コントロールに `ButtonValue` という名前のプロパティを追加します。  
  
#### Value プロパティを追加するには  
  
1.  **ソリューション エクスプローラー**で、**\[ValueButton.vb\]** を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  `Public Class ValueButton` ステートメントを探します。  このステートメントの直後に、次のコードを追加します。  
  
     \[Visual Basic\]  
  
    ```  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     このコードは、`ButtonValue` プロパティの格納方法と取得方法を設定します。  `Get` ステートメントは、返された値をプライベート変数 `varValue` に格納されている値に設定します。`Set` ステートメントは、`Value` キーワードを使用してプライベート変数の値を設定します。  
  
3.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックしてプロジェクトを保存します。  
  
## コントロールのテスト  
 コントロールはスタンドアロン プロジェクトではないため、コンテナーでホストする必要があります。  コントロールをテストするには、コントロールを実行するテスト プロジェクトを指定する必要があります。  また、コントロールをビルド \(コンパイル\) してテスト プロジェクトからもアクセスできるようにする必要があります。  ここでは、コントロールを作成し、Windows フォームでそのコントロールをテストします。  
  
#### コントロールをビルドするには  
  
1.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
     ビルドは、コンパイル エラーも警告もなしに完了します。  
  
#### テスト プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューの **\[追加\]** をポイントし、**\[新しいプロジェクト\]** をクリックして **\[新しいプロジェクトの追加\]** ダイアログ ボックスを表示します。  
  
2.  [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] プロジェクト ノードを選択し、**\[Windows フォーム アプリケーション\]** をクリックします。  
  
3.  **\[プロジェクト名\]** ボックスに「`Test`」と入力します。  
  
4.  **ソリューション エクスプローラー**の **\[すべてのファイルを表示\]** をクリックします。  
  
5.  **ソリューション エクスプローラー**で、テスト プロジェクトの **\[参照設定\]** ノードを右クリックし、ショートカット メニューの **\[参照の追加\]** をクリックして **\[参照の追加\]** ダイアログ ボックスを表示します。  
  
6.  **\[プロジェクト\]** タブをクリックします。  
  
7.  **\[プロジェクト\]** タブをクリックします。  `ValueButtonLib` プロジェクトが **\[プロジェクト名\]** の下に表示されます。  プロジェクトをダブルクリックしてテスト プロジェクトへの参照を追加します。  
  
8.  **ソリューション エクスプローラー**で、**\[Test\]** を右クリックし、**\[ビルド\]** をクリックします。  
  
#### フォームにコントロールを追加するには  
  
1.  **ソリューション エクスプローラー**で、**\[Form1.vb\]** を右クリックし、ショートカット メニューの **\[デザイナーの表示\]** をクリックします。  
  
2.  **ツールボックス**の **\[ValueButtonLib コンポーネント\]** をクリックします。  **\[ValueButton\]** をダブルクリックします。  
  
     **ValueButton** がフォームに表示されます。  
  
3.  **\[ValueButton\]** を右クリックし、ショートカット メニューの **\[プロパティ\]** をクリックします。  
  
4.  **\[プロパティ\]** ウィンドウで、このコントロールのプロパティを調べます。  標準のボタンによって公開されるのと同じプロパティの他に、追加のプロパティ `ButtonValue` が含まれています。  
  
5.  `ButtonValue` プロパティを `5` に設定します。  
  
6.  **ツールボックス**の **\[すべての Windows フォーム\]** タブで、**\[Label\]** をダブルクリックしてフォームに <xref:System.Windows.Forms.Label> コントロールを追加します。  
  
7.  ラベルをフォームの中央に配置し直します。  
  
8.  `ValueButton1` をダブルクリックします。  
  
     **コード エディター**が開き、`ValueButton1_Click` イベントが表示されます。  
  
9. 次のコード行を入力します。  
  
     \[Visual Basic\]  
  
    ```  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. **ソリューション エクスプローラー**で、**\[Test\]** を右クリックし、ショートカット メニューの **\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
11. **\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。  
  
     `Form1` が表示されます。  
  
12. \[`Valuebutton1`\] をクリックします。  
  
     `Label1` に数字 "5" が表示され、継承したコントロールの `ButtonValue` プロパティが `ValueButton1_Click` メソッドを介して `Label1` に渡されたことを示します。  このようにして、`ValueButton` コントロールは標準の Windows フォーム ボタンの機能をすべて継承しながら、追加のカスタム プロパティを公開します。  
  
## 参照  
 [チュートリアル : Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [方法: \[ツールボックス アイテムの選択\] ダイアログ ボックスにコントロールを表示する](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/ja-jp/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)