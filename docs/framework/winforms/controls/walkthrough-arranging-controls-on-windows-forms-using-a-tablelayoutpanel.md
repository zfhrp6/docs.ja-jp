---
title: "チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9636585fe9671b8822a6510d405eef5e6f23527e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置
アプリケーションによっては、フォームのサイズを変更したり、コンテンツのサイズが変化したりしたときに、それに応じて自動的にレイアウトを調整するフォームが必要です。 動的なレイアウトが必要であり、かつコードで <xref:System.Windows.Forms.Control.Layout> イベントを明示的に処理しない場合は、レイアウト パネルの使用をご検討ください。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> コントロールと <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、コントロールをフォームに直感的な方法で配置できます。 これら 2 つのコントロールは、それぞれに含まれる子コントロールの相対位置を制御するための自動的で構成可能な機能を提供します。また、どちらも実行時に動的なレイアウト機能を提供するため、親フォームの寸法の変更に応じて子コントロールのサイズと位置を変更できます。 レイアウト パネルは他のレイアウト パネルの入れ子にすることができるため、高度なユーザー インターフェイスを実現できます。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> はその内容を特定のフローの方向 (水平または垂直) に配置します。 ある行から次の行、またはある列から次の列に内容をラップすることができます。 また、ラップする代わりにクリップすることもできます。 詳細については、次を参照してください。[チュートリアル: Windows を使用して、FlowLayoutPanel をフォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)です。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> HTML と同様の機能を提供する、グリッドに内容を整列\<テーブル > 要素。 <xref:System.Windows.Forms.TableLayoutPanel>コントロールでは、個々 のコントロールの位置を正確に指定することがなく、グリッド レイアウトにコントロールを配置することができます。 セルは行と列に配置され、それぞれに異なるサイズを設定できます。 セルは、行および列全体でマージできることができます。 セルには、すべてのフォームを含めをコンテナーとしての他のほとんどの点での動作を含めることができます。  
  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールも機能が備わっている比例サイズ変更、実行時に、フォームのサイズを変更、レイアウトがスムーズに変更できるようにします。 これにより、<xref:System.Windows.Forms.TableLayoutPanel>コントロールは、データ エントリ フォームとローカライズされたアプリケーションなどの目的も適しています。 詳細については、次を参照してください。[チュートリアル: データ エントリのサイズ変更可能な Windows フォームの作成](http://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab)と[チュートリアル: ローカライズ可能な Windows フォームの作成](http://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c)です。  
  
 一般に、使用しないで、<xref:System.Windows.Forms.TableLayoutPanel>レイアウト全体のコンテナーと同様に制御します。 使用して<xref:System.Windows.Forms.TableLayoutPanel>コントロールをレイアウトの部分に比例してサイズ変更機能を提供します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   行と列にコントロールの配置  
  
-   設定の行と列のプロパティ  
  
-   コントロールで行または列のまたがりメモリ割り当てください。  
  
-   オーバーフローの自動処理  
  
-   ツールボックスでのダブルクリックによるコントロールの挿入  
  
-   アウトラインの描画によるコントロールの挿入  
  
-   別の親コントロールへの既存コントロールの再割り当て  
  
 終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  "TableLayoutPanelExample"と呼ばれる Windows アプリケーション プロジェクトを作成します。 詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)です。  
  
2.  フォームを選択、 **Windows** **フォーム デザイナー**です。  
  
## <a name="arranging-controls-in-rows-and-columns"></a>行と列にコントロールの配置  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールでは、行と列にコントロールを簡単に配置することができます。  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>TableLayoutPanel を使用して列と行にコントロールを配置するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。 なお、既定では、<xref:System.Windows.Forms.TableLayoutPanel>コントロールに 4 つのセルがあります。  
  
2.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、セルの 1 つにドロップします。 なお、<xref:System.Windows.Forms.Button>コントロールが選択したセル内で作成します。  
  
3.  3 個をドラッグして<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.TableLayoutPanel>コントロールで、各セルにボタンが含まれていること。  
  
4.  2 つの列間の垂直方向サイズ変更ハンドルをドラッグし、左に移動します。 なお、<xref:System.Windows.Forms.Button>中のサイズ、幅を小さくする最初の列内のコントロールのサイズが変更される、 <xref:System.Windows.Forms.Button> 2 番目の列内のコントロールが変更されていません。  
  
5.  2 つの列間の垂直方向サイズ変更ハンドルをドラッグし、右側に移動します。 注意してください、<xref:System.Windows.Forms.Button>最初の列内のコントロールは、元のサイズに戻るときに、 <xref:System.Windows.Forms.Button> 2 番目の列内のコントロールが右方向に移動します。  
  
6.  パネル内のコントロールへの影響を表示するには、上下の水平方向サイズ変更ハンドルを移動します。  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>ドッキングと固定を使用して、セル内のコントロールの配置  
 アンカーで子コントロールの動作、<xref:System.Windows.Forms.TableLayoutPanel>他のコンテナー コントロールの動作と異なります。 子コントロールのドッキング動作は、他のコンテナー コントロールと同じです。  
  
