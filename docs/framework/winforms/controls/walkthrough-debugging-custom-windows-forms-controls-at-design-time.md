---
title: 'チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: b87c46b2182884f90b427498b9af696d14acac96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a>チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ
カスタム コントロールを作成するときに、多くの場合、必要な場合が、デザイン時の動作をデバッグします。 これは、カスタム コントロールのカスタム デザイナーを作成している場合に特に当てはまります。 詳細については、「[チュートリアル:、Windows フォーム コントロール利用の Visual Studio デザイン時の機能を作成する](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)です。  
  
 他の .NET Framework クラスをデバッグする場合と同様に、Visual Studio を使用して、カスタム コントロールをデバッグできます。 違いは、カスタム コントロールのコードを実行している Visual Studio の別のインスタンスをデバッグすることです。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   カスタム コントロールをホストする Windows フォーム プロジェクトを作成します。  
  
-   コントロール ライブラリ プロジェクトを作成します。  
  
-   カスタム コントロールにプロパティを追加します。  
  
-   ホスト フォームへのカスタム コントロールの追加  
  
-   デザイン時デバッグのためのプロジェクトの設定  
  
-   カスタム コントロールをデザイン時のデバッグ  
  
 完了したら、カスタム コントロールのデザイン時の動作をデバッグするために必要なタスクについて理解があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初の手順では、アプリケーション プロジェクトを作成します。 このプロジェクトを使用するカスタム コントロールをホストするアプリケーションをビルドします。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
-   "DebuggingExample"と呼ばれる Windows アプリケーション プロジェクトを作成します。 詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
## <a name="creating-a-control-library-project"></a>コントロール ライブラリ プロジェクトを作成します。  
 次の手順では、コントロール ライブラリ プロジェクトを作成し、カスタム コントロールを設定します。  
  
#### <a name="to-create-the-control-library-project"></a>コントロール ライブラリ プロジェクトを作成するには  
  
1.  追加、 **Windows コントロール ライブラリ**プロジェクトがソリューションにします。  
  
2.  新しい**UserControl** DebugControlLibrary プロジェクト項目です。 詳細については、「 [NIB: 方法: 新しいプロジェクト項目の追加](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)です。 新しいソース ファイルに「タブ」の基本の名前を付けます。  
  
3.  使用して、**ソリューション エクスプ ローラー**の基本名を持つコード ファイルを削除することによって、プロジェクトの既定のコントロールを削除する"`UserControl1`"です。 詳細については、「 [NIB: 方法:: 削除、削除、および項目の除外](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)です。  
  
4.  ソリューションをビルドします。  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点では、ことができますにカスタム コントロールを表示する、**ツールボックス**です。  
  
#### <a name="to-check-your-progress"></a>進行状況を確認するには  
  
-   呼ばれる新しいタブを見つける**DebugControlLibrary コンポーネント** をクリックして選択します。 開くときに、コントロールが表示されます**タブ**その横にある既定のアイコンとします。  
  
## <a name="adding-a-property-to-your-custom-control"></a>カスタム コントロールにプロパティを追加します。  
 デザイン時にカスタム コントロールのコードが実行されていることを示すためには、プロパティを追加して、プロパティを実装するコードにブレークポイントを設定します。  
  
#### <a name="to-add-a-property-to-your-custom-control"></a>カスタム コントロールにプロパティを追加するには  
  
1.  開いている**タブ**で、**コード エディター**です。 クラスの定義に次のコードを追加します。  
  
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
  
## <a name="adding-your-custom-control-to-the-host-form"></a>ホスト フォームへのカスタム コントロールの追加  
 カスタム コントロールのデザイン時の動作をデバッグするには、ホストのフォームにカスタム コントロール クラスのインスタンスを配置します。  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a>ホストのフォームにカスタム コントロールを追加するには  
  
1.  プロジェクトで、"DebuggingExample"で、Form1 を開き、 **Windows フォーム デザイナー**です。  
  
2.  **ツールボックス**を開き、 **DebugControlLibrary コンポーネント** タブ、ドラッグして、**タブ**フォーム上にインスタンス。  
  
