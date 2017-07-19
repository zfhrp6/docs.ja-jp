---
title: "Windows フォーム DataGridView コントロールでのデータ表示モード | Microsoft Docs"
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
  - "データ [Windows フォーム], 表示モード"
  - "データ グリッド, 表示モード"
  - "DataGridView コントロール [Windows フォーム], 表示モード"
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Windows フォーム DataGridView コントロールでのデータ表示モード
<xref:System.Windows.Forms.DataGridView> コントロールでは、バインド、非バインド、仮想の 3 つの異なるモードでデータを表示できます。  要求に基づいて最適なモードを選択します。  
  
## 非バインド  
 非バインド モードは、プログラムによって管理する、比較的少量のデータを表示するのに適しています。  このモードでは、バインド モードと違って、<xref:System.Windows.Forms.DataGridView> コントロールをデータ ソースに直接アタッチしません。  代わりに、通常、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=fullName> メソッドを使用して、独自にコントロールにデータを設定します。  
  
 非バインド モードは、読み取り専用の静的なデータを表示する場合や、外部データ ストアと対話する独自のコードを提供する場合に特に役立ちます。  ただし、ユーザーが外部データ ソースと対話するようにする場合は、通常、バインド モードを使用します。  
  
 読み取り専用の非バインド <xref:System.Windows.Forms.DataGridView> の使用例については、「[方法 : 連結されていない Windows フォーム DataGridView コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)」を参照してください。  
  
## バインド  
 バインド モードは、データ ストアとの自動対話によってデータを管理するのに適しています。  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティを設定して、データ ソースに直接アタッチできます。  コントロールがデータ バインドの場合、開発者の側で明示的に管理しなくてもデータ行がプッシュおよびプルされます。  <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> プロパティが `true` のときは、データ ソースの各列によって、対応する列がコントロールで作成されます。  独自の列を作成する場合は、このプロパティを `false` に設定し、各列の設定時に <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> プロパティを使用してバインドします。  これは、既定で生成される型以外の列型を使用するときに役立ちます。  詳細については、「[Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 バインド <xref:System.Windows.Forms.DataGridView> コントロールの使用例については、「[チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 バインド モードの <xref:System.Windows.Forms.DataGridView> コントロールには、非バインド列を追加することもできます。  これは、特定の行に対する操作をユーザーが実行できるようにするボタンやリンクの列を表示するときに役立ちます。  また、バインド列に基づいて計算された値を含む列を表示する場合にも役立ちます。  計算された列のセル値は、<xref:System.Windows.Forms.DataGridView.CellFormatting> イベントのハンドラーに設定できます。  ただし、<xref:System.Data.DataSet> や <xref:System.Data.DataTable> をデータ ソースとして使用する場合は、代わりに <xref:System.Data.DataColumn.Expression%2A?displayProperty=fullName> プロパティを使用して、計算された列を生成することもできます。  この場合、<xref:System.Windows.Forms.DataGridView> コントロールは、計算された列を、データ ソース内の他の列と同じように取り扱います。  
  
 バインド モードでの非バインド列による並べ替えはサポートされません。  ユーザーによる編集が可能な値を含む非バインド列をバインド モードで作成した場合は、仮想モードを実装することで、コントロールをバインド列で並べ替えたときにこれらの値を保持する必要があります。  
  
## Virtual  
 仮想モードでは、独自のデータ管理操作を実装できます。  これは、コントロールをバインド列で並べ替えたときに、バインド モードで非バインド列の値を保持するために必要です。  ただし、仮想モードの主要な用途は、大量のデータとやりとりするときにパフォーマンスを最適化することです。  
  
 管理対象であり、データ行をプッシュおよびプルするときにコードで制御するキャッシュに <xref:System.Windows.Forms.DataGridView> コントロールをアタッチします。  メモリの使用量を抑えるには、キャッシュのサイズは、現在表示されている行数と同じにする必要があります。  ユーザーが新しい行をスクロール表示すると、コードが新しいデータをキャッシュに要求し、オプションで以前のデータをメモリからフラッシュします。  
  
 仮想モードを実装する場合は、新しい行がデータ モデルで必要になる時点と、新しい行の追加をロールバックする時点を監視する必要があります。  この機能の正確な実装は、データ モデルの実装とトランザクション セマンティクス \(コミット スコープがセル レベルか、行レベルか\) によって異なります。  
  
 仮想モードの詳細については、「[Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)」を参照してください。  仮想モード イベントの使用例については、「[チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)   
 [チュートリアル : バインドされていない Windows フォーム DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)   
 [方法 : データを Windows フォーム DataGridView コントロールにバインドする](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)