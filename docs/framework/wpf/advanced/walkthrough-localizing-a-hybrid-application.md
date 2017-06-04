---
title: "チュートリアル : ハイブリッド アプリケーションのローカライズ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ハイブリッド アプリケーション [WPF 相互運用性]"
  - "ローカリゼーション [WPF 相互運用性]"
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# チュートリアル : ハイブリッド アプリケーションのローカライズ
このチュートリアルでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのハイブリッド アプリケーション内にある [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 要素をローカライズする方法を示します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ホスト プロジェクトを作成する。  
  
-   ローカライズ可能な内容を追加する。  
  
-   ローカライズを有効にする。  
  
-   リソース識別子を割り当てる。  
  
-   LocBaml ツールを使用してサテライト アセンブリを生成する。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、[ハイブリッド アプリケーションのローカライズのサンプル](http://go.microsoft.com/fwlink/?LinkID=160015)を参照してください。  
  
 終了すると、ローカライズされたハイブリッド アプリケーションが作成されています。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## Windows フォームのホスト プロジェクトの作成  
 最初に [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アプリケーション プロジェクトを作成し、内容をローカライズする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素を追加します。  
  
#### ホスト プロジェクトを作成するには  
  
1.  `LocalizingWpfInWf` という名前の WPF アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  `SimpleControl` という [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 要素をプロジェクトに追加します。  
  
3.  <xref:System.Windows.Forms.Integration.ElementHost> コントロールを使用して、フォームに `SimpleControl` 要素を配置します。  詳細については、「[チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)」を参照してください。  
  
## ローカライズ可能な内容を追加する  
 次に、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ラベル コントロールを追加し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素の内容にローカライズ可能な文字列を設定します。  
  
#### ローカライズ可能な内容を追加する手順  
  
1.  ソリューション エクスプローラーで **\[SimpleControl.xaml\]** をダブルクリックして、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]でそのファイルを開きます。  
  
2.  次のコードを使用している <xref:System.Windows.Controls.Button> コントロールの内容を設定します。  
  
     [!code-xml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  ソリューション エクスプローラーで **\[Form1\]** をダブルクリックして Windows フォーム デザイナーを開きます。  
  
4.  ツールボックスを開いて、**\[ラベル\]** をダブルクリックし、フォームにラベル コントロールを追加します。  <xref:System.Windows.Forms.Control.Text%2A> プロパティの値を`「Hello」`に設定します。  
  
5.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
     `SimpleControl` 要素とラベル コントロールにより、テキスト **\[Hello\]** が表示されます。  
  
## ローカライズを有効にする  
 Windows フォーム デザイナーでは、サテライト アセンブリのローカライズを有効にする設定を行うことができます。  
  
#### ローカライズを有効にする手順  
  
1.  ソリューション エクスプローラーで、**\[Form1.cs\]** をダブルクリックして Windows フォーム デザイナーで開きます。  
  
2.  \[プロパティ\] ウィンドウで、フォームの **\[ローカライズ可能\]** プロパティを `true` に設定します。  
  
3.  \[プロパティ\] ウィンドウで、**\[言語\]** プロパティを **\[スペイン語 \(スペイン\)\]** に設定します。  
  
4.  Windows フォーム デザイナーで、ラベル コントロールを選択します。  
  
5.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.Control.Text%2A> プロパティの値を`「Hola」`に設定します。  
  
     Form1.es\-ES.resx という名前の新しいリソース ファイルが、プロジェクトに追加されます。  
  
6.  ソリューション エクスプローラーで、**\[Form1.cs\]** を右クリックし、**\[コードの表示\]** をクリックしてコード エディターで開きます。  
  
7.  `InitializeComponent` の呼び出しの前にある `Form1` コンストラクターに次のコードをコピーします。  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  ソリューション エクスプローラーで、**\[LocalizingWpfInWf\]** を右クリックし、**\[プロジェクトのアンロード\]** をクリックします。  
  
     プロジェクト名に **\(利用不可\)** のマークが付きます。  
  
9. **\[LocalizingWpfInWf\]** を右クリックし、**\[LocalizingWpfInWf.csproj の編集\]** をクリックします。  
  
     コード エディターでプロジェクト ファイルが開きます。  
  
10. プロジェクト ファイルの最初の `PropertyGroup` に次の行をコピーします。  
  
    ```  
    <UICulture>en-US</UICulture>   
    ```  
  
11. プロジェクト ファイルを保存して閉じます。  
  
12. ソリューション エクスプローラーで、**\[LocalizingWpfInWf\]** を右クリックし、**\[プロジェクトの再読み込み\]** をクリックします。  
  
## リソース識別子を割り当てる  
 リソース識別子を使用すると、ローカライズ可能な内容をリソース アセンブリにマッピングできます。  `updateuid` オプションを指定すると、MsBuild.exe アプリケーションが自動的にリソース識別子を割り当てます。  
  
#### リソース識別子を割り当てる手順  
  
1.  \[スタート\] メニューから、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] コマンド プロンプトを開きます。  
  
2.  次のコマンドを使用して、ローカライズ可能な内容にリソース識別子を割り当てます。  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  ソリューション エクスプローラーで、\[SimpleControl.xaml\] をダブルクリックして、コード エディターでそのファイルを開きます。  `msbuild` コマンドによって、すべての要素に `Uid` 属性が追加されています。  これにより、リソース識別子の割り当てを用いたローカライズが容易になります。  
  
     [!code-xml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  F6 キーを押してソリューションをビルドします。  
  
## LocBaml を使用してサテライト アセンブリを生成する  
 ローカライズされた内容は、リソース専用*サテライト アセンブリ*に格納されています。  LocBaml.exe コマンド ライン ツールを使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内容のローカライズされたアセンブリを生成します。  
  
#### サテライト アセンブリを生成する手順  
  
1.  プロジェクトの obj\\Debug フォルダーに LocBaml.exe をコピーします。  詳細については、「[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)」を参照してください。  
  
2.  コマンド プロンプト ウィンドウで、次のコマンドを使用してテンポラリ ファイルにリソース文字列を抽出します。  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] または別のテキスト エディターで temp.csv ファイルを開きます。  文字列 `"Hello"` をそのスペイン語の訳語 `"Hola"` に置き換えます。  
  
4.  temp.csv ファイルを保存します。  
  
5.  次のコマンドを使用して、ローカライズされたリソース ファイルを生成します。  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     LocalizingWpfInWf.g.es\-ES.resources ファイルは、obj\\Debug フォルダーに作成されます。  
  
6.  次のコマンドを使用して、ローカライズされたサテライト アセンブリを作成します。  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     LocalizingWpfInWf.resources.dll ファイルは、obj\\Debug フォルダーに作成されます。  
  
7.  プロジェクトの bin\\Debug\\es\-ES フォルダーに LocalizingWpfInWf.resources.dll ファイルをコピーします。  既存のファイルを置き換えます。  
  
8.  プロジェクトの bin\\Debug フォルダーにある LocalizingWpfInWf.exe を実行します。  サテライト アセンブリが上書きされるので、アプリケーションを再度ビルドしないでください。  
  
     アプリケーションにより、英語の文字列の代わりにローカライズされた文字列が表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)   
 [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/ja-jp/9a96220d-a19b-4de0-9f48-01e5d82679e5)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)