#### <a name="positioning-controls-within-cells"></a>セル内のコントロールの配置  
  
1.  最初の選択<xref:System.Windows.Forms.Button>コントロール。 <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Fill>に変更します。 なお、<xref:System.Windows.Forms.Button>コントロールを拡張すると、そのセルを入力します。  
  
2.  その他のいずれかを選択<xref:System.Windows.Forms.Button>コントロール。 <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を <xref:System.Windows.Forms.AnchorStyles.Right>に変更します。 コントロールが移動されるよう、右罫線のセルの右側の境界線の近くに注意してください。 枠線の間の距離は、の合計、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティと、パネルの<xref:System.Windows.Forms.Control.Padding%2A>プロパティです。  
  
3.  値を変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを<xref:System.Windows.Forms.AnchorStyles.Right>と<xref:System.Windows.Forms.AnchorStyles.Left>です。 コントロールが、セルの幅にサイズ設定に注意してください、<xref:System.Windows.Forms.Control.Margin%2A>と<xref:System.Windows.Forms.Control.Padding%2A>値を考慮します。  
  
4.  手順 2. および 3. を繰り返して、<xref:System.Windows.Forms.AnchorStyles.Top>と<xref:System.Windows.Forms.AnchorStyles.Bottom>スタイル。  
  
## <a name="setting-row-and-column-properties"></a>設定の行と列のプロパティ  
 使用して行および列の個別のプロパティを設定することができます、<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>と<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>コレクション。  
  
#### <a name="to-set-row-and-column-properties"></a>行と列のプロパティを設定するには  
  
1.  選択、<xref:System.Windows.Forms.TableLayoutPanel>内の制御、 **Windows フォーム デザイナー**です。  
  
