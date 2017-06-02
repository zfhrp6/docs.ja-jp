---
title: "チュートリアル : ElementHost コントロールを使用したプロパティの割り当て | Microsoft Docs"
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
  - "ElementHost コントロール, 割り当て (プロパティを)"
  - "割り当て (プロパティを)"
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# チュートリアル : ElementHost コントロールを使用したプロパティの割り当て
このチュートリアルでは、<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> プロパティを使用して、ホストされている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素の対応するプロパティに [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] プロパティを割り当てる方法を示します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   新しいプロパティ マッピングの定義。  
  
-   既定のプロパティ マッピングの削除。  
  
-   既定のプロパティ マッピングの拡張。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、[ElementHost コントロールを使用したプロパティの割り当てのサンプル](http://go.microsoft.com/fwlink/?LinkID=160018)を参照してください。  
  
 終了すると、ホストされている要素の対応する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティに [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] プロパティを割り当てることができるようになります。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## プロジェクトの作成  
  
#### プロジェクトを作成するには  
  
1.  `PropertyMappingWithElementHost` という名前の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  ソリューション エクスプローラーで、次の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アセンブリへの参照を追加します。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
3.  次のコードを `Form1` コード ファイルの先頭にコピーします。  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  Windows フォーム デザイナーで `Form1` を開きます。  フォームをダブルクリックして <xref:System.Windows.Forms.Form.Load> イベントのイベント ハンドラーを追加します。  
  
5.  Windows フォーム デザイナーに戻り、フォームの <xref:System.Windows.Forms.Control.Resize> イベントのイベント ハンドラーを追加します。  詳細については、「[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/ja-jp/8461e9b8-14e8-406f-936e-3726732b23d2)」を参照してください。  
  
6.  `Form1` クラス内に、<xref:System.Windows.Forms.Integration.ElementHost> フィールドを宣言します。  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## 新しいプロパティ割り当ての定義  
 <xref:System.Windows.Forms.Integration.ElementHost> コントロールには、既定のプロパティ割り当てがいくつか用意されています。  新しいプロパティ割り当てを追加するには、<xref:System.Windows.Forms.Integration.ElementHost> コントロールの <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> で <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> メソッドを呼び出します。  
  
#### 新しいプロパティ割り当てを定義するには  
  
1.  `Form1` クラスの定義に次のコードをコピーします。  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     `AddMarginMapping` メソッドは、<xref:System.Windows.Forms.Control.Margin%2A> プロパティの新しいマッピングを追加します。  
  
     `OnMarginChange` メソッドは、<xref:System.Windows.Forms.Control.Margin%2A> プロパティを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の <xref:System.Windows.FrameworkElement.Margin%2A> プロパティに変換します。  
  
2.  `Form1` クラスの定義に次のコードをコピーします。  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     `AddRegionMapping` メソッドは、<xref:System.Windows.Forms.Control.Region%2A> プロパティの新しいマッピングを追加します。  
  
     `OnRegionChange` メソッドは、<xref:System.Windows.Forms.Control.Region%2A> プロパティを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の <xref:System.Windows.UIElement.Clip%2A> プロパティに変換します。  
  
     `Form1_Resize` メソッドは、フォームの <xref:System.Windows.Forms.Control.Resize> イベントを処理し、ホストされている要素に合わせてクリッピング領域のサイズを設定します。  
  
## 既定のプロパティ マッピングの削除  
 既定のプロパティ割り当てを削除するには、<xref:System.Windows.Forms.Integration.ElementHost> コントロールの <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> で <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> メソッドを呼び出します。  
  
#### 既定のプロパティ マッピングを削除するには  
  
-   `Form1` クラスの定義に次のコードをコピーします。  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     `RemoveCursorMapping` メソッドは、<xref:System.Windows.Forms.Control.Cursor%2A> プロパティの既定のマッピングを削除します。  
  
## 既定のプロパティ マッピングの拡張  
 既定のプロパティ マッピングを使用したり、それをユーザー独自のマッピングで拡張することもできます。  
  
#### 既定のプロパティ マッピングを拡張するには  
  
-   `Form1` クラスの定義に次のコードをコピーします。  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     `ExtendBackColorMapping` メソッドは、カスタム プロパティ トランスレータを既存の <xref:System.Windows.Forms.Control.BackColor%2A> プロパティ マッピングに追加します。  
  
     `OnBackColorChange` メソッドは、特定のイメージをホストされているコントロールの <xref:System.Windows.Controls.Control.Background%2A> プロパティに割り当てます。  `OnBackColorChange` メソッドは、既定のプロパティ マッピングの適用後に呼び出されます。  
  
## プロパティ マッピングの初期化  
  
#### プロパティ マッピングを初期化するには  
  
1.  `Form1` クラスの定義に次のコードをコピーします。  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     `Form1_Load` メソッドは <xref:System.Windows.Forms.Form.Load> イベントを処理し、次の初期化を実行します。  
  
    -   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> 要素を作成します。  
  
    -   このチュートリアルで定義したメソッドを呼び出して、プロパティ マッピングを設定します。  
  
    -   マップされたプロパティに初期値を割り当てます。  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)