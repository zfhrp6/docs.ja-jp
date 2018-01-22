---
title: "方法 : デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする"
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
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa78d8afe59a147a37b1c827e8c755bf74e95633
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法 : デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする
ユーザーが既定では、テキストと Windows フォームに表示される数値のデータ変更できる<xref:System.Windows.Forms.DataGridView>コントロール。 変更できないデータを表示する場合は、読み取り専用のデータを含む列を行う必要があります。 完全に読み取り専用のコントロールを作成する方法については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールを使用して、デザイナーで防ぐ行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)です。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a>デザイナーを使用して、列を読み取り専用にする  
  
1.  スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>を制御し、**列の編集**です。  
  
2.  列を選択して、**選択されている列** ボックスの一覧です。  
  
3.  **列プロパティ**グリッドで、設定、<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A>プロパティを`true`です。  
  
    > [!NOTE]
    >  作成することも、列読み取り専用 を選択して追加すると、**読み取り専用** チェック ボックス、**列の追加** ダイアログ ボックス。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [方法: デザイナーを使用して Windows フォーム DataGridView コントロールで行が追加および削除されないようにする](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 [方法: Windows アプリケーション プロジェクトの作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [方法: Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
