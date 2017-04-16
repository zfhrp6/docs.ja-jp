---
title: "方法 : 子テーブルの選択行が現在位置を保持することを保証する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "キャッシュ [.NET Framework], 子の位置"
  - "子の位置"
  - "子テーブルの行の選択"
  - "現在の子の位置"
  - "データ バインディング [.NET Framework], 行の選択"
  - "マスター/詳細ビュー [Windows フォーム]"
  - "マスター/詳細ビュー"
  - "親/子ビュー [Windows フォーム]"
  - "リセット (子の位置を)"
  - "行位置 [Windows フォーム]"
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 子テーブルの選択行が現在位置を保持することを保証する
多くの場合、Windows フォームでデータ バインディングを処理するときは、いわゆる親\/子ビューまたはマスター\/詳細ビューにデータを表示します。  これは、同一ソースのデータが、2 つのコントロールに表示されるデータ バインディング シナリオを示します。  片方のコントロールで選択を変更すると、他方のコントロールに表示されるデータが変化します。  たとえば、第 1 のコントロールに顧客リストが含まれ、第 2 のコントロールに、第 1 のコントロールで選択された顧客に関連する注文リストが含まれます。  
  
 .NET Framework Version 2.0 以降、親\/子ビューにデータを表示する場合は、子テーブルで現在選択されている行が、親テーブルの先頭行にリセットされないようにするために、追加の手順を実行する必要があります。  そのためには、子テーブルの位置をキャッシュし、親テーブルが変更された後で位置をリセットする必要があります。  通常、子テーブルのリセットは、親テーブルの行のフィールドが初めて変更されたときに発生します。  
  
### 子テーブルの現在位置をキャッシュするには  
  
1.  子リストの位置を格納する整数変数と、子の位置をキャッシュするかどうかを示すブール変数を宣言します。  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  バインディングの <xref:System.Windows.Forms.CurrencyManager> の <xref:System.Windows.Forms.CurrencyManager.ListChanged> イベントを処理し、<xref:System.ComponentModel.ListChangedType> の <xref:System.ComponentModel.ListChangedType> をチェックします。  
  
3.  <xref:System.Windows.Forms.CurrencyManager> の現在位置をチェックします。  それがリストの最初のエントリ \(通常は 0\) よりも大きい場合は、変数に保存します。  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  親リストの親現在位置マネージャーの <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> イベントを処理します。  ハンドラーで、キャッシュ シナリオではないことを示すブール値を設定します。  <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> が発生した場合、親の変更はリストの位置の変更であり、項目値の変更ではありません。  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### 子の位置をリセットするには  
  
1.  子のバインディングの <xref:System.Windows.Forms.CurrencyManager> の <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> イベントを処理します。  
  
2.  子テーブルの位置を、前の手順で保存したキャッシュ位置にリセットします。  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## 使用例  
 子テーブルの <xref:System.Windows.Forms.CurrencyManager> の現在位置を保存し、親テーブルの編集が完了した後でその位置をリセットする方法を次の例に示します。  この例には、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用して <xref:System.Data.DataSet> 内の 2 つのテーブルにバインドされた 2 つの <xref:System.Windows.Forms.DataGridView> コントロールが含まれます。  この 2 つのテーブルの間にリレーションシップが確立され、そのリレーションシップが <xref:System.Data.DataSet> に追加されます。  子テーブル内の位置は、デモを目的として、3 行目に初期設定されています。  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 このコード例をテストするには、次の手順を実行します。  
  
1.  例を実行します。  
  
2.  \[**Cache and reset position**\] \(位置をキャッシュしてリセットする\) チェック ボックスがオンであることを確認します。  
  
3.  \[**Clear parent field**\] \(親フィールドのクリア\) ボタンをクリックして、親テーブルのフィールドを変更します。  子テーブル内の選択行が変更されないことに注目してください。  
  
4.  例をいったん閉じてから、例を再実行します。  リセット動作は親行が初めて変更された場合のみ発生するので、この操作を実行する必要があります。  
  
5.  \[**Cache and reset position**\] \(位置をキャッシュしてリセットする\) チェック ボックスをオフにします。  
  
6.  \[**Clear parent field**\] \(親フィールドのクリア\) ボタンをクリックします。  子テーブル内の選択行が 1 行目に変更されることに注目してください。  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、System.Windows.Forms、および System.XML の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法の詳細は、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 [方法 : 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)   
 [BindingSource コンポーネント](../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)