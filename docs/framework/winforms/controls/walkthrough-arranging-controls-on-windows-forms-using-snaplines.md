---
title: "チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be514f435b787c770eca114d42bee5c1424a40c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置
フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。 Windows フォーム デザイナーでは、これを実現するさまざまなレイアウト ツールを提供します。 最も重要な 1 つは、<xref:System.Windows.Forms.Design.Behavior.SnapLine>機能します。  
  
 スナップ線では、他のコントロールとコントロールを整列する位置を正確を示します。 Windows ユーザー インターフェイスのガイドラインに従って、コントロール間の余白の推奨距離も示します。 詳細については、「[ユーザー インターフェイスの設計と開発](http://go.microsoft.com/FWLink/?LinkId=83878)です。  
  
 スナップ線しやすいように、鮮明でコントロールを整列させるプロフェッショナルな外観と動作 (ルック アンド フィール)。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   スペーシングとスナップ線を使用して、コントロールの配置  
  
-   フォームまたはコンテナーのマージンに整列  
  
-   グループ化されたコントロールに合わせて調整  
  
-   スナップ線を使用して、サイズのアウトラインでコントロールを配置するには  
  
-   ツールボックスからコントロールをドラッグしたときに、スナップ線を使用します。  
  
-   スナップ線を使用して、コントロールのサイズを変更します。  
  
-   コントロールのテキストとラベルの整列  
  
-   キーボード ナビゲーションをスナップ線を使用します。  
  
-   スナップ線とレイアウト パネル  
  
-   スナップ線を無効にします。  
  
 完了したら、レイアウトにスナップ線機能が果たす役割について理解があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  "SnaplineExample"と呼ばれる Windows ベースのアプリケーション プロジェクトを作成します。 詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  フォーム デザイナーでフォームを選択します。  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>スペーシングとスナップ線を使用して、コントロールの配置  
 スナップ線では、フォーム上のコントロールを配置するための正確かつ直感的な方法を提供します。 別のコントロールやコントロールのセットは整列する位置の近くまたは複数の選択したコントロールを移動するときに表示されます。 選択内容は「スナップ」推奨位置に過去の他のコントロールに移動するとします。  
  
#### <a name="to-arrange-controls-using-snaplines"></a>スナップ線を使用してコントロールを配置するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。  
  
2.  移動、<xref:System.Windows.Forms.Button>フォームの右下隅にコントロールできます。 注スナップ線として表示される<xref:System.Windows.Forms.Button>コントロール下およびフォームの右側の境界線のアプローチです。 これらのスナップ線は、コントロールの枠線とフォームの推奨される距離を表示します。  
  
3.  移動、<xref:System.Windows.Forms.Button>注スナップ線が表示される、フォームの境界線を制御します。 完了したら、移動、<xref:System.Windows.Forms.Button>フォームの中央付近コントロール。  
  
4.  別のドラッグ<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。  
  
5.  2 番目の移動<xref:System.Windows.Forms.Button>が最初にほぼレベルになるまでを制御します。 両方のボタンのテキストのベースラインに表示されるスナップ線をメモし、移動中のコントロールが他のコントロールにレベルだけである位置にスナップすることに注意してください。  
  
6.  2 番目の移動<xref:System.Windows.Forms.Button>最初のすぐ上に配置されるまでを制御します。 スナップ線が両方のボタンの左と右の端に表示され、コントロールが他のコントロールを正確に配置される位置に移動のスナップを注意してください。  
  
7.  いずれかを選択、<xref:System.Windows.Forms.Button>を制御し、ほぼに触れることまで、その他の近くに移動します。 それらの間に表示されるスナップ線に注意してください。 推奨される、コントロールの境界線間この距離です。 また、移動中のコントロールがこの位置にスナップすることに注意してください。  
  
8.  2 つをドラッグして<xref:System.Windows.Forms.Panel>から制御、**ツールボックス**フォーム上にします。  
  
9. いずれかの移動、<xref:System.Windows.Forms.Panel>が最初にほぼレベルになるまでを制御します。 スナップ線が両方のコントロールの上部と下部の端に沿って表示され、移動中のコントロールが他のコントロールにレベルだけである位置にスナップすることに注意してください。 注意してください。  
  
## <a name="aligning-to-form-and-container-margins"></a>フォームまたはコンテナーのマージンに整列  
 スナップ線を使用して、一貫した方法でコントロールをフォームやコンテナーのマージンを配置するのに役立ちます。  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>フォームとコンテナーの余白にコントロールを配置するには  
  
1.  いずれかを選択、<xref:System.Windows.Forms.Button>を制御し、スナップ線が表示されるまで、フォームの右罫線の近くに移動します。 右罫線のスナップ線の距離は、コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティと、フォームの<xref:System.Windows.Forms.Control.Padding%2A>プロパティの値。  
  
> [!NOTE]
>  場合、フォームの<xref:System.Windows.Forms.Control.Padding%2A>0,0,0,0 にプロパティが設定されている、Windows フォーム デザイナーは、フォームをシャドウ<xref:System.Windows.Forms.Control.Padding%2A>9,9,9,9 の値。 この動作をオーバーライドするには、0,0,0,0 以外の値を割り当てます。  
  
1.  値を変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Margin%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.All%2A>プロパティを 0 にします。 詳細については、「[チュートリアル: レイアウトを Windows フォーム コントロールを Padding Margin、および AutoSize プロパティ](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)です。  
  
2.  移動、<xref:System.Windows.Forms.Button>スナップ線が表示されるまでフォームの右罫線の近くに制御します。 この距離は、フォームの値によって指定された<xref:System.Windows.Forms.Control.Padding%2A>プロパティです。  
  
3.  ドラッグ、<xref:System.Windows.Forms.GroupBox>から制御、**ツールボックス**フォーム上にします。  
  
4.  値を変更、<xref:System.Windows.Forms.GroupBox>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、 <xref:System.Windows.Forms.Padding.All%2A> 10 プロパティです。  
  
5.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.GroupBox>コントロール。  
  
6.  移動、<xref:System.Windows.Forms.Button>の右側の境界線に近いコントロール、<xref:System.Windows.Forms.GroupBox>スナップ線が表示されるまでを制御します。 移動、<xref:System.Windows.Forms.Button>内の制御、<xref:System.Windows.Forms.GroupBox>コントロールと、スナップ線が表示されます。  
  
## <a name="aligning-to-grouped-controls"></a>グループ化されたコントロールに合わせて調整  
 グループ化されたコントロールを配置するスナップ線を使用することができます内で制御と同様、<xref:System.Windows.Forms.GroupBox>コントロール。  
  
#### <a name="to-align-to-grouped-controls"></a>グループ化されたコントロールに合わせて調整するには  
  
1.  フォーム上のコントロールの 2 つを選択します。 選択範囲を移動し、選択内容とその他のコントロール間に表示されるスナップ ラインに注意してください。  
  
2.  ドラッグ、<xref:System.Windows.Forms.GroupBox>から制御、**ツールボックス**フォーム上にします。  
  
3.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.GroupBox>コントロール。  
  
4.  いずれかを選択、<xref:System.Windows.Forms.Button>を制御し、移動、<xref:System.Windows.Forms.GroupBox>コントロール。 注スナップ線の端に表示される<xref:System.Windows.Forms.GroupBox>コントロール。 なお、スナップ線の端に表示されますが、<xref:System.Windows.Forms.Button>コントロールに含まれています、<xref:System.Windows.Forms.GroupBox>コントロール。 コンテナー コントロールの子であるコントロールでは、スナップ線もサポートします。  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>スナップ線を使用して、サイズのアウトラインでコントロールを配置するには  
 スナップ線に整列させることは、ときに最初に配置するにフォームを制御します。  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>によって、サイズのアウトライン コントロールを配置するスナップ線を使用するには  
  
1.  **ツールボックス**で <xref:System.Windows.Forms.Button> コントロール アイコンをクリックします。 フォームにドラッグしないでください。  
  
2.  フォームのデザイン画面上には、マウス ポインターを移動します。 ポインターが <xref:System.Windows.Forms.Button> コントロール アイコンが付いた十字カーソルに変わることにご注意ください。 なお、表示されるスナップ ラインの位置を揃えるを提案する、<xref:System.Windows.Forms.Button>コントロール。  
  
3.  マウス ボタンを押したままにします。  
  
4.  フォーム上のマウス ポインターをドラッグします。 アウトラインを描画すること、位置、およびコントロールのサイズを示すに注意してください。  
  
5.  フォーム上の別のコントロールと揃うまでドラッグします。 整列を示すスナップ線が表示されることに注意してください。  
  
6.  マウスのボタンを離します。 アウトラインで示されるサイズと位置にコントロールを作成するとします。  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>ツールボックスからコントロールをドラッグしたときに、スナップ線を使用します。  
 スナップ線に整列させることを制御からそれらをドラッグすると、**ツールボックス**フォーム上にします。  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>ツールボックスからコントロールをドラッグするときに、スナップ線を使用するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にマウス ボタンを押したままです。  
  
2.  フォームのデザイン画面上には、マウス ポインターを移動します。 位置を示すために、ポインターを変更ことに注意してください。 新しい<xref:System.Windows.Forms.Button>コントロールが作成されます。  
  
3.  フォーム上のマウス ポインターをドラッグします。 位置を揃えるに表示されるスナップ線に注意してください、<xref:System.Windows.Forms.Button>コントロール。 その他のコントロールと整合する位置を検索します。  
  
4.  マウスのボタンを離します。 スナップ線によって示される位置にあるコントロールを作成します。  
  
## <a name="resizing-controls-using-snaplines"></a>スナップ線を使用して、コントロールのサイズを変更します。  
 スナップ線を使用するようにサイズ変更してコントロールを配置します。  
  
#### <a name="to-resize-a-control-using-snaplines"></a>スナップ線を使用して、コントロールのサイズを変更するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。  
  
2.  サイズ変更、<xref:System.Windows.Forms.Button>上隅をドラッグしてサイズ変更ハンドルのいずれかを行ったによって制御します。 詳細については、「[する方法: Windows フォームでのコントロールのサイズを変更する](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)です。  
  
3.  1 つまでのサイズ変更ハンドルをドラッグして、<xref:System.Windows.Forms.Button>コントロールの枠線が別のコントロールに揃えて配置します。 スナップ線が表示されることに注意してください。 また、サイズ変更ハンドルがスナップ線によって示される位置にスナップすることに注意してください。  
  
4.  サイズ変更、<xref:System.Windows.Forms.Button>いろいろな方向を制御し、さまざまなコントロールをサイズ変更ハンドルを揃えます。 配置を示すためにさまざまな向きでスナップ線を表示する方法に注意してください。  
  
## <a name="aligning-a-label-to-a-controls-text"></a>コントロールのテキストとラベルの整列  
 一部のコントロールは、他のコントロールに表示されるテキストを配置するスナップ線を提供します。  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>コントロールのテキストにラベルを整列するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TextBox>から制御、**ツールボックス**フォーム上にします。 ドロップすると、<xref:System.Windows.Forms.TextBox>フォーム上に制御し、スマート タグ グリフをクリックし、選択、 **textBox1 にテキストを設定**オプション。 詳細については、「[チュートリアル: を実行する一般的なタスクを使用してスマート タグに Windows フォーム コントロール](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)です。  
  
2.  ドラッグ、<xref:System.Windows.Forms.Label>から制御、**ツールボックス**フォーム上にします。  
  
3.  <xref:System.Windows.Forms.Label> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true` に変更します。 表示テキストに合わせてコントロールの枠線を調整することに注意してください。  
  
4.  移動、<xref:System.Windows.Forms.Label>コントロールの左側に、<xref:System.Windows.Forms.TextBox>を制御するための下部エッジに揃えられます、<xref:System.Windows.Forms.TextBox>コントロール。 2 つのコントロールの下端に沿って表示されるスナップ線に注意してください。  
  
5.  移動、<xref:System.Windows.Forms.Label>コントロールまで、少し上昇、<xref:System.Windows.Forms.Label>テキストと<xref:System.Windows.Forms.TextBox>テキストを配置します。 スタイルの異なるスナップ線が表示されたら、両方のコントロールのテキスト フィールドを配置するときを示すことに注意してください。  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>キーボード ナビゲーションをスナップ線を使用します。  
 スナップ線に整列させることは、配置、キーボードの矢印キーを使用するを制御します。  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>キーボード ナビゲーションをスナップ線を使用するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。 フォームの左上隅に配置します。  
  
2.  Ctrl キーを押しながら下方向のキーを押します。 コントロールが最初の使用可能な水平方向の配置位置をフォーム下へ移動することに注意してください。  
  
3.  コントロールがフォームの下部に達するまで、ctrl キーを押しながら下方向キーを押します。 フォームの下方向に移動するときに占有する位置に注意してください。  
  
4.  Ctrl キーを押しながら右方向のキーを押します。 コントロールをフォーム上で最初の使用可能な縦方向の配置位置を移動するに注意してください。  
  
5.  コントロールがフォームの端に達するまで、ctrl キーを押しながら右方向キーを押します。 フォーム全体を移動する際に占有する位置に注意してください。  
  
6.  方向キーの組み合わせでコントロールをフォーム上を移動します。 コントロールが占める位置とそれに伴うスナップ線に注意してください。  
  
7.  サイズを変更するには、shift キーを押しながら任意の方向キーを押して、 <xref:System.Windows.Forms.Button> 1 ピクセルずつコントロール。  
  
8.  サイズを変更するには、CTRL + SHIFT + 任意の方向キーを押して、<xref:System.Windows.Forms.Button>スナップ線単位で制御します。  
  
## <a name="snaplines-and-layout-panels"></a>スナップ線とレイアウト パネル  
 レイアウト パネル内では、スナップ線が無効になります。  
  
#### <a name="to-selectively-disable-snaplines"></a>スナップ線を選択的に無効にするには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。  
  
2.  <xref:System.Windows.Forms.Button> ツールボックス **の**コントロール アイコンをダブルクリックします。 新しいボタン コントロールが含まれているメモ、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの最初のセル。  
  
3.  ダブルクリックして、<xref:System.Windows.Forms.Button>コントロールのアイコン、**ツールボックス**さらに 2 回です。 これにより、1 つの空のセル、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
4.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**の空のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 スナップ線が表示されないことに注意してください。  
  
5.  ドラッグ、<xref:System.Windows.Forms.Button>の制御、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、移動、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 スナップ線が再度表示されることに注意してください。  
  
## <a name="disabling-snaplines"></a>スナップ線を無効にします。  
 スナップ ガイドラインは、既定で有効にします。 スナップ線を選択的に、無効にできますか、デザイン環境で無効にできます。  
  
#### <a name="to-selectively-disable-snaplines"></a>スナップ線を選択的に無効にするには  
  
-   ALT キーを押して、コントロールをフォーム上の移動中にします。  
  
     スナップ線が表示されませんが、コントロールが潜在的な配置位置にスナップいないことに注意してください。  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>デザイン環境のスナップ線を無効にするには  
  
1.  **ツール**メニューを開き、**オプション** ダイアログ ボックス。 Windows フォーム デザイナー ダイアログ ボックスを開きます。 詳細については、[[全般]、Windows フォーム デザイナー、オプション ダイアログ ボックス](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)です。  
  
2.  選択、**全般**ノード。 **レイアウト モード**セクションからの選択を変更**スナップ線**に**SnapToGrid**です。  
  
3.  設定を適用するには、[ok] をクリックします。  
  
4.  フォーム上のコントロールを選択し、その他のコントロールを移動します。 スナップ線が表示されないことに注意してください。  
  
## <a name="next-steps"></a>次の手順  
 スナップ ガイドラインは、直観的に、フォームのコントロールの配置を提供します。 さらに詳しく調べるための推奨事項を次に示します。  
  
-   入れ子の再試行、<xref:System.Windows.Forms.GroupBox>中に別のコントロール<xref:System.Windows.Forms.GroupBox>コントロール。 場所、<xref:System.Windows.Forms.Button>子内のコントロール<xref:System.Windows.Forms.GroupBox>制御、および親内の別<xref:System.Windows.Forms.GroupBox>コントロール。 移動、<xref:System.Windows.Forms.Button>スナップ線がコンテナーの境界を越える方法を表示するには、約コントロール。  
  
-   列を作成<xref:System.Windows.Forms.TextBox>コントロールとの対応する列<xref:System.Windows.Forms.Label>コントロール。 値を設定、<xref:System.Windows.Forms.Label>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`です。 移動するスナップ線を使用して、<xref:System.Windows.Forms.Label>ためのテキストに、表示されるテキストの配置を制御、<xref:System.Windows.Forms.TextBox>コントロール。  
  
 Windows ユーザー インターフェイスの設計方法については、ブックを参照してください。 *Microsoft Windows ユーザー エクスペリエンス、ユーザー インターフェイスの開発者とデザイナーの Official Guidelines* Redmond、WA: Microsoft Press、1999 年。 (USBN: 0-7356-0566-1)。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [チュートリアル: Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
