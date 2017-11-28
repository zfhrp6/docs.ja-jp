---
title: "チュートリアル : WindowsFormsHost 要素を使用したプロパティの割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f566d41ff1ffa07a2f52641ba05e48dfa604cfc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>チュートリアル : WindowsFormsHost 要素を使用したプロパティの割り当て
このチュートリアルで使用する方法、<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>プロパティにマップする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   アプリケーションのレイアウトを定義します。  
  
-   新しいプロパティ マッピングを定義します。  
  
-   プロパティの既定のマッピングを削除しています。  
  
-   プロパティの既定のマッピングを置換します。  
  
-   プロパティの既定のマッピングを拡張します。  
  
 このチュートリアルでタスクの完全なコードについては、次を参照してください。 [WindowsFormsHost 要素のサンプルを使用してプロパティをマッピング](http://go.microsoft.com/fwlink/?LinkID=160019)です。  
  
 完了したらにマップできる、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`PropertyMappingWithWfhSample`です。  
  
2.  ソリューション エクスプ ローラーで、WindowsFormsIntegration.dll と呼ばれる WindowsFormsIntegration アセンブリへの参照を追加します。  
  
3.  ソリューション エクスプ ローラーで、System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照を追加します。  
  
## <a name="defining-the-application-layout"></a>アプリケーションのレイアウトを定義します。  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションで使用する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストへの要素、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
#### <a name="to-define-the-application-layout"></a>アプリケーションのレイアウトを定義するには  
  
1.  Window1.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
2.  既存のコードを次のコードに置き換えます。  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  Window1.xaml.cs の名前をコード エディターで開きます。  
  
4.  ファイルの先頭には、次の名前空間をインポートします。  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a>新しいプロパティ マッピングを定義します。  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がいくつかの既定のプロパティ マッピングを用意されています。 呼び出して新しいプロパティ マッピングを追加する、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。  
  
#### <a name="to-define-a-new-property-mapping"></a>新しいプロパティ マッピングを定義するには  
  
-   定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     `AddClipMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.UIElement.Clip%2A>プロパティです。  
  
     `OnClipChange`メソッドは、変換、<xref:System.Windows.UIElement.Clip%2A>プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>プロパティです。  
  
     `Window1_SizeChanged`メソッドを処理ウィンドウの<xref:System.Windows.FrameworkElement.SizeChanged>イベントと、アプリケーション ウィンドウに合わせてクリッピング領域のサイズします。  
  
## <a name="removing-a-default-property-mapping"></a>プロパティの既定のマッピングを削除します。  
 プロパティの既定のマッピングを削除する、<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。  
  
#### <a name="to-remove-a-default-property-mapping"></a>プロパティの既定のマッピングを削除するには  
  
-   定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     `RemoveCursorMapping`メソッドの既定のマッピングを削除する、<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティです。  
  
## <a name="replacing-a-default-property-mapping"></a>プロパティの既定のマッピングを置き換える  
 既定のマッピングと呼び出し元を削除することでプロパティの既定のマッピングを置き換える、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。  
  
#### <a name="to-replace-a-default-property-mapping"></a>プロパティの既定のマッピングを置換するには  
  
-   定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     `ReplaceFlowDirectionMapping`メソッドの既定のマッピングに置き換えて、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティです。  
  
     `OnFlowDirectionChange`メソッドは、変換、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>プロパティです。  
  
     `cb_CheckedChanged`メソッド ハンドル、<xref:System.Windows.Forms.CheckBox.CheckedChanged>でイベントを<xref:System.Windows.Forms.CheckBox>コントロール。 割り当てます、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティの値に基づきます、<xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティ  
  
## <a name="extending-a-default-property-mapping"></a>プロパティの既定のマッピングを拡張します。  
 プロパティの既定のマッピングを使用しても、独自のマッピングに付加して拡張できます。  
  
#### <a name="to-extend-a-default-property-mapping"></a>プロパティの既定のマッピングを拡張するには  
  
-   定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     `ExtendBackgroundMapping`メソッドでは、カスタム プロパティ トランスレーターを追加すると、既存<xref:System.Windows.Controls.Control.Background%2A>プロパティ マッピングします。  
  
     `OnBackgroundChange`メソッドは、ホストされるコントロールの特定のイメージを割り当てます<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティです。 `OnBackgroundChange`既定のプロパティ マッピングが適用された後にメソッドが呼び出されます。  
  
## <a name="initializing-your-property-mappings"></a>プロパティ マッピングの初期化  
 プロパティ マッピングで既に説明したメソッドを呼び出して設定、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラー。  
  
#### <a name="to-initialize-your-property-mappings"></a>プロパティ マッピングを初期化するには  
  
1.  定義に次のコードをコピー、`Window1`クラスです。  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     `WindowLoaded`メソッド ハンドル、<xref:System.Windows.FrameworkElement.Loaded>イベントと、次の初期化を実行します。  
  
    -   作成、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox>コントロール。  
  
    -   プロパティ マッピングをセットアップするチュートリアルの前半で定義されているメソッドを呼び出します。  
  
    -   マップされているプロパティに初期値を割り当てます。  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 効果を確認するチェック ボックスをクリックして、<xref:System.Windows.FrameworkElement.FlowDirection%2A>マッピングします。 チェック ボックスをクリックすると、レイアウトは左から右方向を反転させます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [WPF デザイナー](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
