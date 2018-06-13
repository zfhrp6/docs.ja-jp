---
title: MenuStrip コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: b09d653210c72a38bbc4dc0858ae2553ad9cbeef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537487"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip コントロールの概要 (Windows フォーム)
メニューは、共通のテーマでグループ化されているコマンドを保持して、ユーザーに機能を公開します。  
  
 <xref:System.Windows.Forms.MenuStrip>コントロールはこのバージョンの Visual Studio と .NET Framework に新しいです。 コントロールで、Microsoft Office で見つかったものと同様のメニューを簡単に作成できます。  
  
 <xref:System.Windows.Forms.MenuStrip>マルチ ドキュメント インターフェイス (MDI) とメニューのマージ、ツール ヒント、およびオーバーフロー コントロールをサポートしています。 アクセス キー、ショートカット キー、チェック マーク、イメージ、およびのセパレーター バーを追加することで、メニューの読みやすさと使いやすさを強化できます。  
  
 <xref:System.Windows.Forms.MenuStrip>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>コントロール。 ただし、、<xref:System.Windows.Forms.MainMenu>を選択した場合、旧バージョンとの互換性および将来使用するコントロールは保持されます。  
  
## <a name="ways-to-use-the-menustrip-control"></a>MenuStrip コントロールの使用方法  
 使用して、<xref:System.Windows.Forms.MenuStrip>を制御します。  
  
-   拡張ユーザー テキストとイメージの並べ替えとアラインメント、ドラッグ アンド ドロップ操作、MDI、オーバーフロー、メニュー コマンドにアクセスするの代替モードなどのインターフェイスとレイアウトの機能をサポートするメニューは一般的に使用される、簡単にカスタマイズされた作成します。  
  
-   標準的な外観とオペレーティング システムの動作をサポートします。  
  
-   その他のコントロールのイベントを処理する同じ方法ですべてのコンテナーおよびコンテナー内の項目を一貫してイベントを処理します。  
  
 次の表に、いくつかの特に重要なプロパティ<xref:System.Windows.Forms.MenuStrip>クラスに関連付けられているとします。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|取得または設定、 <xref:System.Windows.Forms.ToolStripMenuItem> MDI 子フォームの一覧の表示に使用されます。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|取得または MDI アプリケーションのメニューを親と子メニューをマージする方法を設定します。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|取得または MDI アプリケーションでメニュー内でマージされた項目の位置を設定します。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|取得またはフォームが MDI 子フォームのコンテナーかどうかを示す値を設定します。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|取得または設定のツール ヒントを表示するかどうかを示す値、<xref:System.Windows.Forms.MenuStrip>です。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<xref:System.Windows.Forms.MenuStrip> がオーバーフロー機能をサポートするかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|取得または設定に関連付けられているショートカット キー、<xref:System.Windows.Forms.ToolStripMenuItem>です。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|関連付けられたショートカット キーのキーかどうかを示す値を取得または設定、<xref:System.Windows.Forms.ToolStripMenuItem>横に表示されますが、<xref:System.Windows.Forms.ToolStripMenuItem>です。|  
  
 次の表は、重要な<xref:System.Windows.Forms.MenuStrip>コンパニオン クラスです。  
  
|クラス|説明|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|表示される選択可能なオプションを表す、<xref:System.Windows.Forms.MenuStrip>または<xref:System.Windows.Forms.ContextMenuStrip>です。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|ショートカット メニューを表します。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|ユーザーが、ユーザーがクリックしたときに表示される一覧から 1 つの項目を選択できるコントロールを表す、<xref:System.Windows.Forms.ToolStripDropDownButton>または高レベルのメニュー項目。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|派生したコントロールの基本的な機能を提供<xref:System.Windows.Forms.ToolStripItem>クリックされたときにドロップダウン項目を表示します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
