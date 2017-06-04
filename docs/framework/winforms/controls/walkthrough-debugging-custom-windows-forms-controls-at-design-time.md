---
title: "チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ | Microsoft Docs"
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
  - "コントロール [Windows フォーム], デバッグ"
  - "カスタム コントロール [Windows フォーム], デバッグ"
  - "カスタム コントロール [Windows フォーム], チュートリアル"
  - "デバッグ [Visual Studio], チュートリアル"
  - "デバッグ [Visual Studio], Windows フォーム"
  - "デザイナー"
  - "デザイン時デバッグ"
  - "ビジュアル エディター"
  - "チュートリアル [Windows フォーム], デバッグ"
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ
カスタム コントロールを作成したときは、多くの場合、デザイン時動作のデバッグが必要になります。  特にカスタム コントロール用のカスタム デザイナーを作成した場合は、このようなデバッグが不可欠です。  詳細については、「[チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)」を参照してください。  
  
 カスタム コントロールは、他の .NET Framework クラスの場合と同じように Visual Studio を使用してデバッグできます。  ただし、カスタム コントロールの場合は、そのコードを実行する Visual Studio の別個のインスタンスをデバッグするという点が異なります。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   カスタム コントロールをホストする Windows フォーム プロジェクトの作成  
  
-   コントロール ライブラリ プロジェクトの作成  
  
-   カスタム コントロールへのプロパティの追加  
  
-   ホスト フォームへのカスタム コントロールの追加  
  
-   デザイン時デバッグのためのプロジェクト設定  
  
-   カスタム コントロールのデザイン時のデバッグ  
  
 ここでは、カスタム コントロールのデザイン時の動作のデバッグに必要なタスクについて理解します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 最初にアプリケーション プロジェクトを作成します。  このプロジェクトを使用して、カスタム コントロールをホストするアプリケーションをビルドします。  
  
#### プロジェクトを作成するには  
  
-   "DebuggingExample" という名前の Windows アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
## コントロール ライブラリ プロジェクトの作成  
 次に、コントロール ライブラリ プロジェクトを作成し、カスタム コントロールを設定します。  
  
#### コントロール ライブラリ プロジェクトを作成するには  
  
1.  **Windows コントロール ライブラリ** プロジェクトをソリューションに追加します。  
  
