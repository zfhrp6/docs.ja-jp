---
title: "チュートリアル : メニューのマージと ToolStrip コントロールのある MDI フォームを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e0538151c19eb47f8a51330b7f2c06818d1e73f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>チュートリアル : メニューのマージと ToolStrip コントロールのある MDI フォームを作成する
<xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間は、マルチ ドキュメント インターフェイス (MDI) アプリケーションをサポートし、<xref:System.Windows.Forms.MenuStrip> コントロールはメニューの結合をサポートします。 MDI フォームは、<xref:System.Windows.Forms.ToolStrip> コントロールもサポートします。  
  
 このチュートリアルを使用する方法を示します<xref:System.Windows.Forms.ToolStripPanel>を MDI フォームでコントロール。 フォームは、子メニューをマージするメニューもサポートしています。 次のタスクは、このチュートリアルで例を示します。  
  
-   Windows フォーム プロジェクトを作成します。  
  
-   フォームのメイン メニューを作成します。 メニューの実際の名前が異なります。  
  
-   追加する、<xref:System.Windows.Forms.ToolStripPanel>コントロールを**ツールボックス**です。  
  
-   子フォームを作成します。  
  
-   配置<xref:System.Windows.Forms.ToolStripPanel>z オーダーでコントロール。  
  
 メニューのマージおよび移動をサポートする MDI フォームが完了したら、<xref:System.Windows.Forms.ToolStrip>コントロール。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: メニューのマージと ToolStrip コントロールを MDI フォームを作成](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   作成し、コンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセス許可を[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]がインストールされています。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  いう Windows アプリケーション プロジェクトを作成する**mdi フォーム**です。  
  
     詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  Windows フォーム デザイナーでフォームを選択します。  
  
3.  [プロパティ] ウィンドウ内の値を設定、<xref:System.Windows.Forms.Form.IsMdiContainer%2A>に`true`です。  
  
## <a name="creating-the-main-menu"></a>メイン メニューの作成  
 親 MDI フォームには、メイン メニューが含まれています。 メイン メニューがという名前の項目 1 つのメニュー**ウィンドウ**します。 **ウィンドウ**メニュー項目の子フォームを作成することができます。 子フォームのメニュー項目は、メイン メニューにマージされます。  
  
#### <a name="to-create-the-main-menu"></a>メイン メニューを作成するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>コントロールをフォームにします。  
  
2.  追加、<xref:System.Windows.Forms.ToolStripMenuItem>を<xref:System.Windows.Forms.MenuStrip>を制御し、名前を付けます**ウィンドウ**します。  
  
3.  <xref:System.Windows.Forms.MenuStrip> コントロールを選択します。  
  
4.  [プロパティ] ウィンドウ内の値を設定、<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティを`ToolStripMenuItem1`です。  
  
5.  サブ項目を追加、**ウィンドウ**メニュー項目と、名前、サブアイテム**新規**です。  
  
6.  [プロパティ] ウィンドウでをクリックして**イベント**です。  
  
7.  ダブルクリックして、<xref:System.Windows.Forms.ToolStripItem.Click>イベント。  
  
     Windows フォーム デザイナーでのイベント ハンドラーが生成されます、<xref:System.Windows.Forms.ToolStripItem.Click>イベント。  
  
8.  イベント ハンドラーに次のコードを挿入します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel コントロールをツールボックスに追加します。  
 使用すると<xref:System.Windows.Forms.MenuStrip>する必要があります、MDI フォームでコントロール、<xref:System.Windows.Forms.ToolStripPanel>コントロール。 追加する必要があります、<xref:System.Windows.Forms.ToolStripPanel>コントロールを**ツールボックス**Windows フォーム デザイナーで、MDI フォームを作成します。  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel コントロールをツールボックスに追加するには  
  
1.  開く、**ツールボックス**、をクリックし、**すべての Windows フォーム**利用可能な Windows フォーム コントロールを表示するタブです。  
  
2.  開くには、ショートカット メニューを右クリックし **アイテムの選択**です。  
  
3.  **ツールボックス アイテムの選択**ダイアログ ボックスで、下へスクロールして、**名前**列が見つかるまで**ToolStripPanel**です。  
  
4.  チェック ボックスをオンに**ToolStripPanel**、順にクリック**OK**です。  
  
     <xref:System.Windows.Forms.ToolStripPanel>コントロールに表示され、**ツールボックス**です。  
  
## <a name="creating-a-child-form"></a>子フォームを作成します。  
 この手順をそれ自体を持つ 1 つの子フォーム クラスを定義します<xref:System.Windows.Forms.MenuStrip>コントロール。 このフォームのメニュー項目は、親フォームのマージされます。  
  
#### <a name="to-define-a-child-form"></a>子フォームを定義するには  
  
1.  という名前の新しいフォームを追加`ChildForm`をプロジェクトにします。  
  
     詳細については、次を参照してください。[する方法: Windows フォームをプロジェクトに追加](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1)です。  
  
2.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>子フォームにコントロールできます。  
  
3.  クリックして、<xref:System.Windows.Forms.MenuStrip>コントロールのスマート タグ グリフ (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))、し、**アイテムの編集**です。  
  
