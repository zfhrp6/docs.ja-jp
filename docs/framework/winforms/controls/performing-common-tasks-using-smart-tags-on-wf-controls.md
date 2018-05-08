---
title: 'チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行
Windows フォーム アプリケーションのフォームとコントロールを作成するときに、繰り返し実行する多くのタスクを使用します。 これらは、発生する、よく実行されるタスクの一部を示します。  
  
-   追加または取り外し、タブ、<xref:System.Windows.Forms.TabControl>です。  
  
-   コントロールの親へのドッキングします。  
  
-   向きの変更、<xref:System.Windows.Forms.SplitContainer>コントロール。  
  
 開発を高速には、多くのコントロールは、デザイン時に 1 つのジェスチャで上記のような一般的なタスクを実行することは状況依存のメニューは、スマート タグを提供します。 これらのタスクが呼び出されます*スマート タグ動詞*です。  
  
 スマート タグは、その有効期間、デザイナーでのコントロールのインスタンスに接続されたままし、常に利用します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   スマート タグを使用します。  
  
-   有効にして、スマート タグを無効化  
  
 終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  "SmartTagsExample"と呼ばれる Windows ベースのアプリケーション プロジェクトを作成します。 詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  フォームを選択、 **Windows フォーム デザイナー**です。  
  
## <a name="using-smart-tags"></a>スマート タグを使用します。  
 スマート タグは提供するコントロールのデザイン時に常に使用します。  
  
#### <a name="to-use-smart-tags"></a>スマート タグを使用するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TabControl>から、**ツールボックス**フォーム上にします。 スマート タグ グリフを注意してください (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) のサイドに表示される、<xref:System.Windows.Forms.TabControl>です。  
  
2.  スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**タブの追加**項目。 新しいタブ ページが追加されたことを確認、<xref:System.Windows.Forms.TabControl>です。  
  
3.  ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。  
  
4.  スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**列の追加**項目。 新しい列が追加されたことを確認、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
5.  ドラッグ、<xref:System.Windows.Forms.SplitContainer>から制御、**ツールボックス**フォーム上にします。  
  
6.  スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**水平分割線の向き**項目。 されることを確認、<xref:System.Windows.Forms.SplitContainer>コントロールの分割バーは水平方向です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [チュートリアル: Windows フォームのコンポーネントへのスマート タグの追加](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
