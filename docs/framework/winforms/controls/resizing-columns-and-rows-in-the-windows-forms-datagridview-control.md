---
title: Windows フォーム DataGridView コントロール内の列と行のサイズ変更
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 1e501d124ccec749537d319b992c5caf00b025f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536960"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロール内の列と行のサイズ変更
`DataGridView`コントロールには、その列と行のサイズ変更動作をカスタマイズするためのさまざまなオプションが用意されています。 通常、`DataGridView`セル サイズを変更しないでその内容を基にします。 代わりに、それらはクリップ表示値があるセルよりも大きいです。 コンテンツは、文字列として表示されることができます、セルにより、ツールヒントに表示します。  
  
 既定では、ユーザーは、行、列、および詳細情報を表示するには、マウスでのヘッダー区分線をドラッグできます。 ユーザーは、サイズが自動的にその内容に基づいて関連付けられている行、列、またはヘッダーのバンドの区分線をダブルクリックすることもできます。  
  
 `DataGridView`コントロールには、プロパティ、メソッド、およびカスタマイズしたり、これらすべてのユーザー向け動作を無効にするようにイベントが用意されています。 さらに、プログラムでサイズを変更する行、列、およびその内容に合わせてヘッダーまたはサイズが自動的に自身の内容が変更されるたびにそれらを構成できます。 指定した比率で、コントロールの使用可能な幅を自動的に分割する列を構成することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 サイズ変更行、列、およびヘッダーのオプションについて説明します。 また、サイズ変更に関連するプロパティやメソッドの詳細を提供し、一般的な使用シナリオについて説明します。  
  
 [Windows フォーム DataGridView コントロールの列フィル モード](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 列フィル モードの詳細、および列フィル モードおよびその他のモードを実験に使用できるデモ用のコードを説明します。  
  
 [方法: Windows フォーム DataGridView コントロールのサイズ変更モードを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 一般的な用途のサイズ変更モードを構成する方法について説明します。  
  
 [方法: Windows フォームの DataGridView コントロールの内容に合わせてセルのサイズをプログラムで変更する](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 プログラムによるサイズ変更をテストに使用できるデモ用のコードを提供します。  
  
 [方法: Windows フォームの DataGridView コントロールの内容変更時にセルのサイズを自動的に変更する](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 自動サイズ変更モードを実験に使用できるデモ用のコードを提供します。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。  
  
## <a name="see-also"></a>関連項目  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
