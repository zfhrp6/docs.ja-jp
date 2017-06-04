---
title: "DataGridView コントロール (Windows フォーム) | Microsoft Docs"
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
  - "データ [Windows フォーム], 表示 (表形式で)"
  - "データ グリッド"
  - "データの表示形式"
  - "DataGridView コントロール [Windows フォーム]"
  - "データセット [Windows フォーム], 表示 (DataGridView コントロール内に)"
  - "データセット [Windows フォーム], ユーザー インターフェイス"
  - "グリッド コントロール [Windows フォーム]"
  - "テーブル [Windows フォーム]"
  - "表データ, 表示 (Windows フォームに)"
  - "Windows フォーム, 表示 (データを)"
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# DataGridView コントロール (Windows フォーム)
`DataGridView` コントロールには、データを表形式で表示するための強力で柔軟な機能が用意されています。  `DataGridView` コントロールを使用すると、読み取り専用のビューに少量のデータを表示したり、拡大して非常に大量のデータのセットの編集可能なビューを表示したりできます。  
  
 `DataGridView` コントロールはいくつかの方法で拡張でき、アプリケーションにカスタムの動作を組み込むことができます。  たとえば、プログラムで独自の並べ替えアルゴリズムを指定したり、独自の種類のセルを作成したりできます。  `DataGridView` コントロールの外観は、いくつかのプロパティを選択することで簡単にカスタマイズできます。  `DataGridView` コントロールでは、多くの種類のデータ ストアをデータ ソースとして使用できますが、データ ソースをバインドせずに動作させることもできます。  
  
 このセクションのトピックでは、`DataGridView` の機能をアプリケーションに組み込むときに使用できる概念および手法について説明します。  
  
## このセクションの内容  
 [DataGridView コントロールの概要](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 Windows フォームの `DataGridView` コントロールのアーキテクチャおよび中心となる概念を説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールの既定の機能](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 Windows フォームの `DataGridView` コントロールがデータ ソースにバインドされているときの既定の外観および動作について説明します。  
  
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Windows フォームの `DataGridView` コントロールのデータの表示に使用する列型、およびユーザーがデータを変更または追加できるようにするために使用する列型について説明します。  
  
 [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 セル、行、および列の一般的なプロパティを説明するトピックを示します。  
  
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 コントロールの基本の外観およびセル データの書式設定を変更する方法を説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 コントロールに手動でデータを組み込む方法と、外部データ ソースからデータを取得する方法について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロール内の列と行のサイズ変更](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 セルの内容に合わせて、またはコントロールが利用可能な幅に合わせて、行と列のサイズを自動的に調整する方法を説明するトピックを示します。  
  
 [Windows フォームの DataGridView コントロールでのデータの並べ替え](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 このコントロールの並べ替え機能について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 コントロールのデータに対してユーザーが実行できる追加および修正の仕方を変更する方法を説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 コントロールのセル、行、および列の選択機能について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 セル、行、および列オブジェクトを使用したプログラミング方法を説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 `DataGridView` のセルおよび行のカスタム描画と、セル、列、および行の派生型の作成について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 大量のデータを扱うときのパフォーマンスの問題を避けるために、このコントロールを効率的に使用する方法について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 キーボードとマウスを介してユーザーが `DataGridView` コントロールとやり取りする方法を説明します。  
  
 [Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 `DataGridView` コントロールが <xref:System.Windows.Forms.DataGrid> コントロールより改良され、これに代わるものである点について説明します。  
  
 「[Windows フォーム DataGridView コントロールでのデザイナーの使用](http://msdn.microsoft.com/library/ms171593\(v=vs.110\))」も参照してください。  
  
## 関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingSource> コンポーネントのリファレンス ドキュメントを提供します。  <xref:System.Windows.Forms.DataGridView> コントロールと <xref:System.Windows.Forms.BindingSource> コンポーネントは、密接に連携して機能するようにデザインされています。  
  
## 参照  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)