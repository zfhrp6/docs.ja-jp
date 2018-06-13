---
title: Windows フォーム DataGridView コントロール内の列の並べ替えモード
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: 9ebcfc435fcc7d2b0dfbfe3004d958c73dd1347c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529689"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロール内の列の並べ替えモード
<xref:System.Windows.Forms.DataGridView> 列では、次の 3 つの並べ替えモードがあります。 各列の並べ替えモードを指定、 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 、次のいずれかに設定することができる列のプロパティ<xref:System.Windows.Forms.DataGridViewColumnSortMode>列挙値。  
  
|`DataGridViewColumnSortMode` の値|説明|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|テキスト ボックスの列の既定値です。 選択範囲に列ヘッダーが使用される場合を除き、列ヘッダーをクリックすると、自動的にソート、<xref:System.Windows.Forms.DataGridView>この列でし、並べ替え順序を示すグリフを表示します。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|非テキスト ボックスの列の既定値です。 この列をプログラムで並べ替えることができます。ただし、ものではありません、並べ替えのため、並べ替えグリフの領域が予約されていません。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|プログラムでは、この列を並べ替えることができ、並べ替えのグリフの領域が予約されています。|  
  
 既定値は、列の並べ替えモードを変更する可能性があります<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>明確注文可能な値が含まれている場合。 項目の状態を表す数値を含むデータベースの列があれば、たとえば、image 列をデータベース列にバインドすることによってこれらの数値を対応するアイコンに表示できます。 ハンドラーをイメージの表示値に数値のセルの値を変更し、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベント。 この場合、設定、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティを<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>列の並べ替えにユーザーを有効になります。 自動並べ替えにより、ユーザーは、番号に対応する状態は自然な順序を持っていない場合でも同じ状態にあるアイテムをグループ化します。 チェック ボックス列は、自動的な並べ替えは同じ状態で項目をグループ化するために役立ちます別の例です。  
  
 並べ替えることができます、<xref:System.Windows.Forms.DataGridView>プログラム任意の列またはに関係なく、複数の列の値によって、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>設定します。 プログラムによる並べ替えを並べ替えるため、独自のユーザー インターフェイス (UI) を提供する場合、またはカスタムの並べ替えを実装するときに便利です。 指定する、独自の並べ替えの UI は、便利ですが、たとえば、設定すると、<xref:System.Windows.Forms.DataGridView>選択モード列のヘッダーの選択を有効にします。 この場合、並べ替え、列ヘッダーを使用することはできません、か、ヘッダーを設定するように、適切な並べ替えグリフを表示する、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティを<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>です。  
  
 プログラムによる並べ替えモードに設定されている列は、自動的に並べ替えグリフを表示しません。 これらの列にする必要があります、グリフ自分で設定して表示する、<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>プロパティです。 これは、カスタムの並べ替えを柔軟にする場合に必要です。 たとえば、ソートする場合、<xref:System.Windows.Forms.DataGridView>複数の列で並べ替えに複数の字形またはない並べ替えグリフを表示する場合があります。  
  
 プログラムで並べ替えることができますが、<xref:System.Windows.Forms.DataGridView>任意の列でボタンは、列などのいくつかの列では、可能性があります値が含まれないことができる明確です。 これらの列に対して、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティの設定<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>並べ替えグリフのヘッダー内の領域を予約する必要がないことには使用されず、並べ替えを示します。  
  
 ときに、<xref:System.Windows.Forms.DataGridView>は並べ替えが実行を特定する並べ替え列と並べ替え順序の両方の値のチェック、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>と<xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティです。 カスタム並べ替え操作の後にこれらの値を意味することがありません。 カスタムの並べ替えの詳細については、このトピックの「カスタムの並べ替え」を参照してください。  
  
 ときに、<xref:System.Windows.Forms.DataGridView>バインドとバインドされていない列を含むコントロールが並べ替えられて、自動的にバインドされていない列の値を保持することはできません。 これらの値を維持するために設定して仮想モードを実装する必要があります、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティを`true`処理し、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>と<xref:System.Windows.Forms.DataGridView.CellValuePushed>イベント。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで仮想モードを実装する](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)です。 バインド モードで非バインド列による並べ替えはサポートされていません。  
  
