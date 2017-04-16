---
title: "チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装 | Microsoft Docs"
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
  - "仮想モード, チュートリアル"
  - "チュートリアル [Windows フォーム], DataGridView コントロール"
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装
非常に大きな表形式のデータを <xref:System.Windows.Forms.DataGridView> コントロールに表示するときは、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティを `true` に設定して、コントロールとデータ ストアとのやり取りを明示的に管理できます。  これにより、こうした状況でのコントロールのパフォーマンスを微調整できます。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールには、カスタム データ ストアとやり取りするために使用できるイベントが用意されています。  このチュートリアルでは、このようなイベント ハンドラーの実装手順を具体的に示します。  説明しやすくするために、ここで紹介するコード例は非常に単純なデータ ソースを使用しています。  実際のアプリケーションでは、通常は表示に必要な行だけをキャッシュに読み込み、<xref:System.Windows.Forms.DataGridView> イベントを処理して、キャッシュとのやり取りやキャッシュの更新を行います。  詳細については、「[Windows フォーム DataGridView コントロールでの Just\-In\-Time データ読み込みによる仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)」を参照してください。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : Windows フォーム DataGridView コントロールで仮想モードを実装する](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## フォームの作成  
  
#### 仮想モードを実装するには  
  
1.  <xref:System.Windows.Forms.Form> から派生したクラスを作成し、<xref:System.Windows.Forms.DataGridView> コントロールを含めます。  
  
     次のコードでは基本的な初期化を行います。  後の手順で使用する変数を宣言し、`Main` メソッドを定義し、クラス コンストラクターで単純なフォーム レイアウトを作成します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  フォームの <xref:System.Windows.Forms.Form.Load> イベントに対して、<xref:System.Windows.Forms.DataGridView> コントロールを初期化し、データ ストアにサンプルの値を格納するためのハンドラーを実装します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  <xref:System.Windows.Forms.DataGridView.CellValueNeeded> イベントに対して、要求されたセル値をデータ ストアまたは現在編集中の `Customer` オブジェクトから取得するためのハンドラーを実装します。  
  
     このイベントは、<xref:System.Windows.Forms.DataGridView> コントロールがセルを描画しなければならないときに毎回発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  <xref:System.Windows.Forms.DataGridView.CellValuePushed> イベントに対して、編集されたセル値を編集中の行を表す `Customer` オブジェクトに格納するためのハンドラーを実装します。  このイベントは、ユーザーがセル値の変更をコミットすると発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  <xref:System.Windows.Forms.DataGridView.NewRowNeeded> イベントに対して、新しく作成される行を表す `Customer` オブジェクトを作成するためのハンドラーを実装します。  
  
     このイベントは、ユーザーが新しいレコード用の行を入力すると発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  <xref:System.Windows.Forms.DataGridView.RowValidated> イベントに対して、新しい行または変更された行をデータ ストアに保存するためのハンドラーを実装します。  
  
     このイベントは、ユーザーが現在の行を変更すると発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> イベントに対して、ユーザーが Esc キーを \(編集モードの場合は 2 回、編集モードでない場合は 1 回\) 押して行の復帰を指示したときに <xref:System.Windows.Forms.DataGridView.CancelRowEdit> イベントを発生させるかどうかを設定するハンドラーを実装します。  
  
     <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> イベント ハンドラー内で <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=fullName> プロパティを `true` に設定していない場合は、現在行の中の任意のセルが修正されているときに行の復帰を指示すると、既定で <xref:System.Windows.Forms.DataGridView.CancelRowEdit> イベントが発生します。  このイベントは、コミットのスコープが実行時に決定される場合に役立ちます。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  <xref:System.Windows.Forms.DataGridView.CancelRowEdit> イベントに対して、現在行を表す `Customer` オブジェクトの値を破棄するためのハンドラーを実装します。  
  
     このイベントは、ユーザーが Esc キーを \(編集モードでは 2 回、編集モード以外では 1 回\) 押して行の復帰を指示したときに発生します。  このイベントは、現在行の中に変更されたセルがない場合や、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> イベント ハンドラー内で <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=fullName> プロパティの値が `false` に設定されている場合には発生しません。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <xref:System.Windows.Forms.DataGridView.UserDeletingRow> イベントに対して、既存の `Customer` オブジェクトをデータ ストアから削除したり、新しく作成された行を表す保存されていない `Customer` オブジェクトを破棄したりするためのハンドラーを実装します。  
  
     このイベントは、ユーザーが行ヘッダーをクリックした後に Del キーを押して行を削除すると発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. このコード例で使用されるデータ項目を表す単純な `Customers` クラスを実装します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### フォームをテストするには  
  
-   アプリケーションをコンパイルして実行します。  
  
     3 件の顧客レコードを含んだ <xref:System.Windows.Forms.DataGridView> コントロールが表示されます。  行内の複数のセルの値を変更した後に、Esc キーを \(編集モードの場合は 2 回、編集モードでない場合は 1 回\) 押すと、行全体を元の値に戻すことができます。  コントロール内の行を変更、追加、または削除すると、データ ストア内の `Customer` オブジェクトも変更、追加、削除されます。  
  
## 次の手順  
 このアプリケーションは、<xref:System.Windows.Forms.DataGridView> コントロールの仮想モードを実装するときに処理しなければならないイベントの基本を示しています。  このアプリケーションはさまざまな方法で改良できます。  
  
-   外部データベースから値をキャッシュするデータ ストアを実装します。  このキャッシュは必要に応じて値を取得および破棄するので、表示に必要なデータだけを格納し、クライアント コンピューターのメモリ消費量を抑えることができます。  
  
-   データ ストアのパフォーマンスを要件に合わせて微調整します。  たとえば、クライアント コンピューターのメモリの制限よりも、ネットワーク接続の遅さをカバーするためには、大きなサイズのキャッシュを使用して、データベース クエリの回数を最小限に抑えます。  
  
 外部データベースから値をキャッシュする方法の詳細については、「[方法 : Windows フォーム DataGridView コントロールで Just\-In\-Time データ読み込みを使用して仮想モードを実装する](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)」を参照してください。  
  
## 参照  
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
 [Windows フォーム DataGridView コントロールでの Just\-In\-Time データ読み込みによる仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)   
 [方法 : Windows フォーム DataGridView コントロールで仮想モードを実装する](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)