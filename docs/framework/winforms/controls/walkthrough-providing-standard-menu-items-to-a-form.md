---
title: 'チュートリアル : 標準メニュー項目をフォームに用意する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00988266804207e85bc715342f888fd29348066e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>チュートリアル : 標準メニュー項目をフォームに用意する
フォームの標準のメニューを <xref:System.Windows.Forms.MenuStrip> コントロールに提供できます。  
  
 このチュートリアルを使用する方法を示します、<xref:System.Windows.Forms.MenuStrip>標準メニューを作成するコントロール。 フォームは、ユーザーがメニュー項目を選択したときにも応答します。 次のタスクは、このチュートリアルで例を示します。  
  
-   Windows フォーム プロジェクトを作成します。  
  
-   標準メニューを作成します。  
  
-   作成する、<xref:System.Windows.Forms.StatusStrip>コントロール。  
  
-   メニュー項目の選択を処理しています。  
  
 標準メニューにメニュー項目の選択を表示するフォームが完了したら、<xref:System.Windows.Forms.StatusStrip>コントロール。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: フォームに標準のメニュー項目の提供](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  いう Windows アプリケーション プロジェクトを作成する**StandardMenuForm**です。  
  
     詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  Windows フォーム デザイナーでフォームを選択します。  
  
## <a name="creating-a-standard-menu"></a>標準メニューを作成します。  
 Windows フォーム デザイナーが自動的に設定できる、<xref:System.Windows.Forms.MenuStrip>標準メニュー項目を含むコントロールです。  
  
#### <a name="to-create-a-standard-menu"></a>標準メニューを作成するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>コントロールをフォームにします。  
  
2.  クリックして、<xref:System.Windows.Forms.MenuStrip>コントロールのスマート タグ グリフ (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) を選択して**標準項目の挿入**です。  
  
     <xref:System.Windows.Forms.MenuStrip>標準メニュー項目コントロールが表示されます。  
  
3.  クリックして、**ファイル**メニュー項目をその既定のメニュー項目と対応するアイコンを参照してください。  
  
## <a name="creating-a-statusstrip-control"></a>StatusStrip コントロールの作成  
 使用して、<xref:System.Windows.Forms.StatusStrip>して Windows フォーム アプリケーションの状態を表示するコントロール。 現在の例では、ユーザーによって選択されたメニュー項目が表示されます、<xref:System.Windows.Forms.StatusStrip>コントロール。  
  
#### <a name="to-create-a-statusstrip-control"></a>StatusStrip コントロールを作成するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.StatusStrip>コントロールをフォームにします。  
  
     <xref:System.Windows.Forms.StatusStrip>コントロールが自動的に、フォームの下部にドッキングします。  
  
2.  クリックして、<xref:System.Windows.Forms.StatusStrip>コントロールのドロップダウン ボタンをクリックし、選択**StatusLabel**を追加する、<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールを<xref:System.Windows.Forms.StatusStrip>コントロール。  
  
## <a name="handling-item-selection"></a>処理の項目の選択  
 処理、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント、ユーザーがメニュー項目を選択するときに応答します。  
  
#### <a name="to-handle-item-selection"></a>項目の選択を処理するには  
  
1.  クリックして、**ファイル**作成で作成したメニュー項目に標準メニュー セクションです。  
  
2.  **プロパティ**ウィンドウで、をクリックして**イベント**です。  
  
3.  ダブルクリックして、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント。  
  
     Windows フォーム デザイナーでのイベント ハンドラーが生成されます、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント。  
  
4.  イベント ハンドラーに次のコードを挿入します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  挿入、`UpdateStatus`ユーティリティ メソッドの定義、フォームにします。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>チェックポイント  
  
#### <a name="to-test-your-form"></a>フォームをテストするには  
  
1.  F5 キーを押してをコンパイルして、フォームを実行します。  
  
2.  クリックして、**ファイル**メニュー項目、メニューを開きます。  
  
3.  **ファイル**] メニューの [選択項目のいずれかをクリックします。  
  
     <xref:System.Windows.Forms.StatusStrip>コントロールには、選択した項目が表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、標準メニューを備えたフォームを作成しました。 使用することができます、<xref:System.Windows.Forms.ToolStrip>ファミリの他のさまざまな目的のコントロール。  
  
-   コントロールのショートカット メニューを作成する<xref:System.Windows.Forms.ContextMenuStrip>です。 詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)です。  
  
-   ドッキングとマルチ ドキュメント インターフェイス (MDI) フォームを作成する<xref:System.Windows.Forms.ToolStrip>コントロール。 詳細については、次を参照してください。[チュートリアル: メニューのマージと ToolStrip コントロールを MDI フォームを作成する](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)です。  
  
-   与える、<xref:System.Windows.Forms.ToolStrip>プロフェッショナルな外観を制御します。 詳細については、次を参照してください。[する方法: アプリケーションの ToolStrip レンダラーを設定](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
