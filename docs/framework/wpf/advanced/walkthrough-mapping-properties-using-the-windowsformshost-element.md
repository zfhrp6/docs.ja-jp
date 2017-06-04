---
title: "チュートリアル : WindowsFormsHost 要素を使用したプロパティの割り当て | Microsoft Docs"
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
  - "割り当て (プロパティを)"
  - "WindowsFormsHost 要素のプロパティの割り当て"
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# チュートリアル : WindowsFormsHost 要素を使用したプロパティの割り当て
このチュートリアルで使用する方法、<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>プロパティにマップする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、ホスト型の対応するプロパティにプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトを作成しています。  
  
-   アプリケーションのレイアウトを定義します。  
  
-   新しいプロパティ マッピングを定義します。  
  
-   プロパティの既定のマッピングを削除しています。  
  
-   プロパティの既定のマッピングを交換してください。  
  
-   プロパティの既定のマッピングを拡張しています。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、次を参照してください。 [WindowsFormsHost 要素のサンプルを使用してマッピング プロパティ](http://go.microsoft.com/fwlink/?LinkID=160019)します。  
  
 マップが完了したらができます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールです。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-and-set-up-the-project"></a>作成し、プロジェクトを設定するには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`PropertyMappingWithWfhSample`です。  
  
2.  ソリューション エクスプ ローラーでは、WindowsFormsIntegration.dll と呼ばれる WindowsFormsIntegration アセンブリへの参照を追加します。  
  
3.  ソリューション エクスプ ローラーでは、System.Drawing、および System.Windows.Forms アセンブリへの参照を追加します。  
  
## <a name="defining-the-application-layout"></a>アプリケーションのレイアウトを定義します。  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションで使用する、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストへの要素、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールです。  
  
#### <a name="to-define-the-application-layout"></a>アプリケーションのレイアウトを定義するには  
  
1.  Window1.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
2.  既存のコードを次のコードに置き換えます。  
  
     [!code-xml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  Window1.xaml.cs のコード エディターでを開きます。  
  
4.  ファイルの上部にある次の名前空間をインポートします。  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a>新しいプロパティ マッピングを定義します。  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、いくつかの既定のプロパティ マッピングを提供します。 新しいプロパティ割り当てを追加するには呼び出すことによって、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。  
  
#### <a name="to-define-a-new-property-mapping"></a>新しいプロパティ マッピングを定義するには  
  
-   定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     `AddClipMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.UIElement.Clip%2A>プロパティです。  
  
     `OnClipChange`メソッドは、変換、<xref:System.Windows.UIElement.Clip%2A>プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>プロパティです。  
  
     `Window1_SizeChanged`メソッドは処理ウィンドウの<xref:System.Windows.FrameworkElement.SizeChanged>イベントがアプリケーション ウィンドウに合わせてクリッピング領域のサイズを設定するとします。  
  
## <a name="removing-a-default-property-mapping"></a>プロパティの既定のマッピングを削除します。  
 プロパティの既定のマッピングを削除する、<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。  
  
#### <a name="to-remove-a-default-property-mapping"></a>プロパティの既定のマッピングを削除するには  
  
-   定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     `RemoveCursorMapping`メソッドの既定のマッピングを削除する、<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティです。  
  
## <a name="replacing-a-default-property-mapping"></a>プロパティの既定のマッピングを置き換える  
 既定のマッピングと呼び出しを削除することでプロパティの既定のマッピングを置き換える、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。  
  
#### <a name="to-replace-a-default-property-mapping"></a>プロパティの既定のマッピングを置換するには  
  
-   定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     `ReplaceFlowDirectionMapping`メソッドは、置換の既定のマッピング、 <xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティです。  
  
     `OnFlowDirectionChange`メソッドは、変換、 <xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A>プロパティです。  
  
     `cb_CheckedChanged`メソッド ハンドル、 <xref:System.Windows.Forms.CheckBox.CheckedChanged>でイベントを<xref:System.Windows.Forms.CheckBox>コントロールです。 割り当て、 <xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティの値に基づいて、 <xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティ  
  
## <a name="extending-a-default-property-mapping"></a>プロパティの既定のマッピングを拡張します。  
 プロパティの既定のマッピングを使用し、また独自のマッピングでは拡張できます。  
  
#### <a name="to-extend-a-default-property-mapping"></a>プロパティの既定のマッピングを拡張するには  
  
-   定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     `ExtendBackgroundMapping`メソッドでは、カスタム プロパティの翻訳者を追加すると、既存<xref:System.Windows.Controls.Control.Background%2A>プロパティ マッピングします。  
  
     `OnBackgroundChange`メソッドは、ホストされるコントロールの特定のイメージを割り当てます<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティです。 `OnBackgroundChange`既定のプロパティ マッピングが適用された後にメソッドが呼び出されます。  
  
## <a name="initializing-your-property-mappings"></a>プロパティ マッピングの初期化  
 プロパティ マッピングで既に説明したメソッドを呼び出して設定、 <xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーです。  
  
#### <a name="to-initialize-your-property-mappings"></a>プロパティ マッピングを初期化するには  
  
1.  定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     `WindowLoaded`メソッド ハンドル、 <xref:System.Windows.FrameworkElement.Loaded>イベントし、次の初期化を実行します。  
  
    -   作成、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox>コントロールです。  
  
    -   プロパティのマッピングを設定するチュートリアルの前半で定義されているメソッドを呼び出します。  
  
    -   初期の割り当て済みのプロパティに値を割り当てます。  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 効果を確認するチェック ボックスをクリックして、 <xref:System.Windows.FrameworkElement.FlowDirection%2A>マッピングします。 チェック ボックスをクリックすると、レイアウトは左から右方向を反転します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [チュートリアル: WPF での Windows フォーム コントロールをホストしています。](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)