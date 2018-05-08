---
title: Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: d0a82d5724ebe142ae080fc930665733e701e237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて
<xref:System.Windows.Forms.DataGridView>コントロールは、新しいコントロールを置き換える、<xref:System.Windows.Forms.DataGrid>コントロール。 <xref:System.Windows.Forms.DataGridView>コントロールで欠落している多数の基本と高度な機能を提供する、<xref:System.Windows.Forms.DataGrid>コントロール。 さらのアーキテクチャ、<xref:System.Windows.Forms.DataGridView>コントロールを使用すると拡張とカスタマイズよりもはるかに簡単、<xref:System.Windows.Forms.DataGrid>コントロール。  
  
 次の表に、いくつかの主な機能で使用できる、<xref:System.Windows.Forms.DataGridView>から欠落しているコントロール、<xref:System.Windows.Forms.DataGrid>コントロール。  
  
|DataGridView コントロールの機能|説明|  
|----------------------------------|-----------------|  
|複数の列型|<xref:System.Windows.Forms.DataGridView>コントロールより多くの組み込み列の型が用意されています、<xref:System.Windows.Forms.DataGrid>コントロール。 これらの列型は、最も一般的なシナリオのニーズを満たすが簡単に拡張または置換列内の型よりも、<xref:System.Windows.Forms.DataGrid>コントロール。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)です。|  
|データを表示するいくつかの方法|<xref:System.Windows.Forms.DataGrid>コントロールは、外部データ ソースからデータを表示するのには限定されます。 <xref:System.Windows.Forms.DataGridView>コントロールではただし、コントロール、バインドされたデータ ソースからのデータまたはバインドとバインドされていないデータに一緒に格納されているバインドされていないデータを表示できます。 仮想モードを実装することも、<xref:System.Windows.Forms.DataGridView>カスタム データの管理を提供するコントロール。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)です。|  
|データの表示をカスタマイズするいくつかの方法|<xref:System.Windows.Forms.DataGridView>コントロールには、多数のプロパティとデータを書式設定および表示する方法を指定するためのイベントが用意されています。 セル、行、および含まれるデータに依存する列の外観を変更するなど、別の型の等価のデータに 1 つのデータ型のデータを置き換えることができます。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールでデータの書式設定](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)です。|  
|セル、行、列、およびヘッダーの外観と動作を変更するための複数のオプション|<xref:System.Windows.Forms.DataGridView>コントロールでは、さまざまな方法でグリッドの個々 のコンポーネントを操作することができます。 たとえば、行と列をスクロールすることを防ぐことを固定できます。行、列、およびヘッダーを非表示にします。行、列、およびヘッダーのサイズが調整されている方法を変更します。項目を選択するようにする方法を変更します。個々 のセル、行、および列のツールヒントとショートカット メニューを提供します。|  
  
 <xref:System.Windows.Forms.DataGrid>旧バージョンと互換性のため、特別なニーズのコントロールは保持されます。 ほぼすべての目的で使用する必要があります、<xref:System.Windows.Forms.DataGridView>コントロール。 使用できる機能のみ、<xref:System.Windows.Forms.DataGrid>コントロールでは使用できませんを<xref:System.Windows.Forms.DataGridView>コントロールは、1 つのコントロールに関連する 2 つのテーブルからの情報の階層表示します。 2 つを使用する必要があります<xref:System.Windows.Forms.DataGridView>マスター/詳細リレーションシップ内にある 2 つのテーブルからの情報を表示するコントロール。  
  
## <a name="upgrading-to-the-datagridview-control"></a>DataGridView コントロールへのアップグレード  
 使用する既存のアプリケーションがある場合、<xref:System.Windows.Forms.DataGrid>コントロール シナリオでは、単純なデータ バインドのカスタマイズせず、置き換えることができます単に、古いコントロール、新しいコントロールです。 両方のコントロールは標準の Windows フォーム データ バインディング アーキテクチャを使用するため、<xref:System.Windows.Forms.DataGridView>コントロールが必要な追加の構成がないと、バインドされたデータを表示します。 データをバインドすることによって、データ バインディングの機能強化、ただしの利用を検討することができます、<xref:System.Windows.Forms.BindingSource>にバインドすることができますし、コンポーネント、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、次を参照してください。 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)です。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールが完全に新しいアーキテクチャは、使用できる単純変換パスはありません<xref:System.Windows.Forms.DataGrid>とカスタマイズ、<xref:System.Windows.Forms.DataGridView>コントロール。 多く<xref:System.Windows.Forms.DataGrid>のカスタマイズが必要とされない、<xref:System.Windows.Forms.DataGridView>制御、ただし、新しいコントロールで使用できる組み込みの機能が原因です。 カスタム列の型を作成した場合、<xref:System.Windows.Forms.DataGrid>で使用するコントロール、<xref:System.Windows.Forms.DataGridView>コントロール、もう一度新しいアーキテクチャを使用してそれらを実装する必要があります。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでのデータの書式設定](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロール内の列の並べ替えモード](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールの選択モード](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