2.  新しい **UserControl** アイテムを DebugControlLibrary プロジェクトに追加します。  詳細については、「[NIB:How to: Add New Project Items](http://msdn.microsoft.com/ja-jp/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)」を参照してください。  新しいソース ファイルに、"DebugControl" という基本名を付けます。  
  
3.  **ソリューション エクスプローラー**を使用して、"`UserControl1`" という基本名のコード ファイルを削除することにより、プロジェクトの既定のコントロールを削除します。  詳細については、「[NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/ja-jp/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)」を参照してください。  
  
4.  ソリューションをビルドします。  
  
## チェックポイント  
 この時点で、カスタム コントロールが**ツールボックス**に表示されます。  
  
#### 進行状況を確認するには  
  
-   **\[DebugControlLibrary コンポーネント\]** という新しいタブを見つけ、クリックして選択します。  開いたタブには、コントロールが **\[DebugControl\]** としてリストされ、その横に既定のアイコンが表示されます。  
  
## カスタム コントロールへのプロパティの追加  
 カスタム コントロールのコードがデザイン時に動作することを示すために、プロパティを追加し、そのプロパティを実装するコードにブレークポイントを設定します。  
  
#### カスタム コントロールにプロパティを追加するには  
  
1.  **コード エディター**で **\[DebugControl\]** を開きます。  次のコードをクラス定義に追加します。  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  ソリューションをビルドします。  
  
## ホスト フォームへのカスタム コントロールの追加  
 カスタム コントロールのデザイン時動作をデバッグするには、カスタム コントロール クラスのインスタンスをホスト フォームに配置します。  
  
#### ホスト フォームにカスタム コントロールを追加するには  
  
1.  "DebuggingExample" プロジェクトの Form1 を **Windows フォーム デザイナー**で開きます。  
  
2.  **\[ツールボックス\]** の **\[DebugControlLibrary コンポーネント\]** タブを開き、**\[DebugControl\]** インスタンスをフォームにドラッグします。  
  
3.  **\[プロパティ\]** ウィンドウで `DemoString` カスタム プロパティを見つけます。  このプロパティの値は、他のプロパティと同じように変更できます。  また、`DemoString` プロパティを選択すると、**\[プロパティ\]** ウィンドウの下部にプロパティの説明文字列が表示されます。  
  
## デザイン時デバッグのためのプロジェクト設定  
 カスタム コントロールのデザイン時動作をデバッグするには、カスタム コントロールのコードを実行する Visual Studio の別個のインスタンスをデバッグします。  
  
#### デザイン時デバッグのためにプロジェクトを設定するには  
  
1.  **ソリューション エクスプローラー**で、**\[DebugControlLibrary\]** プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **DebugControlLibrary** プロパティ シートの **\[デバッグ\]** タブをクリックします。  
  
     **\[開始動作\]** セクションで、**\[外部プログラムの開始\]** を選択します。  Visual Studio の別個のインスタンスをデバッグするので、省略記号 \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックして、Visual Studio IDE を参照します。  実行可能ファイルの名前は **devenv.exe** で、既定の場所にインストールした場合、ファイルのパスは "%programfiles%\\Microsoft Visual Studio 9.0\\Common7\\IDE\\devenv.exe" になります。  
  
3.  **\[OK\]** をクリックし、ダイアログ ボックスを閉じます。  
  
4.  **\[DebugControlLibrary\]** プロジェクトを右クリックし、**\[スタートアップ プロジェクトに設定\]** をクリックして、このデバッグ構成を有効にします。  
  
## カスタム コントロールのデザイン時のデバッグ  
 これで、カスタム コントロールをデザイン モードで実行しながらデバッグする準備ができました。  デバッグ セッションを開始すると、Visual Studio の新しいインスタンスが作成され、それを使って "DebuggingExample" ソリューションを読み込みます。  **フォーム デザイナー**で Form1 を開くと、カスタム コントロールのインスタンスが作成され、実行を開始します。  
  
#### カスタム コントロールをデザイン時にデバッグするには  
  
1.  **コード エディター**で **\[DebugControl\]** ソース ファイルを開き、`DemoString` プロパティの `Set` アクセサーにブレークポイントを配置します。  
  
2.  F5 キーを押してデバッグ セッションを開始します。  Visual Studio の新しいインスタンスが作成されることを確認してください。  各インスタンスは、次の 2 つの方法で識別できます。  
  
    -   デバッグ インスタンスのタイトル バーには、"**実行中**" という単語が表示されます。  
  
    -   デバッグ インスタンスの **\[デバッグ\]** ツール バーの **\[開始\]** ボタンは無効になります。  
  
     デバッグ インスタンスにブレークポイントが設定されます。  
  
3.  Visual Studio の新しいインスタンスで、"DebuggingExample" ソリューションを開きます。  **\[ファイル\]** メニューの **\[最近使ったプロジェクト\]** をクリックすると、ソリューションが簡単に見つかります。  "DebuggingExample.sln" ソリューション ファイルが、最後に使用したファイルとして表示されます。  
  
4.  **フォーム デザイナー**で Form1 を開き、**\[DebugControl\]** コントロールを選択します。  
  
5.  `DemoString` プロパティの値を変更します。  変更をコミットすると、Visual Studio のデバッグ インスタンスがフォーカスを取得し、ブレークポイントで実行が停止します。  プロパティ アクセサーは、他のコードと同じようにシングル ステップ実行できます。  
  
6.  デバッグ セッションが終了したら、Visual Studio のホスト インスタンスを閉じるか、デバッグ インスタンスの **\[デバッグの停止\]** をクリックして終了できます。  
  
## 次の手順  
 これで、カスタム コントロールをデザイン時にデバッグできるようになりました。この後は、コントロールと Visual Studio IDE の対話をさまざまな方法で拡張できます。  
  
-   <xref:System.ComponentModel.Component> クラスの <xref:System.ComponentModel.Component.DesignMode%2A> プロパティを使用して、デザイン時にのみ動作するコードを記述できます。  詳細については、「<xref:System.ComponentModel.Component.DesignMode%2A>」を参照してください。  
  
-   カスタム コントロールとデザイナーの対話を操作するために、コントロールのプロパティに適用できる属性がいくつかあります。  これらの属性は、<xref:System.ComponentModel?displayProperty=fullName> 名前空間に含まれています。  
  
-   カスタム コントロール用のカスタム デザイナーを作成できます。  これにより、Visual Studio によって公開されている拡張性のあるデザイナー インフラストラクチャを使用して、デザイン手順を全面的に制御できます。  詳細については、「[チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)」を参照してください。  
  
## 参照  
 [チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)   
 [How to: Access Design\-Time Services](../Topic/How%20to:%20Access%20Design-Time%20Services.md)   
 [How to: Access Design\-Time Support in Windows Forms](../Topic/How%20to:%20Access%20Design-Time%20Support%20in%20Windows%20Forms.md)