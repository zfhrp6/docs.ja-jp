---
title: DataRepeater コントロールの仮想モード (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- virtual data binding [Visual Basic]
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
ms.openlocfilehash: 7aa462f670c95f2d5996cf04b676bf09e9ec62b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592237"
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>DataRepeater コントロールの仮想モード (Visual Studio)
大量の表形式データを表示する場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを設定してパフォーマンスを向上させることができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティを`True`と明示的にそのデータ ソース コントロールの相互作用を管理します。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、データ ソースと対話し、実行時に、必要に応じてデータの表示を処理できるいくつかのイベントを提供します。  
  
## <a name="how-virtual-mode-works"></a>仮想モードの動作  
 最も一般的なシナリオ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、の子コントロールをバインドする、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>データにでき、デザイン時にソース、<xref:System.Windows.Forms.BindingSource>に応じて前後にデータを渡すことです。 仮想モードを使用するときに、コントロールがデータ ソースにバインドされていない、データ渡されます前後、基になるデータ ソースに実行時。  
  
 ときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティに設定されている`True`からコントロールを追加して、ユーザー インターフェイスを作成する、**ツールボックス**からバインド コントロールを追加する代わりに、**データソース**ウィンドウです。  
  
 イベントは、コントロールごとに発生して、データの表示を処理するコードを追加する必要があります。 新しい<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>スクロール、表示、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>イベントはコントロールごとに 1 回発生し、内の各コントロールの値を指定する必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>イベント ハンドラー。  
  
 ユーザーがコントロールのいずれかでデータが変更された場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>イベントが発生し、データを検証し、データ ソースに保存する必要があります。  
  
 ユーザーは新しい項目を追加する場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>イベントが発生します。 このイベントのハンドラーを使用して、データ ソースに新しいレコードを作成します。 予期しない変更を防ぐためには、監視する必要も、<xref:System.Windows.Forms.Control.KeyDown>コントロールおよび呼び出しごとにイベント<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>ユーザーが ESC キーを押した場合。  
  
 場合は、データ ソースが変更を更新できます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを呼び出して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>と<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>メソッドです。 順序では、両方のメソッドを呼び出す必要があります。  
  
 最後に、イベント ハンドラーを実装する必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>用、および必要に応じて項目が削除されたときに発生するイベント、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems>と<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>イベントで、ユーザーは、DELETE キーを押して、項目が削除されるたびに発生します。  
  
## <a name="implementing-virtual-mode"></a>仮想モードの実装  
 仮想モードを実装するために必要な手順を次に示します。  
  
#### <a name="to-implement-virtual-mode"></a>仮想モードを実装するには  
  
1.  ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> プロパティを `True` に設定します。  
  
2.  コントロールをドラッグ、**ツールボックス**の項目テンプレート領域 (上部領域) に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 表示するデータ ソースのフィールドごとに 1 つのコントロールを必要があります。  
  
3.  ハンドラーを実装、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>イベントの各コントロールの値を指定します。 このイベントは、新しい<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>スクロール表示します。 コードの次の例では、という名前のデータ ソースのようになります`Employees`です。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  ハンドラーを実装、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>データを格納するイベントです。 このイベントは、ユーザーの子コントロールに変更をコミットするときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>です。 コードの次の例では、という名前のデータ ソースのようになります`Employees`です。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  各子コントロールのハンドラーを実装して<xref:System.Windows.Forms.Control.KeyDown>イベントとモニター、ESC キー。 呼び出す、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>しないようにする方法、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>イベントの発生します。 コードは次の例のようになります。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  ハンドラーを実装、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>イベント。 このイベントは、ユーザーに新しい項目を追加するときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 コードの次の例では、という名前のデータ ソースのようになります`Employees`です。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  ハンドラーを実装、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>イベント。 このイベントは、ユーザーが既存の項目を削除するときに発生します。 コードの次の例では、という名前のデータ ソースのようになります`Employees`です。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  ハンドラーを必要に応じてコントロール レベルの検証の実装、<xref:System.Windows.Forms.Control.Validating>子コントロールのイベントです。 コードは次の例のようになります。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