2.  **プロパティ**開いているウィンドウ、<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>省略記号をクリックして、コレクション (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタン次に、**列**エントリです。  
  
3.  最初の列を選択しの値を変更、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティを<xref:System.Windows.Forms.SizeType.AutoSize>です。 をクリックして**OK**変更を確定します。 最初の列の幅が、それに合わせて短くなることに注意してください、<xref:System.Windows.Forms.Button>コントロール。 列の幅がサイズ変更可能なことはありませんにも注意してください。  
  
4.  **プロパティ**ウィンドウを開いた、<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>コレクションし、最初の列を選択します。 値を変更、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティを<xref:System.Windows.Forms.SizeType.Percent>です。 をクリックして**OK**変更を確定します。 サイズ変更、<xref:System.Windows.Forms.TableLayoutPanel>の幅を制御し、最初の列の幅が展開することに注意してください。 サイズ変更、<xref:System.Windows.Forms.TableLayoutPanel>小規模な幅を制御し、最初の列にボタンがセルに合わせてサイズことに注意してください。 また、列の幅がサイズ変更可能なことに注意してください。  
  
5.  **プロパティ**ウィンドウを開いた、<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>コレクションと表示されているすべての列を選択します。 値の設定すべて<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティを<xref:System.Windows.Forms.SizeType.Percent>です。 をクリックして**OK**変更を確定します。 繰り返し、<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>コレクション。  
  
6.  サイズ変更ハンドル上隅のいずれかを取得し、サイズの高さと幅を変更する、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 行および列としてサイズが変更されること、<xref:System.Windows.Forms.TableLayoutPanel>コントロールのサイズを変更します。 行と列が水平方向サイズ変更可能なと垂直方向サイズ変更ハンドルにも注意してください。  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>コントロールで行または列のまたがりメモリ割り当てください。  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、デザイン時にコントロールをいくつかの新しいプロパティを追加します。 これらのプロパティの 2 つは`RowSpan`と`ColumnSpan`です。 コントロールの範囲より 1 つの行または列にするのには、これらのプロパティを使用できます。  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>コントロールで行または列にまたがること  
  
1.  選択、<xref:System.Windows.Forms.Button>コントロールの最初の行の最初の列です。  
  
2.  **プロパティ**windows での値を変更する、`ColumnSpan`プロパティを**2**です。 なお、<xref:System.Windows.Forms.Button>コントロールは、最初の列と 2 番目の列を入力します。 この変更に対応する追加の行が追加されているよりも注意してください。  
  
3.  手順 2. を繰り返します、`RowSpan`プロパティです。  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>ツールボックスでのダブルクリックによるコントロールの挿入  
 設定することができます、<xref:System.Windows.Forms.TableLayoutPanel>コントロール内のコントロールをダブルクリックして、**ツールボックス**です。  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>ツールボックスでダブルクリックしてコントロールを挿入するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。  
  
2.  <xref:System.Windows.Forms.Button> ツールボックス **の**コントロール アイコンをダブルクリックします。 新しいボタン コントロールが含まれているメモ、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの最初のセル。  
  
3.  **ツールボックス**でさらにいくつかのコントロールをダブルクリックします。 新しいコントロールに順次表示されることに注意してください、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの使用されていないセル。 また、<xref:System.Windows.Forms.TableLayoutPanel>コントロールは、新しいコントロールに合わせてセルがない場合に拡張します。  
  
## <a name="automatic-handling-of-overflows"></a>オーバーフローの自動処理  
 ときにコントロールを挿入する場合は、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが不足する空のセル、新しいコントロールのです。 <xref:System.Windows.Forms.TableLayoutPanel>コントロールこのような状況を自動的に処理のセルの数を増やすことで。  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>オーバーフローの自動処理を確認するには  
  
1.  まだ空のセルがある場合、<xref:System.Windows.Forms.TableLayoutPanel>制御、新規の挿入を続行<xref:System.Windows.Forms.Button>まで制御、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが完全にします。  
  
2.  1 回、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが完全をダブルクリックして、<xref:System.Windows.Forms.Button>のアイコン、**ツールボックス**別を挿入する<xref:System.Windows.Forms.Button>コントロール。 なお、<xref:System.Windows.Forms.TableLayoutPanel>コントロールは、新しいコントロールに合わせて新しいセルを作成します。 さらに、いくつかのコントロールを挿入し、サイズ変更動作を確認します。  
  
3.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールの <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> プロパティの値を <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize> に変更します。 ダブルクリックして、<xref:System.Windows.Forms.Button>のアイコン、**ツールボックス**を挿入する<xref:System.Windows.Forms.Button>まで制御、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが完全にします。 ダブルクリックして、<xref:System.Windows.Forms.Button>のアイコン、**ツールボックス**もう一度です。 エラー メッセージが表示されることに注意してください、 **Windows フォーム デザイナー**追加の行と列を作成できないことを通知します。  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>アウトラインの描画によるコントロールの挿入  
 コントロールを挿入することができます、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、セルにアウトラインを描画してそのサイズを指定します。  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>アウトラインを描画してコントロールを挿入するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。  
  
2.  **ツールボックス**で <xref:System.Windows.Forms.Button> コントロール アイコンをクリックします。 フォームにドラッグしないでください。  
  
3.  マウス ポインターを重ねる、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 ポインターが <xref:System.Windows.Forms.Button> コントロール アイコンが付いた十字カーソルに変わることにご注意ください。  
  
4.  マウス ボタンを押したままにします。  
  
5.  マウス ポインターをドラッグして、 <xref:System.Windows.Forms.Button> コントロールのアウトラインを描画します。 適切なサイズのアウトラインを描画したら、マウス ボタンを離します。 なお、<xref:System.Windows.Forms.Button>コントロールのアウトラインを描画するセルにコントロールを作成します。  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>セル内の複数のコントロールが許可されていません  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、1 つのセルの 1 つだけの子コントロールを含めることができます。  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>セル内の複数のコントロールは使用できませんを示すために  
  
-   ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、使用中のセルの 1 つにドロップします。 なお、<xref:System.Windows.Forms.TableLayoutPanel>コントロール削除はできません、<xref:System.Windows.Forms.Button>占有されたセルにコントロールを。  
  
## <a name="swapping-controls"></a>コントロールの交換  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールでは、次の 2 つの異なるセルを使用していたコントロールを交換することができます。  
  
#### <a name="to-swap-controls"></a>コントロールをスワップするには  
  
-   1 つをドラッグして、<xref:System.Windows.Forms.Button>コントロールから占有セルおよび他の占有されたセルにドロップします。 他の 2 つのコントロールを 1 つのセルから移動することに注意してください。  
  
## <a name="next-steps"></a>次の手順  
 レイアウト パネルとコントロールを組み合わせて使用すると、複雑なレイアウトを作成できます。 さらに詳しく調べるための推奨事項を次に示します。  
  
-   いずれかのサイズ、<xref:System.Windows.Forms.Button>より大きなサイズの注、レイアウトに影響を制御します。  
  
-   複数のコントロールの選択範囲を貼り付け、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、コントロールを挿入する方法に注意してください。  
  
-   レイアウト パネルには、別のレイアウト パネルを含めることができます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールを既存のコントロールにドロップしてみます。  
  
-   ドック、<xref:System.Windows.Forms.TableLayoutPanel>親フォームを制御します。 フォームのサイズを変更し、レイアウトの変化を確認します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Microsoft Windows ユーザー エクスペリエンス、ユーザー インターフェイスの開発者とデザイナーのための公式のガイドライン。Redmond、WA: Microsoft Press、1999 年。(USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [チュートリアル: データ入力用のサイズ変更可能な Windows フォームの作成](http://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab)  
 [チュートリアル: ローカライズ可能な Windows フォームの作成](http://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c)  
 [TableLayoutPanel コントロールの推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [方法: Windows フォーム上のコントロールをドッキングする](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [方法: Windows フォームにコントロールを固定する](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
