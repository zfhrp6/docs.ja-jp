---
title: 'チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 52e93ebe0b2903fdf2fe97f4ce812331e740f8b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539920"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装
非常に大量の表形式データを表示する場合、<xref:System.Windows.Forms.DataGridView>コントロールを設定できます、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティを`true`と明示的にそのデータ ストアとコントロールの相互作用を管理します。 このような状況で、コントロールのパフォーマンスを微調整できます。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールには、カスタム データ ストアとの対話を処理できるいくつかのイベントが用意されています。 このチュートリアルでは、これらのイベント ハンドラーを実装するプロセスを説明します。 このトピックのコード例では、わかりやすくするための非常に単純なデータ ソースを使用します。 実稼働設定をキャッシュ内に表示し、処理する必要がある行のみをロードするは通常<xref:System.Windows.Forms.DataGridView>とやり取りして、キャッシュを更新するイベントです。 詳細については、次を参照してください[Windows フォーム DataGridView コントロールで Just-In-Time データ読み込みで仮想モードの実装。](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: Windows フォーム DataGridView コントロールで仮想モードを実装する](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-implement-virtual-mode"></a>仮想モードを実装するには  
  
1.  派生するクラスを作成する<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
     次のコードには、基本的な初期化が含まれています。 後の手順で使用されるいくつかの変数を宣言して、提供、`Main`メソッド、およびクラス コンス トラクターでの単純なフォーム レイアウトを提供します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  フォームの用のハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>を制御し、サンプルの値を使用してデータ ストアを追加します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>データ ストアから要求されたセルの値を取得するイベントまたは`Customer`現在編集中のオブジェクト。  
  
     このイベントが発生するたびに、<xref:System.Windows.Forms.DataGridView>コントロールがセルを描画する必要があります。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CellValuePushed>で編集されたセル値を格納するイベント、`Customer`編集された行を表すオブジェクト。 このイベントは、ユーザーがセル値の変更をコミットするたびに発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.NewRowNeeded>新たに作成するイベント`Customer`を新しく作成された行を表すオブジェクト。  
  
     このイベントは、ユーザーが新しいレコードの行を入力するたびに発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.RowValidated>新しいまたは変更された行をデータ ストアに保存するイベントです。  
  
     このイベントは、ユーザーが、現在の行を変更するたびに発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベントを示すかどうか、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>イベントは、ユーザーが ESC キーを押して編集モードで 2 回または 1 回は編集モードの外部で行バージョンを再設定を示すときに発生します。  
  
     既定では、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>しない限り、現在の行内のセルが変更されたときに、行バージョンを再設定時に発生、<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>プロパティに設定されている`true`で、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベント ハンドラー。 このイベントは、実行時にコミットのスコープを決定する場合に便利です。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>の値を破棄するイベント、`Customer`現在の行を表すオブジェクト。  
  
     このイベントは、ユーザーが ESC キーを押して編集モードで 2 回または 1 回は編集モードの外部で行バージョンを再設定を示すときに発生します。 このイベントは、現在の行のセルが修正されていない場合、またはの値、<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>プロパティに設定された`false`で、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベント ハンドラー。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.UserDeletingRow>既存を削除するイベント`Customer`データ ストアからオブジェクトまたは破棄され、保存されていない`Customer`を新しく作成された行を表すオブジェクト。  
  
     このイベントは、ユーザーは、行ヘッダーをクリックして、DEL キーを押して行を削除するたびに発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. 単純な実装`Customers`このコード例で使用されるデータ項目を表すクラス。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   アプリケーションをコンパイルして実行します。  
  
     表示されます、<xref:System.Windows.Forms.DataGridView>コントロールが次の 3 つの顧客レコードを格納します。 行の複数のセルの値を変更し、編集モードで 2 回クリック 1 回、および元の値に行全体を戻すには編集モードの外部では、esc キーを押してできます。 変更、追加、または、コントロール内の行を削除するときに`Customer`データ ストア内のオブジェクトの変更、追加、または同時に削除します。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでの仮想モードを実装する必要がありますを処理するイベントの基本を理解、<xref:System.Windows.Forms.DataGridView>コントロール。 さまざまな方法で、この基本的なアプリケーションを改善することができます。  
  
-   外部データベースから値をキャッシュするデータ ストアを実装します。 キャッシュは、取得し、クライアント コンピューターで少量のメモリを消費しているときに表示するために必要なことのみが含まれるように、必要に応じて値を破棄する必要があります。  
  
-   要件に応じて、データ ストアのパフォーマンスを微調整します。 たとえば、補正するためにクライアント コンピューターのメモリ制限ではなく、低速ネットワーク接続を大きなサイズのキャッシュを使用し、データベース クエリの数を最小限に抑えることができます。  
  
 外部データベースから値をキャッシュの詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで Just-In-Time データ読み込みによる仮想モードを実装する](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [方法: Windows フォーム DataGridView コントロールで仮想モードを実装する](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
