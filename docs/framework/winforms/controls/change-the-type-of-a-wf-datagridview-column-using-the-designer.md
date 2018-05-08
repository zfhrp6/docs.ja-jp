---
title: '方法 : デザイナーを使用して Windows フォーム DataGridView 列の種類を変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: b5d395575ac486307625fbdf2f236b6a588cc3ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>方法 : デザイナーを使用して Windows フォーム DataGridView 列の種類を変更する
Windows フォームには既に追加されている列の種類を変更することがありますする<xref:System.Windows.Forms.DataGridView>コントロール。 たとえば、一部のデータ ソースにコントロールをバインドするときに自動的に生成される列の種類を変更する可能性があります。 これは、関連テーブル内の行を外部キーを含む列を表示するテーブルがある場合に便利です。 この場合、関連テーブルから意味のある値を表示するコンボ ボックスの列と、これらの外部キーを表示するテキスト ボックスの列を置換することがあります。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a>デザイナーを使用して列の型を変更するには  
  
1.  スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>を制御し、**列の編集**です。  
  
2.  列を選択して、**選択されている列** ボックスの一覧です。  
  
3.  **列プロパティ**グリッドで、設定、`ColumnType`プロパティを新しい列の型。  
  
    > [!NOTE]
    >  `ColumnType`プロパティは、デザイン時のみを示すプロパティを列のデータ型を表すクラス。 Column クラスで定義されている実際のプロパティではありません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [方法: Windows アプリケーション プロジェクトの作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [方法: Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
