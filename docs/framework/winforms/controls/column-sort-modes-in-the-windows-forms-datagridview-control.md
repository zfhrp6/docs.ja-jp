---
title: "Windows フォーム DataGridView コントロール内の列の並べ替えモード | Microsoft Docs"
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
  - "データ グリッド, 並べ替えモード"
  - "DataGridView コントロール [Windows フォーム], 並べ替えモード"
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Windows フォーム DataGridView コントロール内の列の並べ替えモード
<xref:System.Windows.Forms.DataGridView> 列には、3 つの並べ替えモードがあります。  各列の並べ替えモードは、列の <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> プロパティによって指定されます。このプロパティは、次の <xref:System.Windows.Forms.DataGridViewColumnSortMode> 列挙値のいずれかに設定できます。  
  
|`DataGridViewColumnSortMode` の値|Description|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|テキスト ボックス列の既定値です。  列ヘッダーを選択用として使用する場合を除き、ヘッダーをクリックすると、この列で <xref:System.Windows.Forms.DataGridView> が自動的に並べ替えられ、並べ替え順序を示すグリフが表示されます。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|非テキスト ボックス列の既定値です。  この列は、プログラムによって並べ替えることができますが、並べ替えを目的としていないため、並べ替えグリフの表示領域は予約されません。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|この列はプログラムによって並べ替えることができ、並べ替えグリフの表示領域が予約されます。|  
  
 意味のある順序で並べることができる値が列に含まれている場合は、既定で <xref:System.Windows.Forms.DataGridViewColumnSortMode> に設定される列の並べ替えモードを変更できます。  たとえば、項目の状態を表す数値がデータベース列に含まれている場合、イメージ列をデータベース列に関連付けることによって、これらの数値を対応するアイコンとして表示できます。  次に、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> イベントのハンドラーで、数値セルの値をイメージ表示値に変更できます。  この場合、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> プロパティに<xref:System.Windows.Forms.DataGridViewColumnSortMode> を設定すると、ユーザーによる列の並べ替えが可能になります。  自動並べ替えにより、ユーザーは、数値に対応する状態が自然なシーケンスでない場合でも、同じ状態の項目をグループ化できます。  自動並べ替えは、チェック ボックス列の場合にも同じ状態の項目をグループ化するのに役立ちます。  
  
 <xref:System.Windows.Forms.DataGridView> は、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> の設定と無関係に、任意の列または複数の列の値を基準にして、プログラムによって並べ替えることができます。  プログラムによる並べ替えは、独自の並べ替え用ユーザー インターフェイス \(UI\) を提供したり、カスタムの並べ替え機能を実装したりする場合に役立ちます。  独自の並べ替え UI の提供は、たとえば、<xref:System.Windows.Forms.DataGridView> 選択モードを設定して列ヘッダーの選択を有効にする場合に役立ちます。  この場合、列ヘッダーは並べ替えで使用できませんが、適切な並べ替えグリフをヘッダーに表示して、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> プロパティに <xref:System.Windows.Forms.DataGridViewColumnSortMode> を設定できます。  
  
 プログラムによる並べ替えモードに設定された列には、並べ替えグリフが自動的には表示されません。  このような列では、<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName> プロパティを設定して、グリフを独自に表示する必要があります。  これは、カスタムの並べ替えを柔軟にする場合に必要です。  たとえば、複数の列で <xref:System.Windows.Forms.DataGridView> を並べ替える場合、複数の並べ替えグリフを表示したり、1 つも表示しないようにしたりする必要があります。  
  
 <xref:System.Windows.Forms.DataGridView> は、任意の列を基準にプログラムによって並べ替えることができますが、ボタン列などの一部の列には、意味のある順序で並べることのできる値を格納できないことがあります。  このような列では、<xref:System.Windows.Forms.DataGridViewColumnSortMode> の <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> プロパティ設定により、列が並べ替えで使用されないため、並べ替えグリフの表示領域をヘッダーで予約する必要がないことが示されています。  
  
 <xref:System.Windows.Forms.DataGridView> を並べ替えるときは、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A> プロパティと <xref:System.Windows.Forms.DataGridView.SortOrder%2A> プロパティの値をチェックにして、並べ替え列と並べ替え順序を共に確認できます。  これらの値は、カスタムの並べ替え操作を実行した後には意味がなくなります。  カスタムの並べ替えの詳細については、後記の「カスタムの並べ替え」を参照してください。  
  
 バインド列と非バインド列の両方を含む <xref:System.Windows.Forms.DataGridView> コントロールを並べ替えるときは、非バインド列の値を自動的に保持できません。  これらの値を保持するには、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティに `true` を設定し、<xref:System.Windows.Forms.DataGridView.CellValueNeeded> イベントと <xref:System.Windows.Forms.DataGridView.CellValuePushed> イベントを処理して、仮想モードを実装する必要があります。  詳細については、「[方法 : Windows フォーム DataGridView コントロールで仮想モードを実装する](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)」を参照してください。  バインド モードでの非バインド列による並べ替えはサポートされません。  
  
