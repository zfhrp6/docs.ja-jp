---
title: ToolStrip コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 3927f180e738541f2f2f8af6d03d281f6a601167
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542052"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.ToolStrip>コントロールとその関連クラスは、ツールバー、ステータス バー、およびメニューにユーザー インターフェイス要素を結合するため、共通のフレームワークを提供します。 <xref:System.Windows.Forms.ToolStrip> コントロールは、水平または垂直のスペースを共有するツールバーの機能は、インプレース アクティブ化と編集、カスタム レイアウト、およびラフティング、豊富なデザイン時のエクスペリエンスを提供します。  
  
 <xref:System.Windows.Forms.ToolStrip>置き換え、以前のバージョン コントロール機能が追加<xref:System.Windows.Forms.ToolBar>は、必要な場合は旧バージョンとの互換性と将来の使用の両方に保持されます。  
  
## <a name="features-of-the-toolstrip-controls"></a>ToolStrip コントロールの機能  
 使用して、<xref:System.Windows.Forms.ToolStrip>を制御します。  
  
-   コンテナーで共通のユーザー インターフェイスを提供します。  
  
-   一般的に使用されるサポートするツールバーがユーザー インターフェイスとレイアウト機能、高度なテキストとイメージ、ドロップダウン ボタン、およびコントロールのドッキング、ラフティング、ボタンなどオーバーフロー ボタン、および実行時の並べ替えを実行、簡単にカスタマイズされた<xref:System.Windows.Forms.ToolStrip>項目。  
  
-   オーバーフローおよび実行時の項目の並べ替えをサポートします。 オーバーフロー機能は、アイテムに移動ドロップダウン メニューに表示する十分な領域がない場合、<xref:System.Windows.Forms.ToolStrip>です。  
  
-   標準的な外観と一般的なレンダリング モデルにより、オペレーティング システムの動作をサポートします。  
  
-   その他のコントロールのイベントを処理する同じ方法ですべてのコンテナーおよびコンテナー内の項目を一貫してイベントを処理します。  
  
-   いずれかから項目をドラッグ<xref:System.Windows.Forms.ToolStrip>別内、または、<xref:System.Windows.Forms.ToolStrip>です。  
  
-   ドロップダウン コントロールとユーザー インターフェイスの型エディターで高度なレイアウトを作成、<xref:System.Windows.Forms.ToolStripDropDown>です。  
  
 使用して、<xref:System.Windows.Forms.ToolStripControlHost>クラスを他のコントロールを使用して、<xref:System.Windows.Forms.ToolStrip>でき<xref:System.Windows.Forms.ToolStrip>それらの機能です。  
  
 機能を拡張しを使用して外観と動作を変更することができます、 <xref:System.Windows.Forms.ToolStripRenderer>、 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>、および<xref:System.Windows.Forms.ToolStripManager>と共に、<xref:System.Windows.Forms.ToolStripRenderMode>と<xref:System.Windows.Forms.ToolStripManagerRenderMode>列挙体です。  
  
 <xref:System.Windows.Forms.ToolStrip>コントロールが高い構成可能な拡張可能な多くのプロパティ、メソッド、および外観と動作をカスタマイズするイベントを提供します。 いくつかの重要なメンバーを次に示します。  
  
### <a name="important-toolstrip-members"></a>ToolStrip の重要なメンバー  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|取得または設定の親コンテナーの端、<xref:System.Windows.Forms.ToolStrip>にドッキングします。|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|<xref:System.Windows.Forms.ToolStrip> クラスがドラッグ アンド ドロップおよび項目の並べ替えをプライベートで処理するかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|取得または設定を示す値、<xref:System.Windows.Forms.ToolStrip>その項目をレイアウトします。|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|取得または設定するかどうか、<xref:System.Windows.Forms.ToolStripItem>にアタッチされて、<xref:System.Windows.Forms.ToolStrip>または<xref:System.Windows.Forms.ToolStripOverflowButton>または float 型の 2 つのことができます。|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|示す値を取得するかどうか、<xref:System.Windows.Forms.ToolStripItem>ドロップダウン リストでその他の項目を表示します。 場合の一覧、<xref:System.Windows.Forms.ToolStripItem>をクリックします。|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|オーバーフローが有効な <xref:System.Windows.Forms.ToolStrip> のオーバーフロー ボタンである <xref:System.Windows.Forms.ToolStripItem> を取得します。|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|取得または設定、<xref:System.Windows.Forms.ToolStripRenderer>の (ルック アンド フィール) の動作と外観をカスタマイズするために使用する<xref:System.Windows.Forms.ToolStrip>です。|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|取得または設定に適用される描画スタイル、<xref:System.Windows.Forms.ToolStrip>です。|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|いつ発生するか、<xref:System.Windows.Forms.ToolStrip.Renderer%2A>プロパティが変更されました。|  
  
 <xref:System.Windows.Forms.ToolStrip>に多数のコンパニオン クラスを使用してコントロールの柔軟性を実現します。 最も注目すべきことの一部を次に示します。  
  
### <a name="important-toolstrip-companion-classes"></a>ToolStrip の重要なコンパニオン クラス  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|置き換えする機能を追加、<xref:System.Windows.Forms.MainMenu>クラスです。|  
|<xref:System.Windows.Forms.StatusStrip>|置き換えする機能を追加、<xref:System.Windows.Forms.StatusBar>クラスです。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|置き換えする機能を追加、<xref:System.Windows.Forms.ContextMenu>クラスです。|  
|<xref:System.Windows.Forms.ToolStripItem>|抽象基本クラスのイベントとすべての要素のレイアウトを管理すること、 <xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripControlHost>、または<xref:System.Windows.Forms.ToolStripDropDown>含めることができます。|  
|<xref:System.Windows.Forms.ToolStripContainer>|さまざまな方法でコントロールを配置するフォームの各辺にパネルにコンテナーを提供します。|  
|<xref:System.Windows.Forms.ToolStripRenderer>|描画機能を処理<xref:System.Windows.Forms.ToolStrip>オブジェクト。|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Microsoft Office スタイルの外観を提供します。|  
|<xref:System.Windows.Forms.ToolStripManager>|コントロール<xref:System.Windows.Forms.ToolStrip>レンダリングはラフティング、およびマージ<xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.ToolStripDropDownMenu>、および<xref:System.Windows.Forms.ToolStripMenuItem>オブジェクト。|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|指定の倍数に適用される描画スタイル (ユーザー設定、Windows XP、または Microsoft Office Professional)<xref:System.Windows.Forms.ToolStrip>フォームに含まれるオブジェクト。|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|いずれかに適用される描画スタイル (ユーザー設定、Windows XP、または Microsoft Office Professional) を指定<xref:System.Windows.Forms.ToolStrip>フォームに含まれるオブジェクト。|  
|<xref:System.Windows.Forms.ToolStripControlHost>|具体的にはないその他のコントロールをホスト<xref:System.Windows.Forms.ToolStrip>コントロールが対象となる<xref:System.Windows.Forms.ToolStrip>機能します。|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|指定するかどうか、<xref:System.Windows.Forms.ToolStripItem>は主にレイアウトする<xref:System.Windows.Forms.ToolStrip>、オーバーフローに<xref:System.Windows.Forms.ToolStrip>、またはどちらもします。|  
  
 詳細については、次を参照してください。 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)と[ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