3.  検索、`DemoString`内のカスタム プロパティ、**プロパティ**ウィンドウです。 他のプロパティと同様に、値を変更することに注意してください。 場合にも注意してください、`DemoString`プロパティが選択されている場合、プロパティの説明文字列がの下に表示される、**プロパティ**ウィンドウです。  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>デザイン時デバッグのためのプロジェクトの設定  
 カスタム コントロールのデザイン時の動作をデバッグするには、カスタム コントロールのコードを実行している Visual Studio の別のインスタンスをデバッグします。  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>デザイン時デバッグ用のプロジェクトを設定するには  
  
1.  右クリックし、 **DebugControlLibrary**プロジェクトで、**ソリューション エクスプ ローラー**選択**プロパティ**です。  
  
2.  **DebugControlLibrary**プロパティ シートで、**デバッグ**タブです。  
  
     **開始動作**セクションで、**外部プログラムの開始**です。 できます、省略記号ボタンをクリックして、Visual Studio の別のインスタンスをデバッグ (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を Visual Studio IDE の参照ボタンをクリックします。 実行可能ファイルの名前は**devenv.exe**、され、パスは %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe で既定の場所にインストールした場合。  
  
3.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
4.  右クリックし、 **DebugControlLibrary**プロジェクトし、選択**スタートアップ プロジェクトとして設定**このデバッグ構成を有効にします。  
  
## <a name="debugging-your-custom-control-at-design-time"></a>カスタム コントロールをデザイン時のデバッグ  
 デザイン モードで実行するときに、カスタム コントロールをデバッグする準備が整いました。 デバッグ セッションを開始して Visual Studio の新しいインスタンスを作成、ソリューションを読み込み、"DebuggingExample"を使用します。 Form1 を開いたとき、**フォーム デザイナー**、カスタム コントロールのインスタンスが作成され、実行が開始されます。  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a>デザイン時にカスタム コントロールをデバッグするには  
  
1.  開く、**タブ**内のソース ファイル、**コード エディター**にブレークポイントを配置し、`Set`のアクセサー、`DemoString`プロパティです。  
  
2.  F5 キーを押してデバッグ セッションを開始します。 Visual Studio の新しいインスタンスを作成することに注意してください。 2 つの方法でインスタンスを区別することができます。  
  
    -   デバッグのインスタンスには、word**を実行している**のタイトル バーに  
  
    -   デバッグ インスタンスが、**開始**のボタンではその**デバッグ**ツールバーを無効になっています  
  
     ブレークポイントは、デバッグのインスタンスで設定されます。  
  
3.  Visual Studio の新しいインスタンスの"DebuggingExample"ソリューションを開きます。 選択して、ソリューションを簡単に見つけることができます**最近使ったプロジェクト**から、**ファイル**メニュー。 最近使用したファイル、"DebuggingExample.sln"ソリューション ファイルが表示されます。  
  
4.  Form1 を開き、**フォーム デザイナー**を選択し、**タブ**コントロール。  
  
5.  値を変更、`DemoString`プロパティです。 変更をコミットする場合、Visual Studio のデバッグのインスタンスがフォーカスを取得し、ブレークポイントで実行が停止に注意してください。 プロパティ アクセサーを 1 ステップを作成することができますと同様に、その他のコードはします。  
  
6.  Visual Studio のホスト インスタンスを閉じるかをクリックして終了する、デバッグ セッションがしたら、**デバッグの停止**デバッグ インスタンスでボタンをクリックします。  
  
## <a name="next-steps"></a>次の手順  
 これで、カスタム コントロールをデバッグするにはデザイン時に、Visual Studio IDE を使用して、コントロールの相互作用の拡張のさまざまな方法があります。  
  
-   使用することができます、<xref:System.ComponentModel.Component.DesignMode%2A>のプロパティ、<xref:System.ComponentModel.Component>デザイン時にのみ実行されるコードを記述するクラス。 詳細については、「<xref:System.ComponentModel.Component.DesignMode%2A>」を参照してください。  
  
-   いくつかの属性をデザイナーにカスタム コントロールの相互作用を操作するコントロールのプロパティに適用することができます。 これらの属性を見つけることができます、<xref:System.ComponentModel?displayProperty=nameWithType>名前空間。  
  
-   カスタム コントロールのカスタム デザイナーを記述することができます。 Visual Studio によって公開される拡張可能なデザイナー インフラストラクチャを使用してデザイン環境を完全に制御できます。 詳細については、「[チュートリアル:、Windows フォーム コントロール利用の Visual Studio デザイン時の機能を作成する](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [方法: デザイン時のサービスにアクセス](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [方法: Windows フォームでデザイン時サポートにアクセスする](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
