---
title: '方法: 2 つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>方法 : 2 つの DataRepeater コントロールを使用してマスター/詳細形式のフォームを作成する (Visual Studio)
関連するデータを表示するには 2 つ以上を使用して<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>マスター/詳細フォームを作成するコントロール。 いずれかで顧客の一覧を表示するなど、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>、ユーザーは、顧客を選択するときに、1 秒あたりその顧客の注文の一覧を表示および<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>です。  
  
 関連するデータを表示するには、同じマスター テーブルのノードから共有詳細項目をドラッグして、**データ ソース** ウィンドウ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 たとえば、Customers テーブルと関連する Orders テーブルを持つデータ ソースがあれば、両方のテーブルとして表示ツリー ビューで、最上位のノード、**データソース**ウィンドウです。 列を認識できるように、Customers ノードを展開します。 一覧の最後の列は、Orders テーブルを表す展開可能なノードであることを確認します。 このノードは、顧客に関連する注文を表します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>2 つの DataRepeater コントロールに関連するデータを表示するには  
  
1.  2 つをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。  
  
2.  コントロールをサイズ変更、サイド バイ サイド配置へのサイズと位置のハンドルをドラッグします。  
  
3.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
    > [!NOTE]
    >  場合、**データソース**ウィンドウが空の場合に、データ ソースを追加します。 詳細については、「[新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)」を参照してください。  
  
4.  **データソース**ウィンドウで、マスター テーブルの最上位ノードを選択します。  
  
5.  クリックして、マスター テーブルのドロップ タイプの詳細に変更**詳細**テーブル ノードのドロップダウン リストでします。  
  
6.  最初の項目テンプレート領域上にマスター テーブル ノードをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
7.  マスター テーブル ノードを展開し、関連するテーブルの詳細ノードを選択します。  
  
8.  クリックして、[詳細] テーブルのドロップ タイプの詳細に変更**詳細**テーブル ノードのドロップダウン リストでします。  
  
9. このテーブル ノードを選択し、2 番目の項目テンプレート領域にドラッグ<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに、バインドされたデータを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [方法: 関連するデータを Windows フォーム アプリケーションに表示する](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