## プログラムによる並べ替え  
 <xref:System.Windows.Forms.DataGridView> をプログラムによって並べ替えるには、<xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドを呼び出します。  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(DataGridViewColumn,ListSortDirection)` オーバーロードでは、パラメーターとして <xref:System.Windows.Forms.DataGridViewColumn> 列挙値と <xref:System.ComponentModel.ListSortDirection> 列挙値を受け取ります。  このオーバーロードは、意味のある順序で並べることができる値を含んでいても、自動並べ替えを設定するのが望ましくない列で並べ替える場合に役立ちます。  このオーバーロードを呼び出し、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> プロパティ値が <xref:System.Windows.Forms.DataGridViewColumnSortMode?displayProperty=fullName> の列に渡すと、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A> プロパティと <xref:System.Windows.Forms.DataGridView.SortOrder%2A> プロパティが自動的に設定され、適切な並べ替えグリフが列ヘッダーに表示されます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティを設定して、<xref:System.Windows.Forms.DataGridView> コントロールを外部データ ソースにバインドした場合、`Sort(DataGridViewColumn,ListSortDirection)` メソッド オーバーロードは、非バインド列に対して使用できません。  また、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティが `true` の場合、このオーバーロードは、バインド列に対してのみ呼び出すことができます。  列がデータ バインドかどうかを確認するには、<xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> プロパティ値を調べます。  バインド モードでの非バインド列の並べ替えはサポートされません。  
  
## カスタムの並べ替え  
 <xref:System.Windows.Forms.DataGridView> をカスタマイズするには、<xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(IComparer)` オーバーロードを使用するか、<xref:System.Windows.Forms.DataGridView.SortCompare> イベントを処理します。  
  
 `Sort(IComparer)` メソッド オーバーロードでは、<xref:System.Collections.IComparer> インターフェイスを実装するクラスのインスタンスをパラメーターとして受け取ります。  このオーバーロードが役立つのは、たとえば、列の値が自然な並べ替え順序を持たない場合や自然な並べ替え順序が不適切な場合など、カスタムな並べ替えを実現する場合です。  この場合、自動並べ替えは使用できませんが、ユーザーが列ヘッダーをクリックして並べ替えることができます。  列ヘッダーを選択用として使用しない場合は、このオーバーロードを <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> イベントのハンドラーで呼び出すことができます。  
  
> [!NOTE]
>  `Sort(IComparer)` メソッド オーバーロードは、<xref:System.Windows.Forms.DataGridView> コントロールが外部データ ソースにバインドされておらず、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティ値が `false` のときにのみ使用できます。  外部データ ソースにバインドされた列の並べ替えをカスタマイズするには、データ ソースによって提供される並べ替え操作を使用する必要があります。  仮想モードでは、非バインド列に対して独自の並べ替え操作を実行できるようにする必要があります。  
  
 `Sort(IComparer)` メソッド オーバーロードを使用するには、<xref:System.Collections.IComparer> インターフェイスを実装する独自のクラスを作成する必要があります。  このインターフェイスでは、クラスで <xref:System.Collections.IComparer.Compare%2A?displayProperty=fullName> メソッドを実装する必要があります。このメソッドには、`Sort(IComparer)` メソッド オーバーロードが呼び出されたときに、<xref:System.Windows.Forms.DataGridView> から <xref:System.Windows.Forms.DataGridViewRow> オブジェクトが入力として渡されます。  これにより、任意の列の値を基にして適切な行の順序を計算できます。  
  
 `Sort(IComparer)` メソッド オーバーロードは、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A> プロパティと <xref:System.Windows.Forms.DataGridView.SortOrder%2A> プロパティを設定しないため、並べ替えグリフが表示されるように常に <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName> プロパティを設定する必要があります。  
  
 `Sort(IComparer)` メソッド オーバーロードを使用する代わりに、<xref:System.Windows.Forms.DataGridView.SortCompare> イベントのハンドラーを実装して、カスタムの並べ替えを可能にすることもできます。  このイベントは、自動並べ替えが設定された列のヘッダーをユーザーがクリックしたり、<xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(DataGridViewColumn,ListSortDirection)` オーバーロードを呼び出したりすると発生します。  このイベントは、コントロール内の行の各ペアに対して発生するため、行の適切な順序を計算できます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare> イベントは、<xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティが設定されている場合や、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティ値が `true` の場合には発生しません。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName>   
 [Windows フォームの DataGridView コントロールでのデータの並べ替え](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)