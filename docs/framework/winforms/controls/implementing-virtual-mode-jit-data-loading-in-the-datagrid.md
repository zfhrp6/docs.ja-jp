---
title: Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: ad3ec7fb2e0012459bcf597ac9abee76c20b767e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540918"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装
仮想モードを実装する 1 つの理由、<xref:System.Windows.Forms.DataGridView>コントロールは、必要なデータのみを取得します。 これと呼ばれる *- just-in-time データ読み込み*です。  
  
 リモート データベースで非常に大きなテーブルで作業している場合などの可能性がありますを避けたいスタートアップの遅延を表示するために必要なデータのみを取得し、ユーザー ビューに新しい行をスクロールする場合にのみ、追加のデータを取得するとします。 アプリケーションを実行しているクライアント コンピューター データの格納に使用可能なメモリ量が限られている場合、データベースから新しい値を取得するときに使用されていないデータを破棄することがもできます。  
  
 次のセクションでは、使用する方法を説明する、 <xref:System.Windows.Forms.DataGridView> ・ イン タイムのキャッシュを制御します。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: Windows フォーム DataGridView コントロールで Just-In-Time データ読み込みによる仮想モードを実装する](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)です。  
  
## <a name="the-form"></a>フォーム  
 次のコード例は、読み取り専用を含むフォームを定義<xref:System.Windows.Forms.DataGridView>と連携するコントロール、`Cache`オブジェクトを介して、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>イベント ハンドラー。 `Cache`オブジェクトがローカルに保存された値を管理しを使用して、 `DataRetriever` Northwind サンプル データベースの Orders テーブルから値を取得するオブジェクト。 `DataRetriever`を実装するオブジェクト、`IDataPageRetriever`必要なインターフェイスを`Cache`クラスは、初期化するために使用も、<xref:System.Windows.Forms.DataGridView>行および列を制御します。  
  
 `IDataPageRetriever`、 `DataRetriever`、および`Cache`型はこのトピックの後半で説明します。  
  
> [!NOTE]
>  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>示しますインターフェイス  
 次のコード例を定義、`IDataPageRetriever`によって実装されるインターフェイス、`DataRetriever`クラスです。 このインターフェイスで宣言されている唯一の方法は、`SupplyPageOfData`メソッドで、最初の行インデックスおよびデータの 1 つのページ内の行の数のカウントが必要です。 これらの値は、データ ソースからデータのサブセットを取得、実装者によって使用されます。  
  
 A`Cache`オブジェクト構築時にこのインターフェイスの実装を使用してデータの最初の 2 つのページを読み込めません。 キャッシュがこれらのページのいずれかを破棄しから値を含む新しいページを要求にキャッシュされていない値が必要になったら、`IDataPageRetriever`です。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever クラス  
 次のコード例を定義、`DataRetriever`クラスを実装する、`IDataPageRetriever`サーバーからのデータ ページを取得するインターフェイスです。 `DataRetriever`クラスも用意されています。`Columns`と`RowCount`プロパティを、<xref:System.Windows.Forms.DataGridView>コントロールを使用して必要な列を作成し、適切な数の空の行を追加、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション。 空の行を追加すると、テーブル内のすべてのデータが含まれている場合と同様に、コントロールが動作できるように、必要があります。 これは、スクロール バーのスクロール ボックスは、適切なサイズを持ち、ユーザーがテーブル内の任意の行にアクセスできることを意味します。 によって、行がいっぱいになる、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>ビューにスクロールする場合にのみ、イベント ハンドラー。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>キャッシュ クラス  
 次のコード例を定義、`Cache`クラスを介して作成されるデータの 2 つのページ、`IDataPageRetriever`実装します。 `Cache`クラス定義の内部`DataPage`を格納する構造体、<xref:System.Data.DataTable>値を 1 つのキャッシュに格納するページと行のインデックスを作成する計算を上限と下限の境界を表してページ。  
  
 `Cache`クラスは、構築時にデータの 2 つのページを読み込みます。 ときに、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>イベントは、値を要求、`Cache`オブジェクトかどうかを値がで使用できるその 2 つのいずれかのページがあれば、それを返します。 値が使用できないローカルで場合、`Cache`オブジェクトを調べ、その 2 つのページのうち、現在表示されている行から最も遠いし、返します、要求された値を含む新しい 1 つのページに置換します。  
  
 仮定すると、データ ページ内の行の数を一度に画面に表示できる行の数と同じで、このモデルは、ページングの表に、ユーザーが効率的に、最も最近表示したページに戻りますを使用できます。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>その他の考慮事項  
 前のコード例は、just-in-time データ読み込みの例として提供されます。 独自のニーズに最も効率を実現するためにコードを変更する必要があります。 少なくとも、キャッシュ内のデータの 1 ページあたりの行の数の適切な値を選択する必要があります。 この値に渡される、`Cache`コンス トラクターです。 1 ページあたりの行の数にする必要がありますで同時に表示できる行の数よりも小さいか不要、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 最良の結果をパフォーマンス テストと使いやすさは、システムと、ユーザーの要件を決定するテストを実施する必要があります。 考慮する必要がありますをいくつかの要因は、アプリケーション、使用すると、ネットワーク接続の使用可能な帯域幅使用されるサーバーの待機時間を実行しているクライアント コンピューターにメモリの量を含めます。 帯域幅と待機時間は、ピーク時決定してください。  
  
 アプリケーションのスクロールのパフォーマンスを向上させるのには、ローカルに格納されているデータの量を変更できます。 起動時間を向上させるのにする必要がありますは避けてください大量のデータを最初に読み込みます。 変更することも、`Cache`クラスを格納できるデータ ページの数を増やします。 スクロールの効率を向上させる多くのデータ ページを使用することができますが、使用可能な帯域幅とサーバーの待機時間に応じてのデータ ページ内の行の最適な数を決定する必要があります。 サイズの小さいページは、サーバーより頻繁にアクセスするより短時間で要求されたデータを返します。 待機時間がより多くの帯域幅よりも、問題の場合は、大きなデータ ページを使用することがあります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールで Just-In-Time データ読み込みを使用して仮想モードを実装する](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