## <a name="programmatic-sorting"></a>プログラムによる並べ替え  
 並べ替えることができます、<xref:System.Windows.Forms.DataGridView>呼び出すことによってプログラムでその<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドです。  
  
 `Sort(DataGridViewColumn,ListSortDirection)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドは、<xref:System.Windows.Forms.DataGridViewColumn>と<xref:System.ComponentModel.ListSortDirection>パラメーターとしての列挙値。 このオーバー ロードは、値を明確注文することができますが、自動並べ替えを構成するたくないを列で並べ替える場合に便利です。 このオーバー ロードを呼び出すし、列に渡す、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>のプロパティの値<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>と<xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティが自動的に設定し、列ヘッダーに適切な並べ替えグリフが表示されます。  
  
> [!NOTE]
>  ときに、<xref:System.Windows.Forms.DataGridView>を設定して、外部データ ソースにコントロールがバインドされている、 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 、プロパティ、`Sort(DataGridViewColumn,ListSortDirection)`バインドされていない列に対してメソッドのオーバー ロードは機能しません。 また、ときに、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティは`true`、バインドされた列に対してのみ、このオーバー ロードを呼び出すことができます。 列のデータ バインドがあるかどうかを確認するには<xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>プロパティの値。 バインド モードでバインドされていない列の並べ替えはサポートされていません。  
  
## <a name="custom-sorting"></a>カスタムの並べ替え  
 カスタマイズできる<xref:System.Windows.Forms.DataGridView>を使用して、`Sort(IComparer)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドまたは処理することにより、<xref:System.Windows.Forms.DataGridView.SortCompare>イベント。  
  
 `Sort(IComparer)`メソッドのオーバー ロードを実装するクラスのインスタンスを受け取り、<xref:System.Collections.IComparer>パラメーターとしてインターフェイスです。 このオーバー ロードは、カスタムの並べ替え; を指定する場合に役立ちますたとえば、列の値を持っていない場合、自然な並べ替え順序またはときに、自然の並べ替え順序がありません適切です。 この場合、自動並べ替えを使用することはできませんが、する場合でも、ユーザーが列見出しをクリックして並べ替え。 ハンドラーで、このオーバー ロードを呼び出すことができます、<xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick>イベントの選択列ヘッダーを使用しない場合。  
  
> [!NOTE]
>  `Sort(IComparer)`メソッドのオーバー ロードされる場合にのみの動作、<xref:System.Windows.Forms.DataGridView>コントロールは、外部データ ソースにバインドされていないと、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティの値が`false`です。 外部データ ソースにバインドされている列の並べ替えをカスタマイズするには、データ ソースによって提供される並べ替え操作を使用する必要があります。 仮想モードでバインドされていない列に対して独自の並べ替え操作を指定する必要があります。  
  
 使用する、`Sort(IComparer)`メソッド オーバー ロードを実装するクラスを作成する必要があります、<xref:System.Collections.IComparer>インターフェイスです。 このインターフェイスを実装するクラスが必要です、<xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>先のメソッド、<xref:System.Windows.Forms.DataGridView>渡します<xref:System.Windows.Forms.DataGridViewRow>としてオブジェクトの入力時に、`Sort(IComparer)`メソッドのオーバー ロードが呼び出されます。 これにより、任意の列の値に基づいて正しい行の順序を計算することができます。  
  
 `Sort(IComparer)`メソッドのオーバー ロードが設定されていない、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>と<xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティ、常に設定する必要がありますので、<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>並べ替えグリフを表示するプロパティです。  
  
 代わりに、`Sort(IComparer)`メソッド オーバー ロードを使用できるハンドラーを実装することによってカスタムの並べ替え、<xref:System.Windows.Forms.DataGridView.SortCompare>イベント。 このイベントは、ユーザーが自動的に並べ替えるかを呼び出すと用に構成された列のヘッダーをクリックしたときに発生、`Sort(DataGridViewColumn,ListSortDirection)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドです。 イベントは、適切な順序を計算できるように、コントロール内の行の各ペアに対して発生します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare>イベントが発生しないときに、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティが設定されて場合や、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティの値が`true`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>  
 [Windows フォームの DataGridView コントロールでのデータの並べ替え](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
