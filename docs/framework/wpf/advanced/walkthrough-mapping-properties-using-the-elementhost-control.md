---
title: "チュートリアル : ElementHost コントロールを使用したプロパティの割り当て"
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
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0db7b9677b5c8c415b6d0b3f49bd149c06843a33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>チュートリアル : ElementHost コントロールを使用したプロパティの割り当て
このチュートリアルで使用する方法、<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>プロパティにマップする[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   新しいプロパティ マッピングを定義します。  
  
-   プロパティの既定のマッピングを削除しています。  
  
-   プロパティの既定のマッピングを拡張します。  
  
 このチュートリアルでタスクの完全なコードについては、次を参照してください。 [ElementHost コントロールのサンプルを使用してプロパティをマッピング](http://go.microsoft.com/fwlink/?LinkID=160018)です。  
  
 完了したらにマップできる、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]を対応するプロパティ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストされている要素のプロパティです。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  作成、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]という名前のアプリケーション プロジェクト`PropertyMappingWithElementHost`です。 詳細については、「 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  ソリューション エクスプ ローラーで、次の参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
3.  先頭に次のコードをコピー、`Form1`コード ファイル。  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  Windows フォーム デザイナーで `Form1` を開きます。 イベント ハンドラーの追加フォームをダブルクリックして、<xref:System.Windows.Forms.Form.Load>イベント。  
  
5.  Windows フォーム デザイナーに戻るし、フォームのイベント ハンドラーを追加<xref:System.Windows.Forms.Control.Resize>イベント。 詳細については、次を参照してください。[する方法: イベント ハンドラーを使用して作成デザイナー](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)です。  
  
6.  宣言、<xref:System.Windows.Forms.Integration.ElementHost>フィールドで、`Form1`クラスです。  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a>新しいプロパティのマッピングを定義します。  
 <xref:System.Windows.Forms.Integration.ElementHost>コントロールにより、いくつかの既定値がプロパティのマッピングを提供します。 呼び出して新しいプロパティ マッピングを追加する、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>します。  
  
#### <a name="to-define-new-property-mappings"></a>新しいプロパティのマッピングを定義するには  
  
1.  定義に次のコードをコピー、`Form1`クラスです。  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     `AddMarginMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.Forms.Control.Margin%2A>プロパティです。  
  
     `OnMarginChange`メソッドは、変換、<xref:System.Windows.Forms.Control.Margin%2A>プロパティを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.FrameworkElement.Margin%2A>プロパティです。  
  
2.  定義に次のコードをコピー、`Form1`クラスです。  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     `AddRegionMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.Forms.Control.Region%2A>プロパティです。  
  
     `OnRegionChange`メソッドは、変換、<xref:System.Windows.Forms.Control.Region%2A>プロパティを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.UIElement.Clip%2A>プロパティです。  
  
     `Form1_Resize`メソッドは、処理、フォームの<xref:System.Windows.Forms.Control.Resize>イベントし、ホストされている要素に合わせてクリッピング領域のサイズを設定します。  
  
## <a name="removing-a-default-property-mapping"></a>プロパティの既定のマッピングを削除します。  
 プロパティの既定のマッピングを削除する、<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>メソッドを<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>します。  
  
#### <a name="to-remove-a-default-property-mapping"></a>プロパティの既定のマッピングを削除するには  
  
-   定義に次のコードをコピー、`Form1`クラスです。  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     `RemoveCursorMapping`メソッドの既定のマッピングを削除する、<xref:System.Windows.Forms.Control.Cursor%2A>プロパティです。  
  
## <a name="extending-a-default-property-mapping"></a>プロパティの既定のマッピングを拡張します。  
 プロパティの既定のマッピングを使用しても、独自のマッピングに付加して拡張できます。  
  
#### <a name="to-extend-a-default-property-mapping"></a>プロパティの既定のマッピングを拡張するには  
  
-   定義に次のコードをコピー、`Form1`クラスです。  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     `ExtendBackColorMapping`メソッドでは、カスタム プロパティ トランスレーターを追加すると、既存<xref:System.Windows.Forms.Control.BackColor%2A>プロパティ マッピングします。  
  
     `OnBackColorChange`メソッドは、ホストされるコントロールの特定のイメージを割り当てます<xref:System.Windows.Controls.Control.Background%2A>プロパティです。 `OnBackColorChange`既定のプロパティ マッピングが適用された後にメソッドが呼び出されます。  
  
## <a name="initializing-your-property-mappings"></a>プロパティ マッピングの初期化  
  
#### <a name="to-initialize-your-property-mappings"></a>プロパティ マッピングを初期化するには  
  
1.  定義に次のコードをコピー、`Form1`クラスです。  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     `Form1_Load`メソッド ハンドル、<xref:System.Windows.Forms.Form.Load>イベントと、次の初期化を実行します。  
  
    -   作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>要素。  
  
    -   プロパティ マッピングをセットアップするチュートリアルの前半で定義されているメソッドを呼び出します。  
  
    -   マップされているプロパティに初期値を割り当てます。  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [WPF デザイナー](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
