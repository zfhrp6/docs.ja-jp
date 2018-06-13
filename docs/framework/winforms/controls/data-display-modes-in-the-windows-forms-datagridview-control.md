---
title: Windows フォーム DataGridView コントロールでのデータ表示モード
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: f97576218df651553ed1ac5f681d1ec0b4ab5ef3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528604"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでのデータ表示モード
<xref:System.Windows.Forms.DataGridView>コントロールは、次の 3 つの異なるモードでデータを表示することができます: バインド、バインドされていない、および仮想です。 要件に基づいて最も適したモードを選択します。  
  
## <a name="unbound"></a>バインドされていません。  
 バインドされていないモードでは、比較的少量のプログラムで管理しているデータの表示に適しています。 アタッチしない、<xref:System.Windows.Forms.DataGridView>バインド モードと同様に、データ ソースに直接制御します。 代わりに、する必要があります、コントロール、自分で通常使用して設定、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>メソッドです。  
  
 バインドされていないモードは、データは、静的な読み取り専用、または外部データ ストアを操作するコードを提供する場合に特に便利ですがあります。 外部データ ソースとの対話をユーザーにする場合は、ただしは通常モードを使用するバインド。  
  
 読み取り専用に使用する例については、バインドされていない<xref:System.Windows.Forms.DataGridView>を参照してください[する方法: バインドされていない Windows フォームの DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)です。  
  
## <a name="bound"></a>バインド  
 バインド モードは、データ ストアと自動操作を使用してデータの管理に適しています。 アタッチすることができます、<xref:System.Windows.Forms.DataGridView>コントロールを設定してそのデータ ソースを直接、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティです。 コントロールがバインドされたデータの場合は、データ行がプッシュされ、プル、部品で明示的に管理の必要はありません。 ときに、<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>プロパティは`true`、データ ソース内の各列は、コントロールの作成に対応する列になります。 独自の列を作成する場合は、このプロパティを設定することができます`false`を使用して、<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>プロパティを構成するときに、各列をバインドします。 これは、既定で生成される型以外の列の型を使用する場合に便利です。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)です。  
  
 バインドを使用する例について<xref:System.Windows.Forms.DataGridView>を制御しを参照してください[チュートリアル: Windows フォーム DataGridView コントロール内のデータの検証](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)です。  
  
 バインドされていない列を追加することも、<xref:System.Windows.Forms.DataGridView>バインド モードで制御します。 これは、特定の行に対してアクションを実行するユーザーを有効にするボタンやリンクの列を表示するときに便利です。 バインドされた列から計算された値を持つ列を表示すると便利です。 ハンドラーで計算列のセル値を設定することができます、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント。 使用している場合、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>データ ソースとしてただしが使用する、<xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>代わりに、計算列を作成するプロパティです。 ここで、<xref:System.Windows.Forms.DataGridView>コントロールは、データ ソースの他の任意の列と同じように計算列を処理します。  
  
 バインド モードで非バインド列による並べ替えはサポートされていません。 ユーザーが編集できる値を含むバインド モードで非バインド列を作成する場合は、コントロールがバインドされた列で並べ替えられたときに、これらの値を維持するために仮想モードを実装する必要があります。  
  
## <a name="virtual"></a>仮想  
 仮想モードでは、独自のデータ管理操作を実装できます。 これは、コントロールがバインドされた列で並べ替えられたバインド モードで非バインド列の値を維持するために必要です。 仮想モードの主な用途は、ただし、大量のデータを扱うときにパフォーマンスを最適化するためには。  
  
 アタッチする、<xref:System.Windows.Forms.DataGridView>を管理するキャッシュ制御とデータ行のプッシュし、プルしたときに、コードを制御します。 メモリ使用量を少なく抑え、キャッシュを現在表示されている行の数にほぼ同じサイズにする必要があります。 ユーザーは、ビューに新しい行をスクロールするときに、コードはキャッシュから新しいデータを要求し、必要に応じてメモリから古いデータをフラッシュします。  
  
 仮想モードを実装しているときに、新しい行が必要なときにデータ モデルでは、新しい行の追加をロールバックするときに追跡する必要があります。 この機能の正確な実装は、データ モデルのトランザクション セマンティクスとデータ モデルの実装に依存します。かどうかコミット スコープは、セルまたは行レベルでです。  
  
 仮想モードの詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)です。 仮想モードのイベントを使用する方法を示す例を次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>  
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [チュートリアル: バインドされていない Windows フォーム DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [方法: データを Windows フォーム DataGridView コントロールにバインドする](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)
