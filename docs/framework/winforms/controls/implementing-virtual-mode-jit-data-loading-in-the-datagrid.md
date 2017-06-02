---
title: "Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装 | Microsoft Docs"
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
  - "データ [Windows フォーム], 管理 (大容量のデータセットを)"
  - "DataGridView コントロール [Windows フォーム], 大容量のデータセット"
  - "DataGridView コントロール [Windows フォーム], 仮想モード"
  - "例 [Windows フォーム], Just-In-Time データ読み込み"
  - "Just-In-Time データ読み込み"
  - "仮想モード, Just-In-Time データ読み込み"
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装
<xref:System.Windows.Forms.DataGridView> コントロールで仮想モードを実装する 1 つの理由は、データを必要なときにのみ取得するためです。  これを *Just\-In\-Time データ読み込み*と言います。  
  
 たとえば、リモート データベースの大型のテーブルを操作する場合、表示に必要なデータのみを取得し、ユーザーが新しい行をスクロール表示したときにのみ追加のデータを取得して、スタートアップの遅延を避ける必要があります。  また、アプリケーションを実行するクライアント コンピューターで、データの保存に利用できるメモリの容量が制限されている場合には、データベースから新しい値を取得するときに不要なデータを破棄する必要もあります。  
  
 以下のセクションでは、Just\-In\-Time キャッシュで <xref:System.Windows.Forms.DataGridView> コントロールを使用する方法について説明します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : Windows フォーム DataGridView コントロールで Just\-In\-Time データ読み込みを使用して仮想モードを実装する](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)」を参照してください。  
  
## フォーム  
 次のコード例では、<xref:System.Windows.Forms.DataGridView.CellValueNeeded> イベント ハンドラー経由で `Cache` オブジェクトと対話する、読み取り専用の <xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを定義しています。  `Cache` オブジェクトは、ローカルに保存された値を管理し、`DataRetriever` オブジェクトを使用して、Northwind サンプル データベースの Orders テーブルから値を取得します。  また、`Cache` クラスで必要な `IDataPageRetriever` インターフェイスを実装する `DataRetriever` オブジェクトを使用して、<xref:System.Windows.Forms.DataGridView> コントロールの行と列を初期化します。  
  
 `IDataPageRetriever` 型、`DataRetriever` 型、および `Cache` 型については、このトピックの後半で説明します。  
  
> [!NOTE]
>  接続文字列内にパスワードなどの機密情報を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。  データベースへのアクセスを制御する方法としては、Windows 認証 \(統合セキュリティとも呼ばれます\) を使用する方が安全です。  詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## IDataPageRetriever インターフェイス  
 `DataRetriever` クラスによって実装される `IDataPageRetriever` インターフェイスを定義するコード例を次に示します。  このインターフェイスで宣言されているメソッドは、初期行インデックスと 1 ページのデータの行数を要求する `SupplyPageOfData` メソッドだけです。  これらの値は、データ ソースからデータのサブセットを取得する実装側で使用されます。  
  
 `Cache` オブジェクトは、このインターフェイスの実装を構築時に使用して、データの最初の 2 ページを読み込みます。  未キャッシュのデータが必要になると、キャッシュはこれらのページのいずれかを破棄し、`IDataPageRetriever` にその値を含む新しいページを要求します。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## DataRetriever クラス  
 次に、`DataRetriever` クラスを定義するコード例を次に示します。このクラスは、データのページをサーバーから取得する `IDataPageRetriever` インターフェイスを実装します。  `DataRetriever` クラスは、`Columns` プロパティと `RowCount` プロパティも提供します。<xref:System.Windows.Forms.DataGridView> コントロールは、これらのプロパティを使用して、必要な列を作成し、適切な数の空の行を <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションに追加します。  空の行の追加は、テーブル内のデータがすべて存在するようにコントロールが動作するうえで必要です。  これにより、スクロール バーのスクロール ボックスが適切なサイズになり、ユーザーがテーブル内の任意の行にアクセスできるようになります。  行は、スクロール表示されたときにのみ、<xref:System.Windows.Forms.DataGridView.CellValueNeeded> イベント ハンドラーによって値が設定されます。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## Cache クラス  
 次に、`Cache` クラスを定義するコード例を示します。このクラスは、`IDataPageRetriever` 実装によって設定される 2 ページのデータを管理します。  `Cache` クラスは、内側の `DataPage` 構造体を定義します。この構造体は、値を 1 つのキャッシュ ページに保存する <xref:System.Data.DataTable> を含み、ページの上下の境界を表す行インデックスを計算します。  
  
 `Cache` クラスは、構築時に 2 ページのデータを読み込みます。  <xref:System.Windows.Forms.DataGridView.CellValueNeeded> イベントが値を要求すると、`Cache` オブジェクトは、その 2 ページのいずれかに値が存在するかどうか確認し、値が存在する場合には返します。  値がローカルに存在しない場合、`Cache` は、2 つのページのうちで、現在表示されている行から遠い方のページを特定し、そのページを、要求されている値を含む新しいページと置き換えて、値を返します。  
  
 データ ページの行数と、画面に同時に表示できる行数が一致することを前提に、このモデルでは、テーブルをページングしているユーザーが、直前に表示されたページに効率的に復帰できます。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## その他の考慮事項  
 上記のコード例は、Just\-In\-Time データ読み込みの例として紹介されています。  そのため、最大の効率を確保するには、独自のニーズに合わせてコードを変更する必要があります。  少なくとも、キャッシュ内の 1 ページあたりのデータの行数として適切な値を選択する必要があります。  この値は、`Cache` コンストラクターに渡されます。  1 ページあたりの行数は、<xref:System.Windows.Forms.DataGridView> コントロールに同時に表示できる行数以上にする必要があります。  
  
 最適な結果を得るには、パフォーマンス テストと操作性テストを実行し、システムとユーザーの要件を確認する必要があります。  考慮する必要がある要素には、アプリケーションを実行するクライアント コンピューターのメモリ容量、使用するネットワーク接続の有効帯域幅、使用するサーバーの待機時間などがあります。  帯域幅と待機時間は、ピーク使用時に測定する必要があります。  
  
 アプリケーションのスクロール性能を向上させるには、ローカルに保存されるデータ量を増やします。  ただし、起動時間を短縮するには、最初に過度のデータを読み込まないようにする必要があります。  `Cache` クラスを修正して、保存できるデータ ページ数を増大することもできます。  データ ページをより多く使用すると、スクロール効率を改善できますが、有効な帯域幅とサーバーの待機時間に応じて、データ ページの適切な行数を決める必要があります。  ページ数を少なくすると、サーバーへのアクセス頻度が増大しますが、要求したデータが返される時間が短縮します。  帯域幅よりも待機時間の方が問題になる場合は、データ ページを増やす必要があります。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールで Just\-In\-Time データ読み込みを使用して仮想モードを実装する](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)