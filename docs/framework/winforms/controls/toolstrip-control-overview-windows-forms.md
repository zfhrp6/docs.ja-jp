---
title: "ToolStrip コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Toolstrip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ツール バー [Windows フォーム]"
  - "ツール バー [Windows フォーム], 新機能 (Windows フォームの)"
  - "ToolStrip コントロール [Windows フォーム], ToolStrip コントロールの概要"
  - "新機能 [Windows フォーム], ツール バー"
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# ToolStrip コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.ToolStrip> コントロールと関連クラスには、ユーザー インターフェイス要素をツール バー、ステータス バー、およびメニューに組み込むための共通のフレームワークがあります。  <xref:System.Windows.Forms.ToolStrip> コントロールは、埋め込み先編集の有効化、カスタム レイアウト、およびラフティング \(水平スペースまたは垂直スペースを共有するツール バーの機能\) を含む豊富なデザイン時機能を提供します。  
  
 <xref:System.Windows.Forms.ToolStrip> コントロールは、以前のバージョンのコントロールに置き換わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保持するため、および将来必要になったときに使用できるように保持されています。  
  
## ToolStrip コントロールの機能  
 <xref:System.Windows.Forms.ToolStrip> コントロールを使用すると、次のことができます。  
  
-   コンテナー間に共通のユーザー インターフェイスを提供する。  
  
-   カスタマイズでき、一般に使用できるだけでなく、高度なユーザー インターフェイス機能とレイアウト機能 \(ドッキング、ラフティング、テキストおよびイメージ付きボタン、ドロップダウン ボタンとドロップダウン コントロール、オーバーフロー ボタン、実行時の <xref:System.Windows.Forms.ToolStrip> 項目の並べ替えなど\) をサポートするツール バーを簡単に作成する。  
  
-   オーバーフローおよび実行時の項目の順序変更をサポートする。  オーバーフロー機能は、スペース不足で <xref:System.Windows.Forms.ToolStrip> に項目を表示できない場合に、項目をドロップダウン メニューに移動します。  
  
-   共通の描画モデルにより、オペレーティング システムの標準的な外観と動作をサポートする。  
  
-   他のコントロールのイベント処理と同じように、コンテナーおよびコンテナーに含まれる項目のすべてを一貫して処理する。  
  
-   複数の <xref:System.Windows.Forms.ToolStrip> 間、または特定の <xref:System.Windows.Forms.ToolStrip> 内で項目をドラッグする。  
  
-   高度なレイアウトを使用したドロップダウン コントロールおよびユーザー インターフェイス型エディターを <xref:System.Windows.Forms.ToolStripDropDown> で作成する。  
  
 <xref:System.Windows.Forms.ToolStripControlHost> クラスを使用して <xref:System.Windows.Forms.ToolStrip> 上で他のコントロールを使用し、それらの <xref:System.Windows.Forms.ToolStrip> 機能を取得します。  
  
 <xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>、および <xref:System.Windows.Forms.ToolStripManager> を <xref:System.Windows.Forms.ToolStripRenderMode> 列挙型および <xref:System.Windows.Forms.ToolStripManagerRenderMode> 列挙型と共に使用すると、機能を拡張して外観と動作を変更できます。  
  
 <xref:System.Windows.Forms.ToolStrip> コントロールは構成が簡単で、拡張性に優れています。また、外観と動作をカスタマイズするためのさまざまなプロパティ、メソッド、およびイベントを提供します。  以下に、いくつかの重要なメンバーを示します。  
  
### 重要な ToolStrip メンバー  
  
|名前|Description|  
|--------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|<xref:System.Windows.Forms.ToolStrip> のドッキング先となる親コンテナーの端を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|<xref:System.Windows.Forms.ToolStrip> クラスがドラッグ アンド ドロップおよび項目の並べ替えをプライベートで処理するかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|<xref:System.Windows.Forms.ToolStrip> が項目をレイアウトする方法を示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|<xref:System.Windows.Forms.ToolStripItem> を <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.ToolStripOverflowButton> のどちらかに結び付けるか、または両者の間でフローティングできるかを取得または設定します。|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|<xref:System.Windows.Forms.ToolStripItem> をクリックしたときに、<xref:System.Windows.Forms.ToolStripItem> がドロップダウン リストに他の項目を表示するかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|オーバーフローが有効になった <xref:System.Windows.Forms.ToolStrip> のオーバーフロー ボタンである <xref:System.Windows.Forms.ToolStripItem> を取得します。|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|<xref:System.Windows.Forms.ToolStrip> の外観と動作 \(ルック アンド フィール\) のカスタマイズに使用される <xref:System.Windows.Forms.ToolStripRenderer> を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|<xref:System.Windows.Forms.ToolStrip> に適用される描画スタイルを取得または設定します。|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|<xref:System.Windows.Forms.ToolStrip.Renderer%2A> プロパティが変更されると発生します。|  
  
 <xref:System.Windows.Forms.ToolStrip> コントロールの柔軟性は、多数のコンパニオン クラスを使用することによって実現されます。  以下に、最も重要なコンパニオン クラスを示します。  
  
### 重要な ToolStrip コンパニオン クラス  
  
|名前|Description|  
|--------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Forms.MainMenu> クラスに対して機能の置き換えと追加を行います。|  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Forms.StatusBar> クラスに対して機能の置き換えと追加を行います。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Forms.ContextMenu> クラスに対して機能の置き換えと追加を行います。|  
|<xref:System.Windows.Forms.ToolStripItem>|<xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.ToolStripControlHost>、または <xref:System.Windows.Forms.ToolStripDropDown> に格納できるすべての要素のイベントとレイアウトを管理する抽象基本クラスです。|  
|<xref:System.Windows.Forms.ToolStripContainer>|コントロールをさまざまな方法で配置できるパネルをフォームの両側に持つコンテナーを提供します。|  
|<xref:System.Windows.Forms.ToolStripRenderer>|<xref:System.Windows.Forms.ToolStrip> オブジェクトの描画機能を処理します。|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Microsoft Office スタイルの外観を提供します。|  
|<xref:System.Windows.Forms.ToolStripManager>|<xref:System.Windows.Forms.ToolStrip> のレンダリングとラフティング、および <xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.ToolStripDropDownMenu>、<xref:System.Windows.Forms.ToolStripMenuItem> の各オブジェクトのマージを制御します。|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|フォームに含まれる複数の <xref:System.Windows.Forms.ToolStrip> オブジェクトに適用される描画スタイル \(カスタム、Windows XP、または Microsoft Office Professional\) を指定します。|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|フォームに含まれる特定の <xref:System.Windows.Forms.ToolStrip> オブジェクトに適用される描画スタイル \(カスタム、Windows XP、または Microsoft Office Professional\) を指定します。|  
|<xref:System.Windows.Forms.ToolStripControlHost>|厳密には <xref:System.Windows.Forms.ToolStrip> コントロールではないが、<xref:System.Windows.Forms.ToolStrip> 機能が必要な他のコントロールをホストします。|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|<xref:System.Windows.Forms.ToolStripItem> をメイン <xref:System.Windows.Forms.ToolStrip> とオーバーフロー <xref:System.Windows.Forms.ToolStrip> のどちらにレイアウトするか、またはどちらにもレイアウトしないかを指定します。|  
  
 詳細については、「[ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)」および「[ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripDropDown>