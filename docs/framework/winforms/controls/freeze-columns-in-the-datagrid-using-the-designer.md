---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 049dd4952dc8af2c0f56567d8f2f53f5be5928ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する
ユーザーが Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールに表示されるデータを確認するときに、1 つの列または列のセットを頻繁に参照しなければならないことがあります。 たとえば、多数の列を含む顧客情報のテーブルを表示するとき、表示領域外にスクロールするには、他の列の有効化中に常に、顧客名を表示するため便利です。  
  
 この動作を実現するために、コントロールの列を固定することができます。 列を固定すると、左側 (右から左へ記述する言語のスクリプトでは右側) のすべての列も同様に固定されます。 固定された列は表示されたままになり、その他のすべての列はスクロールできます。 列の並べ替えが有効な場合、固定された列は、固定されていない列とは異なるグループとして扱われます。 ユーザーは、どちらかのグループに列を再配置できますが、1 つのグループから別のグループに列を移動することはできません。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-freeze-a-column-using-the-designer"></a>デザイナーを使用して列を固定するには  
  
1.  スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>を制御し、**列の編集**です。  
  
2.  列を選択して、**選択されている列** ボックスの一覧です。  
  
3.  **列プロパティ**グリッドで、設定、<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A>プロパティを`true`です。  
  
    > [!NOTE]
    >  選択して追加する際、列を固定することも、 **Frozen**ボックスに、**列の追加** ダイアログ ボックス。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の並べ替えを有効にする](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [方法: グローバリゼーション用の Windows フォームで右から左へテキストを表示](http://msdn.microsoft.com/en-us/f0663385-2354-4c65-8676-706422283b14)  
 [方法: Windows アプリケーション プロジェクトの作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [方法: Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
