---
title: DataGridView コントロール テクノロジの概要 (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: cafd832e7105540ae684dd1feb4b33ab74f72836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528874"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView コントロール テクノロジの概要 (Windows フォーム)
ここでは、`DataGridView` コントロールおよびその使用をサポートしているクラスの概要について説明します。  
  
 表形式でデータの表示は、頻繁に実行することの多いタスクです。 `DataGridView`コントロールがグリッドにデータを表すための完全なソリューションに設計されています。  
  
## <a name="keywords"></a>キーワード  
 DataGridView、BindingSource、テーブル、セル、データ バインディング、仮想モード  
  
## <a name="namespaces"></a>名前空間  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>関連技術  
 `BindingSource`  
  
## <a name="background"></a>背景  
 ユーザー インターフェイス (UI) のデザイナー頻繁に必要なユーザーに表形式のデータを表示します。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]テーブルまたはグリッドにデータを表示するいくつかの方法を提供します。 `DataGridView`コントロールは、Windows フォーム アプリケーションでは、このテクノロジの最新の進化を表します。  
  
 `DataGridView`コントロールは行のデータ ストアからデータを表示できます。 多くの種類のデータ ストアがサポートされています。 データ ストアが 1 次元の配列などのシンプルで型指定されていないデータを保持できるかなど、型指定されたデータを保持できます、<xref:System.Data.DataSet>です。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールにデータをバインド](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)です。  
  
 `DataGridView` コントロールには、データを表形式で表示するための強力で柔軟な機能が用意されています。 小さすぎるため非常に大きなデータ セットの読み取り専用または編集可能なビューを表示するのにコントロールを使用することができます。  
  
 拡張することができます、`DataGridView`をアプリケーションにカスタム動作を構築するいくつかの方法で制御します。 たとえば、プログラムで独自の並べ替えアルゴリズムを指定したり、独自の種類のセルを作成したりできます。 `DataGridView` コントロールの外観は、いくつかのプロパティを選択することで簡単にカスタマイズできます。 多くの種類のデータ ストアは、データ ソースとして使用できますか、`DataGridView`コントロールがデータ ソースをバインドなくても動作できます。  
  
## <a name="implementing-datagridview-classes"></a>DataGridView のクラスの実装  
 いくつかの方法を活用するための`DataGridView`コントロールの拡張機能です。 イベントとプロパティを使用してコントロールの多くの側面をカスタマイズすることができますが、一部のカスタマイズでは、既存のファイルから派生した新しいクラスを作成する必要があります`DataGridView`クラスです。  
  
 一般的に使用される基本クラスは、`DataGridViewCell`と`DataGridViewColumn`です。 独自のセル クラスを派生できます`DataGridViewCell`またはその子クラスのいずれか。 任意の列に任意のセルの種類を追加できますが、するは通常もコンパニオン列からクラスを派生`DataGridViewColumn`既定では、カスタムのセルの種類のセルをホストします。  
  
 実装することができます、`IDataGridViewEditingCell`編集機能が編集モードでのコントロールをホストしていないセルの種類を作成する、派生セル クラスのインターフェイスです。 編集モードのセルでホストできるコントロールを作成することができますを実装する、`IDataGridViewEditingControl`から派生したクラスでインターフェイス<xref:System.Windows.Forms.Control>です。  
  
 詳細については、次を参照してください[する方法: セルのカスタマイズおよびその動作を拡張すると外観が Windows フォーム DataGridView コントロールで列](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)と[する方法: Windows フォーム DataGridView セルでホストコントロール](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## <a name="datagridview-classes-at-a-glance"></a>DataGridView のクラスの概要  
 <xref:System.Windows.Forms>  
  
|テクノロジ領域|クラス/インターフェイス/構成要素|  
|---------------------|-------------------------------------------------|  
|データ バインディング|<xref:System.Windows.Forms.BindingSource>|  
|データの表示|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> 機能拡張|<xref:System.Windows.Forms.DataGridViewCell> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>新機能  
 <xref:System.Windows.Forms.DataGridView>コントロールが Windows フォームで表形式のデータを表示するための完全なソリューションに設計されています。 使用を検討する必要があります、<xref:System.Windows.Forms.DataGridView>など、他のソリューションの前に制御<xref:System.Windows.Forms.DataGrid>新しいアプリケーションを作成する際、します。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールを閉じると組み合わせて、<xref:System.Windows.Forms.BindingSource>コンポーネントです。 このコンポーネントは、フォームのプライマリ データ ソースに設計されています。 間の相互作用を管理できる、<xref:System.Windows.Forms.DataGridView>コントロールとデータに関係なく、データ ソースのソースの種類。  
  
## <a name="see-also"></a>関連項目  
 [DataGridView コントロールの概要](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [DataGridView コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)
