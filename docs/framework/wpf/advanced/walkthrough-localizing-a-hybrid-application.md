---
title: "チュートリアル : ハイブリッド アプリケーションのローカライズ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d46ea30a0e6a509d6a6cac6d8686e5f5307f0cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>チュートリアル : ハイブリッド アプリケーションのローカライズ
このチュートリアルでは、ローカライズする方法について[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内の要素、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-ベースのハイブリッド アプリケーションです。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   作成する、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ホスト プロジェクト。  
  
-   ローカライズ可能なコンテンツを追加します。  
  
-   ローカリゼーションを有効にします。  
  
-   リソース識別子を割り当てます。  
  
-   LocBaml ツールを使用して、サテライト アセンブリを生成します。  
  
 このチュートリアルでタスクの完全なコードについては、次を参照してください。[ハイブリッド アプリケーションのサンプルのローカライズ](http://go.microsoft.com/fwlink/?LinkID=160015)です。  
  
 完了したら、ローカライズされたハイブリッド アプリケーションがあります。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]。  
  
## <a name="creating-the-windows-forms-host-project"></a>Windows フォーム ホスト プロジェクトを作成します。  
 作成するには、まず、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション プロジェクトを追加、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカライズはコンテンツを持つ要素。  
  
#### <a name="to-create-the-host-project"></a>ホスト プロジェクトを作成するには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`LocalizingWpfInWf`です。 詳細については、「 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  追加、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>と呼ばれる要素`SimpleControl`をプロジェクトにします。  
  
3.  使用して、<xref:System.Windows.Forms.Integration.ElementHost>コントロールを配置する、`SimpleControl`フォーム上の要素。 詳細については、次を参照してください。[チュートリアル: Windows フォームの 3-D WPF 複合コントロールをホストしている](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)です。  
  
## <a name="adding-localizable-content"></a>ローカライズ可能なコンテンツを追加します。  
 次に、追加する、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールにラベルを付けるし、設定、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素のコンテンツをローカライズ可能な文字列。  
  
#### <a name="to-add-localizable-content"></a>ローカライズ可能なコンテンツを追加するには  
  
1.  ソリューション エクスプ ローラーで、 **SimpleControl.xaml**で開く、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
2.  コンテンツを設定、<xref:System.Windows.Controls.Button>次のコードを使用して制御します。  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  ソリューション エクスプ ローラーで、 **Form1**を Windows フォーム デザイナーで開きます。  
  
4.  ツールボックスを開き をダブルクリック**ラベル**ラベル コントロールをフォームに追加します。 <xref:System.Windows.Forms.Control.Text%2A> プロパティの値を `"Hello"` に設定します。  
  
5.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
     両方の`SimpleControl`要素、およびラベル コントロールのテキストを表示**「こんにちは」**です。  
  
## <a name="enabling-localization"></a>ローカリゼーションの有効化  
 Windows フォーム デザイナーは、サテライト アセンブリでのローカライズを有効にするための設定を提供します。  
  
#### <a name="to-enable-localization"></a>ローカリゼーションを有効にするには  
  
1.  ソリューション エクスプ ローラーで、 **Form1.cs**を Windows フォーム デザイナーで開きます。  
  
2.  [プロパティ] ウィンドウで、フォームの値を設定**Localizable**プロパティを`true`です。  
  
3.  [プロパティ] ウィンドウ内の値を設定、**言語**プロパティを**スペイン語 (スペイン)**です。  
  
4.  Windows フォーム デザイナーでは、ラベル コントロールを選択します。  
  
5.  [プロパティ] ウィンドウ内の値を設定、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`"Hola"`です。  
  
     Form1.es ES.resx をという名前の新しいリソース ファイルがプロジェクトに追加されます。  
  
6.  ソリューション エクスプ ローラーで右クリック**Form1.cs**  をクリック**コードの表示**コード エディターで開きます。  
  
7.  次のコードをコピー、`Form1`への呼び出しの前のコンス トラクター`InitializeComponent`です。  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  ソリューション エクスプ ローラーで右クリック**LocalizingWpfInWf**  をクリック**プロジェクトのアンロード**です。  
  
     プロジェクト名のラベルは**(使用不可)**です。  
  
9. 右クリック**LocalizingWpfInWf**、 をクリック**編集 LocalizingWpfInWf.csproj**です。  
  
     プロジェクト ファイルがコード エディターで開きます。  
  
10. 最初に、次の行をコピー`PropertyGroup`プロジェクト ファイルにします。  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. プロジェクト ファイルを保存して閉じます。  
  
12. ソリューション エクスプ ローラーで右クリック**LocalizingWpfInWf**  をクリック**プロジェクトの再読み込み**です。  
  
## <a name="assigning-resource-identifiers"></a>リソース識別子を割り当てる  
 リソース識別子を使用して、リソース アセンブリに、ローカライズ可能なコンテンツをマップできます。 MsBuild.exe アプリケーションを指定するときに自動的にリソース識別子を割り当てます、`updateuid`オプション。  
  
#### <a name="to-assign-resource-identifiers"></a>リソース識別子を割り当てる  
  
1.  [スタート] メニューから開きます、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]コマンド プロンプトです。  
  
2.  次のコマンドを使用して、ローカライズ可能なコンテンツにリソース識別子を割り当てます。  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  ソリューション エクスプ ローラーで、 **SimpleControl.xaml**コード エディターで開きます。 \Outputfromtestproviderdebugmode.txt、`msbuild`コマンドが追加、`Uid`すべての要素に属性します。 これには、リソース識別子の割り当てを通じてローカライズが容易になります。  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  F6 キーを押してソリューションをビルドします。  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>LocBaml を使用して、サテライト アセンブリを生成するには  
 リソース専用で、ローカライズされたコンテンツが格納されている*サテライト アセンブリ*です。 ローカライズされたアセンブリを生成するために、コマンド ライン ツール LocBaml.exe を使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。  
  
#### <a name="to-produce-a-satellite-assembly"></a>サテライト アセンブリを生成するには  
  
1.  LocBaml.exe をプロジェクトの obj\Debug フォルダーにコピーします。 詳細については、次を参照してください。[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)です。  
  
2.  コマンド プロンプト ウィンドウでは、一時ファイルにリソース文字列を抽出するのに、次のコマンドを使用します。  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  Temp.csv ファイルを開きます[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]などのテキスト エディター。 文字列を置き換える`"Hello"`スペイン語に翻訳を`"Hola"`です。  
  
4.  Temp.csv ファイルを保存します。  
  
5.  ローカライズされたリソース ファイルを生成するのにには、次のコマンドを使用します。  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     LocalizingWpfInWf.g.es ES.resources ファイルは obj\Debug フォルダーに作成されます。  
  
6.  ローカライズされたサテライト アセンブリをビルドするのにには、次のコマンドを使用します。  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     LocalizingWpfInWf.resources.dll ファイルは obj\Debug フォルダーに作成されます。  
  
7.  LocalizingWpfInWf.resources.dll ファイルをプロジェクトの bin\Debug\es ES フォルダーにコピーします。 既存のファイルを置き換えます。  
  
8.  プロジェクトの bin \debug フォルダーにある LocalizingWpfInWf.exe を実行します。 アプリケーションを再構築しないまたはサテライト アセンブリが上書きされます。  
  
     アプリケーションは、英語の文字列の代わりにローカライズされた文字列を示しています。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [チュートリアル: Windows フォームのローカリゼーション](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [WPF デザイナー](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
