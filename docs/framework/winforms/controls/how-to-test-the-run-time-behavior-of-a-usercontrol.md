---
title: '方法 : UserControl の実行時の動作をテストする'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
ms.openlocfilehash: ac846840f7d420da63f6bfe3db3772d7bf6cc730
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539606"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>方法 : UserControl の実行時の動作をテストする
開発する際に、<xref:System.Windows.Forms.UserControl>実行時の動作をテストする必要があります。 個別の Windows ベースのアプリケーション プロジェクトを作成し、テスト フォームにコントロールを配置することができますが、この手順は便利ではありません。 高速で簡単には、 **UserControl テスト コンテナー** Visual Studio が提供されます。 このテスト コンテナーは、Windows コントロール ライブラリ プロジェクトから直接起動します。  
  
> [!IMPORTANT]
>  テスト コンテナーを読み込む、<xref:System.Windows.Forms.UserControl>コントロールは、少なくとも 1 つのパブリック コンス トラクターをいる必要があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
> [!NOTE]
>  使用して Visual C のコントロールをテストすることはできません、 **UserControl テスト コンテナー**です。  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>UserControl の実行時の動作をテストするには  
  
1.  呼ばれる Windows コントロール ライブラリ プロジェクトを作成**ファイルを開く**です。 詳細については、「 [Windows コントロール ライブラリ テンプレート](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4)です。  
  
2.  **Windows フォーム デザイナー**、ドラッグ、<xref:System.Windows.Forms.Label>から制御、**ツールボックス**コントロールのデザイン サーフェイスにします。  
  
3.  F5 キーを押してプロジェクトをビルドおよび実行する、 **UserControl テスト コンテナー**です。 テスト コンテナーが表示されます、<xref:System.Windows.Forms.UserControl>で、**プレビュー**ウィンドウです。  
  
4.  選択、<xref:System.Windows.Forms.Control.BackColor%2A>プロパティに表示される、<xref:System.Windows.Forms.PropertyGrid>コントロールの右側に、**プレビュー**ウィンドウです。 その値を変更`ControlDark`です。 コントロールが濃い色に変わることを確認します。 他のプロパティ値を変更してみてくださいし、コントロールへの影響を確認します。  
  
5.  クリックして、**ユーザー コントロールの四辺にドッキング**下のチェック ボックス、**プレビュー**ウィンドウです。 コントロールのサイズをウィンドウを入力することを確認します。 テスト コンテナーのサイズを変更し、ペイン コントロールのサイズことを確認します。  
  
6.  テスト コンテナーを閉じます。  
  
7.  別のユーザー コントロールを追加して、**ファイルを開く**プロジェクト。 詳細については、「 [NIB: 方法: 既存項目プロジェクトに追加](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)です。  
  
8.  **Windows フォーム デザイナー**、ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**コントロールのデザイン サーフェイスにします。  
  
9. F5 キーを押してプロジェクトをビルドし、テスト コンテナーを実行します。  
  
10. をクリックして、**ユーザー コントロールの選択**<xref:System.Windows.Forms.ComboBox> 2 つのユーザー コントロールのスケールが切り替わります。  
  
## <a name="testing-user-controls-from-another-project"></a>別のプロジェクトからユーザー コントロールのテスト  
 現在のプロジェクトのテスト コンテナーでは、他のプロジェクトからユーザー コントロールをテストできます。  
  
#### <a name="to-test-user-controls-from-another-project"></a>別のプロジェクトからユーザー コントロールをテストするには  
  
1.  呼ばれる Windows コントロール ライブラリ プロジェクトを作成**TestContainerExample2**です。 詳細については、「 [Windows コントロール ライブラリ テンプレート](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4)です。  
  
2.  **Windows フォーム デザイナー**、ドラッグ、<xref:System.Windows.Forms.RadioButton>から制御、**ツールボックス**コントロールのデザイン サーフェイスにします。  
  
3.  F5 キーを押してプロジェクトをビルドし、テスト コンテナーを実行します。 テスト コンテナーが表示されます、<xref:System.Windows.Forms.UserControl>で、**プレビュー**ウィンドウです。  
  
4.  クリックして、**ロード**ボタンをクリックします。  
  
5.  **開く** ダイアログ ボックスに移動**ファイルを開く**.dll で、前の手順で作成します。 選択**ファイルを開く**.dll およびクリック、**開く** ボタンをユーザー コントロールを読み込めません  
  
6.  使用して、**ユーザー コントロールの選択**<xref:System.Windows.Forms.ComboBox>から 2 つのユーザー コントロールの間で切り替えるには、**ファイルを開く**プロジェクト。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.UserControl>  
 [方法: 複合コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [チュートリアル : Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [チュートリアル: Visual C# による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [ユーザー コントロール デザイナー](http://msdn.microsoft.com/library/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
