---
title: "DataGridView コントロールのシナリオ (Windows フォーム) | Microsoft Docs"
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
  - "データ グリッド, データ グリッドの概要"
  - "DataGridView コントロール [Windows フォーム], シナリオ"
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# DataGridView コントロールのシナリオ (Windows フォーム)
<xref:System.Windows.Forms.DataGridView> コントロールでは、さまざまなデータ ソースから取得した表形式のデータを表示できます。  単純な使い方では、<xref:System.Windows.Forms.DataGridView> コントロールに手動でデータを埋め込み、このコントロールを通じてデータを直接操作します。  しかし一般的な方法では、外部データ ソースにデータを格納しておき、<xref:System.Windows.Forms.BindingSource> コンポーネントを通じてこのコントロールをデータにバインドします。  
  
 ここでは、<xref:System.Windows.Forms.DataGridView> コントロールを使用する一般的なシナリオをいくつか紹介します。  
  
## シナリオ 1: 少量のデータを表示する  
 <xref:System.Windows.Forms.DataGridView> コントロールにデータを表示するときに、そのデータを必ず外部データ ソースに格納しなければならないわけではありません。  少量のデータを扱う場合には、そのデータをコントロールに手動で埋め込み、コントロールを通じてデータを操作できます。  これは*非バインド モード*と呼ばれます。  詳細については、「[方法 : 連結されていない Windows フォーム DataGridView コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)」を参照してください。  
  
### シナリオの要点  
  
-   非バインド モードでは、コントロールに手動でデータを埋め込みます。  
  
-   非バインド モードは、少量の読み取り専用データを扱うときに適しています。  
  
-   非バインド モードは、スプレッドシートのようなテーブルや、部分的にデータが含まれているテーブルにも適しています。  
  
## シナリオ 2: 外部データ ソースに格納されているデータを表示および更新する  
 <xref:System.Windows.Forms.DataGridView> コントロールを、ユーザーがデータベース テーブルやビジネス オブジェクトのコレクションなどのデータ ソース内のデータにアクセスするときに使うユーザー インターフェイス \(UI\) として使用することができます。  詳細については、「[方法 : データを Windows フォーム DataGridView コントロールにバインドする](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)」を参照してください。  
  
### シナリオの要点  
  
-   バインド モードでは、データ ソースに接続し、データ ソースのプロパティやデータベース列に基づいて自動的に列を生成し、コントロールに自動的にデータを読み込むことができます。  
  
-   バインド モードは、ユーザーがデータ操作を頻繁に行う場合に適しています。  データを表示用にフォーマットしたり、ユーザーが指定したデータをデータ ソース側で定義されている形式へと自動フォーマットしたりできます。  データ入力フォーマット エラーやデータベース制約エラーを検出し、ユーザーに警告を出したり、問題のあるセルを訂正したりすることもできます。  
  
-   ユーザーは列の並べ替え、固定、順序変更などの追加機能を使用して、ワークフローに最も適した方法でデータを表示できます。  
  
-   クリップボード サポートにより、ユーザーはアプリケーションから別のアプリケーションにデータをコピーできます。  
  
## シナリオ 3: 高度なデータ  
 標準のデータ バインディング モデルでは対応できない特別な要件がある場合は、*仮想モード*を実装することで、コントロールとデータとのやり取りを管理できます。  仮想モードを実装するとは、コントロールがセルに関する情報を必要なときに要求できるようにするイベント ハンドラーを実装することです。  
  
 たとえば、大量のデータを扱う場合には、仮想モードを実装することで最適な効率を確保できます。  仮想モードは、別のデータ ソースから取得した列と一緒に表示されているバインドされていない列の値を保守する場合にも役立ちます。  
  
 仮想モードの詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)」を参照してください。  
  
### シナリオの要点  
  
-   仮想モードは、高いパフォーマンスを保ちつつ大量のデータを表示しなければならないときに適しています。  
  
## シナリオ 4: 行と列のサイズを自動調整する  
 定期的に更新されるデータを表示するときは、すべての内容が表示されるように自動的に行と列のサイズを変更できます。  <xref:System.Windows.Forms.DataGridView> コントロールには、手動でのサイズ変更を有効\/無効にしたり、特定のタイミングでサイズをプログラムから変更したり、内容が変化したときに自動的にサイズを調整したりするオプションが用意されています。  詳細については、「[Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
### シナリオの要点  
  
-   手動でのサイズ変更を有効にすると、ユーザーがセルの高さと幅を調整できます。  
  
-   自動サイズ変更を有効にすると、セルの内容がクリップされないようにセルのサイズを調整できます。  
  
-   プログラム的なサイズ変更を行うと、特定のタイミングでセルのサイズを変更することができ、連続的な自動サイズ変更によるパフォーマンス低下を回避できます。  
  
## シナリオ 5: 単純なカスタマイズ  
 <xref:System.Windows.Forms.DataGridView> コントロールの基本的な外観と動作はさまざまな方法で変更できます。  詳細については、「[Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
### シナリオの要点  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを使用すると、コントロールの個々の要素に関する色、フォント、形式、位置の情報をさまざまなレベルで設定できます。  
  
-   セルのスタイルは複数の要素で重ねたり共有したりできるので、コードを再使用できます。  
  
## シナリオ 6: 高度なカスタマイズ  
 <xref:System.Windows.Forms.DataGridView> コントロールの外観と動作はさまざまな方法でカスタマイズできます。  
  
### シナリオの要点  
  
-   独自のセル描画コードを記述できます。  詳細については、「[方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)」を参照してください。  
  
-   独自の行描画コードを記述できます。  この手法は、複数の列にまたがる内容を含んだ行を作成するときに役立ちます。  詳細については、「[方法 : Windows フォームの DataGridView コントロールの行の外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)」を参照してください。  
  
-   独自のセル クラスや列クラスを実装して、セルの外観をカスタマイズすることができます。  詳細については、「[方法 : Windows フォーム DataGridView コントロールのセルと列を、それぞれの動作と外観を拡張してカスタマイズする](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)」を参照してください。  
  
-   組み込みの列型ではサポートされないコントロールをホストする独自のセル クラスや列クラスを実装できます。  詳細については、「[方法 : Windows フォーム DataGridView Cells でコントロールをホストする](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [DataGridView コントロールの概要](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)