4.  **Items コレクション エディター**  ダイアログ ボックスで、追加、新しい<xref:System.Windows.Forms.ToolStripMenuItem>という**ChildMenuItem**子メニューをします。  
  
     詳細については、次を参照してください。 [ToolStrip Items コレクション エディター](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25)です。  
  
## <a name="testing-the-form"></a>フォームのテスト  
  
#### <a name="to-test-your-form"></a>フォームをテストするには  
  
1.  F5 キーを押してをコンパイルして、フォームを実行します。  
  
2.  クリックして、**ウィンドウ**、メニューを開き、をクリックしてメニュー項目**新規**です。  
  
     新しい子フォームは、フォームの MDI クライアント領域に作成されます。 子フォームのメニューは、メイン メニューに結合されます。  
  
3.  子フォームを閉じます。  
  
     子フォームのメニューは、メイン メニューから削除されます。  
  
4.  をクリックして**新規**何回か。  
  
     子フォームは自動的に、「、W**ウィンドウ**メニュー項目のため、<xref:System.Windows.Forms.MenuStrip>コントロールの<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティが割り当てられます。  
  
## <a name="adding-toolstrip-support"></a>ToolStrip のサポートを追加します。  
 この手順では追加 4 <xref:System.Windows.Forms.ToolStrip> MDI 親フォームのコントロールです。 各<xref:System.Windows.Forms.ToolStrip>内にコントロールを追加、<xref:System.Windows.Forms.ToolStripPanel>フォームの端にドッキングされているコントロール。  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>ToolStrip コントロールを MDI 親フォームに追加するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ToolStripPanel>コントロールをフォームにします。  
  
2.  <xref:System.Windows.Forms.ToolStripPanel>コントロールを選択し、ダブルクリック、<xref:System.Windows.Forms.ToolStrip>内の制御、**ツールボックス**です。  
  
     A<xref:System.Windows.Forms.ToolStrip>でコントロールが作成された、<xref:System.Windows.Forms.ToolStripPanel>コントロール。  
  
3.  <xref:System.Windows.Forms.ToolStripPanel> コントロールを選択します。  
  
4.  [プロパティ] ウィンドウでのコントロールの値を変更<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Left>です。  
  
     <xref:System.Windows.Forms.ToolStripPanel>メイン メニューの下に、フォームの左側にドッキングを制御します。 MDI クライアント領域のサイズに合わせて、<xref:System.Windows.Forms.ToolStripPanel>コントロール。  
  
