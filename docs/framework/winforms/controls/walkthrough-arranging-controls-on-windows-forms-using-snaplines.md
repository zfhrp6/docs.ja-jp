---
title: "チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置 | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 配置 (スナップ線を使用した)"
  - "SnapLine クラス, チュートリアル"
  - "スナップ線, 配置 (Windows フォーム コントロールを)"
  - "Windows フォーム コントロール, 配置"
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置
フォーム上にコントロールを正確に配置することは、多くのアプリケーションで重要度の高い処理です。  Windows フォーム デザイナーには、そのためのさまざまなレイアウト ツールが用意されています。  その中で最も重要なツールの 1 つが <xref:System.Windows.Forms.Design.Behavior.SnapLine> 機能です。  
  
 スナップ線は、コントロールを他のコントロールと整列させる位置を正確に示します。  また、Windows ユーザー インターフェイスのガイドラインで指定されている、コントロール間のマージンの推奨距離も示します。  詳細については、「[User Interface Design and Development \(ユーザー インターフェイスのデザインと開発\)](http://go.microsoft.com/FWLink/?LinkId=83878)」を参照してください。  
  
 スナップ線を使用すると、簡単にコントロールを整列させることができ、鮮明でプロフェッショナルな外観と動作を実現できます。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   スナップ線を使用したコントロールのスペーシングと配置  
  
-   フォームまたはコンテナーのマージンを使用した整列  
  
-   グループ化されたコントロールとの整列  
  
-   スナップ線を使用した、サイズのアウトラインによるコントロールの配置  
  
-   ツールボックスからコントロールをドラッグするときのスナップ線の使用  
  
-   スナップ線を使用したコントロールのサイズ変更  
  
-   コントロールのテキストとラベルの整列  
  
-   キーボードによる移動時のスナップ線の使用  
  
-   スナップ線とレイアウト パネル  
  
-   スナップ線の無効化  
  
 ここでは、スナップ線機能がレイアウトに果たす役割について理解します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### プロジェクトを作成するには  
  
1.  "SnaplineExample" という名前の Windows ベース アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  フォーム デザイナーでフォームを選択します。  
  
## スナップ線を使用したコントロールのスペーシングと配置  
 スナップ線を使用すると、正確かつ直観的にコントロールをフォームに配置できます。  スナップ線は、選択した単数または複数のコントロールを、他のコントロールやコントロール セットと整列する位置の近くに移動すると表示されます。  選択したコントロールが他のコントロールを通過するとき、推奨位置に "スナップ" します。  
  
#### スナップ線を使用してコントロールを配置するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.Button> コントロールをドラッグします。  
  
2.  <xref:System.Windows.Forms.Button> コントロールをフォームの右下隅に移動します。  <xref:System.Windows.Forms.Button> コントロールがフォームの下側と右側の境界線に近づくと、スナップ線が表示されます。  これらのスナップ線は、コントロールの境界線からフォームの境界線までの推奨距離を表します。  
  
3.  <xref:System.Windows.Forms.Button> コントロールをフォームの境界線付近であちこちに移動し、スナップ線がどこで表示されるかを確認します。  この操作を終えたら、<xref:System.Windows.Forms.Button> コントロールをフォームの中心付近に移動します。  
  
4.  **ツールボックス**から別の <xref:System.Windows.Forms.Button> コントロールをフォームにドラッグします。  
  
5.  この 2 つ目の <xref:System.Windows.Forms.Button> コントロールが、最初のコントロールとほぼ水平の位置関係になるように移動します。  両方のボタンのテキスト ベースラインにスナップ線が表示され、移動中のコントロールが、最初のコントロールの真横にスナップします。  
  
6.  2 つ目の <xref:System.Windows.Forms.Button> コントロールを最初のコントロールのすぐ上に移動します。  両方のボタンの左端と右端に沿ってスナップ線が表示され、移動中のコントロールが、最初のコントロールの真上にスナップします。  
  
7.  <xref:System.Windows.Forms.Button> コントロールのどちらかを選択し、もう 1 つのコントロールにほぼ接触するまで近づけます。  両方のコントロールの間にスナップ線が表示されます。  この距離が、これらのコントロールの境界間の推奨距離になります。  また、移動中のコントロールがこの位置にスナップすることも確認してください。  
  
8.  **ツールボックス**から 2 つの <xref:System.Windows.Forms.Panel> コントロールをフォームにドラッグします。  
  
9. 1 つの <xref:System.Windows.Forms.Panel> コントロールを、もう 1 つのコントロールとほぼ水平の位置関係になるように移動します。  両方のコントロールの上端と下端に沿ってスナップ線が表示され、移動中のコントロールが、もう 1 つのコントロールの真横にスナップします。  
  
## フォームまたはコンテナーのマージンを使用した整列  
 スナップ線を使用すると、一貫した方法でフォームやコンテナーのマージンを使用してコントロールを整列させることができます。  
  
#### フォームやコンテナーのマージンを使用してコントロールを整列させるには  
  
1.  <xref:System.Windows.Forms.Button> コントロールを 1 つ選択し、スナップ線が表示されるまで、フォームの右側の境界線に近づけます。  右側の境界線とスナップ線の距離は、コントロールの <xref:System.Windows.Forms.Control.Margin%2A> プロパティ値とフォームの <xref:System.Windows.Forms.Control.Padding%2A> プロパティ値の合計です。  
  
> [!NOTE]
>  フォームの <xref:System.Windows.Forms.Control.Padding%2A> プロパティを 0,0,0,0 に設定すると、Windows フォーム デザイナーでは、フォームの <xref:System.Windows.Forms.Control.Padding%2A> 値が暗黙的に 9,9,9,9 として解釈されます。  この動作をオーバーライドするには、0,0,0,0 以外の値を割り当てます。  
  
1.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Margin%2A> プロパティの値を変更します。これを行うには、**\[プロパティ\]** ウィンドウで <xref:System.Windows.Forms.Control.Margin%2A> エントリを展開し、<xref:System.Windows.Forms.Padding.All%2A> プロパティを 0 に設定します。  詳細については、「[チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)」を参照してください。  
  
2.  スナップ線が表示されるまで、<xref:System.Windows.Forms.Button> コントロールをフォームの右側の境界線に近づけます。  この距離は、フォームの <xref:System.Windows.Forms.Control.Padding%2A> プロパティの値によって決まります。  
  
3.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.GroupBox> コントロールをドラッグします。  
  
4.  <xref:System.Windows.Forms.GroupBox> コントロールの <xref:System.Windows.Forms.Control.Padding%2A> プロパティの値を変更します。これを行うには、**\[プロパティ\]** ウィンドウで <xref:System.Windows.Forms.Control.Padding%2A> エントリを展開し、<xref:System.Windows.Forms.Padding.All%2A> プロパティを 10 に設定します。  
  
5.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.GroupBox> コントロールにドラッグします。  
  
6.  スナップ線が表示されるまで、<xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.GroupBox> コントロールの右側の境界線に近づけます。  <xref:System.Windows.Forms.GroupBox> コントロール内で <xref:System.Windows.Forms.Button> を移動し、スナップ線がどこで表示されるかを確認します。  
  
## グループ化されたコントロールとの整列  
 スナップ線を使用すると、<xref:System.Windows.Forms.GroupBox> コントロール内の コントロールだけでなく、グループ化されたコントロールも整列させることができます。  
  
#### グループ化されたコントロールと整列させるには  
  
1.  フォーム上のコントロールを 2 つ選択します。  選択したコントロールをあちこちに移動し、選択したコントロールと他のコントロールの間に表示されるスナップ線を確認します。  
  
2.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.GroupBox> コントロールをドラッグします。  
  
3.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.GroupBox> コントロールにドラッグします。  
  
4.  <xref:System.Windows.Forms.Button> コントロールの 1 つを選択し、<xref:System.Windows.Forms.GroupBox> コントロールの周囲であちこちに移動します。  <xref:System.Windows.Forms.GroupBox> コントロールの各端にスナップ線が表示されます。  また、<xref:System.Windows.Forms.GroupBox> コントロールに含まれている <xref:System.Windows.Forms.Button> コントロールの各端にもスナップ線が表示されます。  コンテナー コントロール内の子コントロールもスナップ線をサポートします。  
  
## スナップ線を使用した、サイズのアウトラインによるコントロールの配置  
 スナップ線を使用すると、コントロールを初めてフォームに配置する際に簡単に整列させることができます。  
  
#### スナップ線を使用し、サイズのアウトラインを描いてコントロールを配置するには  
  
1.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロール アイコンをクリックします。  フォームにドラッグしないでください。  
  
2.  マウス ポインターをフォームのデザイン サーフェイスに置きます。  ポインターが <xref:System.Windows.Forms.Button> コントロール アイコンが付いた十字カーソルに変わります。  また、<xref:System.Windows.Forms.Button> コントロールの推奨整列位置を示すスナップ線も表示されます。  
  
3.  マウス ボタンを押したままにします。  
  
4.  マウス ポインターをフォーム上でドラッグします。  コントロールの位置とサイズを示すアウトラインが描画されます。  
  
5.  フォーム上の別のコントロールに整列する位置までポインターをドラッグします。  スナップ線が表示され、整列を示します。  
  
6.  マウスのボタンを離します。  アウトラインで示された位置とサイズでコントロールが作成されます。  
  
## ツールボックスからコントロールをドラッグするときのスナップ線の使用  
 スナップ線を使用すると、**ツールボックス**からフォームにドラッグしたコントロールを簡単に整列させることができます。  
  
#### ツールボックスからコントロールをドラッグするときにスナップ線を使用するには  
  
1.  **ツールボックス**から <xref:System.Windows.Forms.Button> コントロールをフォームにドラッグし、マウス ボタンを押したままにします。  
  
2.  マウス ポインターをフォームのデザイン サーフェイスに置きます。  ポインターの形が変わり、新しい <xref:System.Windows.Forms.Button> コントロールが作成される位置を示します。  
  
3.  マウス ポインターをフォーム上でドラッグします。  <xref:System.Windows.Forms.Button> コントロールの推奨整列位置を示すスナップ線が表示されます。  他のコントロールと整列する位置を見つけます。  
  
4.  マウスのボタンを離します。  スナップ線で示された位置にコントロールが作成されます。  
  
## スナップ線を使用したコントロールのサイズ変更  
 スナップ線を使用すると、コントロールのサイズを変更したときに簡単に整列させることができます。  
  
#### スナップ線を使用してコントロールのサイズを変更するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.Button> コントロールをドラッグします。  
  
2.  <xref:System.Windows.Forms.Button> コントロールの隅にあるサイズ変更ハンドルのいずれかをドラッグして、コントロールのサイズを変更します。  詳細については、「[方法 : Windows フォーム上のコントロールのサイズを変更する](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)」を参照してください。  
  
3.  <xref:System.Windows.Forms.Button> コントロールの境界線のいずれかが他のコントロールと整列するまでサイズ変更ハンドルをドラッグします。  スナップ線が表示されるのを確認します。  また、サイズ変更ハンドルがスナップ線で示された位置にスナップすることも確認します。  
  
4.  さまざまな方向に <xref:System.Windows.Forms.Button> コントロールのサイズを変更し、サイズ変更ハンドルを別のコントロールに整列させます。  スナップ線がさまざまな方向に表示されて、整列を示すことを確認してください。  
  
## コントロールのテキストとラベルの整列  
 一部のコントロールでは、スナップ線を利用して、他のコントロールを表示テキストに合わせて整列させることができます。  
  
#### ラベルとコントロールのテキストを整列させるには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TextBox> コントロールをドラッグします。  <xref:System.Windows.Forms.TextBox> コントロールをフォームにドロップしたら、スマート タグ グリフをクリックし、**\[textBox1 にテキストを設定\]** をクリックします。  詳細については、「[チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)」を参照してください。  
  
2.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.Label> コントロールをドラッグします。  
  
3.  <xref:System.Windows.Forms.Label> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true` に変更します。  コントロールの境界線が表示テキストに合わせて調整されます。  
  
4.  <xref:System.Windows.Forms.Label> コントロールを <xref:System.Windows.Forms.TextBox> コントロールの左に移動し、<xref:System.Windows.Forms.TextBox> コントロールの下端に合わせて配置します。  2 つのコントロールの下端に沿ってスナップ線が表示されます。  
  
5.  <xref:System.Windows.Forms.Label> のテキストと <xref:System.Windows.Forms.TextBox> のテキストが整列するまで、<xref:System.Windows.Forms.Label> コントロールをわずかに上に移動します。  両方のコントロールのテキスト フィールドが整列すると、スタイルの異なるスナップ線が表示されます。  
  
## キーボードによる移動時のスナップ線の使用  
 スナップ線を使用すると、キーボードの方向キーを使用してコントロールを配置するときに、コントロールを簡単に整列させることができます。  
  
#### キーボードによる移動時にスナップ線を使用するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.Button> コントロールをドラッグします。  このコントロールをフォームの左上隅に配置します。  
  
2.  Ctrl キーを押しながら↓キーを押します。  コントロールがフォーム内で下に移動し、使用できる最初の整列位置に置かれます。  
  
3.  コントロールがフォームの下端に到達するまで、Ctrl キーを押しながら↓キーを押し続けます。  コントロールがフォーム内を下に移動するときに占有する位置を確認します。  
  
4.  Ctrl キーを押しながら→キーを押します。  コントロールがフォーム上で右に移動し、使用できる最初の整列位置に置かれます。  
  
5.  コントロールがフォームの右端に到達するまで、Ctrl キーを押しながら→キーを押し続けます。  コントロールがフォーム内を右に移動するときに占有する位置を確認します。  
  
6.  方向キーを組み合わせて使用してコントロールをフォーム上で移動します。  コントロールが占有する位置と表示されるスナップ線を確認します。  
  
7.  Shift キーを押しながら任意の方向キーを押して、<xref:System.Windows.Forms.Button> コントロールのサイズを 1 ピクセルずつ変更します。  
  
8.  Ctrl キーと Shift キーを押しながら任意の方向キーを押して、<xref:System.Windows.Forms.Button> コントロールのサイズをスナップ線のインクリメントで変更します。  
  
## スナップ線とレイアウト パネル  
 スナップ線はレイアウト パネル内で無効にできます。  
  
#### スナップ線を選択的に無効にするには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをドラッグします。  
  
2.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロール アイコンをダブルクリックします。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールの最初のセルに新しいボタン コントロールが表示されます。  
  
3.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロール アイコンをさらに 2 回ダブルクリックします。  これで、<xref:System.Windows.Forms.TableLayoutPanel> コントロール内の空のセルは 1 つになります。  
  
4.  **ツールボックス**から <xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールの空のセルにドラッグします。  スナップ線が表示されないことを確認します。  
  
5.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールの外に <xref:System.Windows.Forms.Button> コントロールをドラッグし、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの周囲を移動します。  スナップ線が再び表示されるのを確認します。  
  
## スナップ線の無効化  
 スナップ線は既定で有効です。  スナップ線は選択的に無効にすることも、デザイン環境で無効にすることもできます。  
  
#### スナップ線を選択的に無効にするには  
  
-   Alt キーを押しながらコントロールをフォーム上で移動します。  
  
     スナップ線が表示されず、コントロールが整列位置にスナップしないことを確認します。  
  
#### スナップ線をデザイン環境で無効にするには  
  
1.  **\[ツール\]** メニューから **\[オプション\]** ダイアログ ボックスを開きます。  \[Windows フォーム デザイナー\] ダイアログ ボックスを開きます。  詳細については、「[General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8dd170af-72f0-4212-b04b-034ceee92834)」を参照してください。  
  
2.  **\[全般\]** ノードを選択します。  **\[Layout Mode\]** セクションの選択項目を **\[SnapLines\]** から **\[SnapToGrid\]** に変更します。  
  
3.  \[OK\] をクリックして設定を適用します。  
  
4.  フォームでコントロールを選択し、他のコントロールの周囲で移動します。  スナップ線が表示されないことを確認します。  
  
## 次の手順  
 スナップ線を使用すると、フォーム上でコントロールを直観的に整列させることができます。  次に行う作業の例を示します。  
  
-   <xref:System.Windows.Forms.GroupBox> コントロールに別の <xref:System.Windows.Forms.GroupBox> コントロールを入れ子にしてみます。  <xref:System.Windows.Forms.Button> コントロールを子 <xref:System.Windows.Forms.GroupBox> コントロールの中に配置し、別の Button コントロールを親 <xref:System.Windows.Forms.GroupBox> コントロールの中に配置します。  <xref:System.Windows.Forms.Button> コントロールをあちこちに移動して、スナップ線がコンテナーの境界線とどのように交差するかを確認します。  
  
-   <xref:System.Windows.Forms.TextBox> コントロールの列と、これに対応する <xref:System.Windows.Forms.Label> コントロールの列を作成します。  <xref:System.Windows.Forms.Label> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true` に設定します。  <xref:System.Windows.Forms.Label> コントロールの表示テキストと <xref:System.Windows.Forms.TextBox> コントロールのテキストが整列するように、スナップ線を使用して Label コントロールを移動します。  
  
 Windows ユーザー インターフェイスのデザインについては、書籍『*Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers*』\(Redmond, WA: Microsoft Press, 1999.   \(USBN: 0\-7356\-0566\-1\)\) を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>   
 [チュートリアル : FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)