5.  手順 1. ~ 4. を繰り返します。  
  
     新しいドッキング<xref:System.Windows.Forms.ToolStripPanel>フォームの上部を制御します。  
  
     <xref:System.Windows.Forms.ToolStripPanel>コントロールが、メイン メニューの下には、最初の右側にドッキングされている<xref:System.Windows.Forms.ToolStripPanel>コントロール。 この手順は、正しく配置の z オーダーの重要度を示しています。<xref:System.Windows.Forms.ToolStripPanel>コントロール。  
  
6.  2 つの手順 1. ~ 4. を繰り返します<xref:System.Windows.Forms.ToolStripPanel>コントロール。  
  
     新しいドッキング<xref:System.Windows.Forms.ToolStripPanel>の権限と、フォームの一番下へのコントロールです。  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Z オーダーで ToolStripPanel コントロールの配置  
 位置、ドッキングされた<xref:System.Windows.Forms.ToolStripPanel>MDI フォーム上のコントロールを z オーダーでコントロールの位置によって決定されます。 ドキュメント アウトライン ウィンドウでコントロールの z オーダーを簡単に配置できます。  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Z オーダーで ToolStripPanel コントロールを配置するには  
  
1.  **ビュー** ] メニューのをクリックして**その他のウィンドウ**、クリックして**[ドキュメント アウトライン**です。  
  
     配置、<xref:System.Windows.Forms.ToolStripPanel>前の手順からコントロールは非標準です。 これは、z オーダーが正しくないためです。 ドキュメント アウトライン ウィンドウを使用すると、コントロールの z オーダーを変更できます。  
  
2.  ドキュメント アウトライン ウィンドウで、次のように選択します。 **ToolStripPanel4**です。  
  
3.  下向きの矢印ボタンをクリックするまで繰り返し、 **ToolStripPanel4**は一覧の下部にします。  
  
     **ToolStripPanel4**コントロールが他のコントロールの下に、フォームの下部にドッキングされています。  
  
4.  選択**ToolStripPanel2**です。  
  
5.  一覧で 3 番目にコントロールの位置を 1 回下向きの矢印ボタンをクリックします。  
  
     **ToolStripPanel2**コントロールは、メイン メニューの下にあると、その他のコントロールの上、フォームの上部にドッキングされています。  
  
6.  さまざまなコントロール、 **ドキュメント アウトライン**ウィンドウし、z オーダーで別の位置に移動します。 Z オーダーのドッキングされたコントロールの配置への影響に注意してください。 CTRL + Z を使用してまたは**を元に戻す**上、**編集**変更を元に戻す] メニューの [します。  
  
## <a name="checkpoint"></a>チェックポイント  
  
#### <a name="to-test-your-form"></a>フォームをテストするには  
  
1.  F5 キーを押してをコンパイルして、フォームを実行します。  
  
2.  ハンドルをクリックして、<xref:System.Windows.Forms.ToolStrip>を制御し、フォーム上の別の位置にコントロールをドラッグします。  
  
     ドラッグすることができます、<xref:System.Windows.Forms.ToolStrip>から 1 つのコントロール<xref:System.Windows.Forms.ToolStripPanel>を別のコントロールです。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルで MDI 親フォームを作成した<xref:System.Windows.Forms.ToolStrip>コントロールやメニューのマージします。 使用することができます、<xref:System.Windows.Forms.ToolStrip>ファミリの他のさまざまな目的のコントロール。  
  
-   コントロールのショートカット メニューを作成する<xref:System.Windows.Forms.ContextMenuStrip>です。 詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)です。  
  
-   自動的に設定された標準のメニューで、フォームを作成します。 詳細については、次を参照してください。[チュートリアル: 標準メニュー項目をフォームに](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)です。  
  
-   与える、<xref:System.Windows.Forms.ToolStrip>プロフェッショナルな外観を制御します。 詳細については、次を参照してください。[する方法: アプリケーションの ToolStrip レンダラーを設定](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [方法: MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [方法: MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [方法: MDI ドロップダウン メニューに MenuStrip を挿入する](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
