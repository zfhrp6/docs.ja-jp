---
title: "How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, master/detail tables"
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つ以上の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを使用して、関連データを表示するマスター\/詳細形式のフォームを作成できます。  たとえば、1 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> に顧客の一覧を表示し、ユーザーが顧客を選択したときにその顧客の注文の一覧を 2 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> に表示する場合などです。  
  
 **\[データ ソース\]** ウィンドウから、同じマスター テーブル ノードを共有する詳細項目を <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールにドラッグして、関連データを表示できます。  たとえば、データ ソースに Customers テーブルとそれに関連する Orders テーブルがある場合、両方のテーブルがツリー ビューの最上位ノードとして **\[データ ソース\]** ウィンドウに表示されます。  Customers ノードを展開して列を表示します。  リストの最後の列は、Orders テーブルを表す展開可能なノードになっています。  このノードは、顧客に関連する注文を表します。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 2 つの DataRepeater コントロールで関連データを表示するには  
  
1.  **ツールボックス**の **\[Visual Basic PowerPacks\]** タブから 2 つの <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  サイズ変更ハンドルをドラッグして 2 つのコントロールのサイズを変更し、移動ハンドルをドラッグして 2 つのコントロールを並べて配置します。  
  
3.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
    > [!NOTE]
    >  **\[データ ソース\]** ウィンドウが空の場合は、そのウィンドウにデータ ソースを追加します。  詳細については、「[データ ソースの概要](/visual-studio/data-tools/add-new-data-sources)」を参照してください。  
  
4.  **\[データ ソース\]** ウィンドウで、マスター テーブルの最上位ノードを選択します。  
  
5.  テーブル ノードのドロップダウン リストの **\[詳細\]** をクリックして、マスター テーブルのドロップ タイプを \[詳細\] に変更します。  
  
6.  マスター テーブル ノードを 1 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域にドラッグします。  
  
7.  マスター テーブル ノードを展開し、関連テーブルの詳細ノードを選択します。  
  
8.  テーブル ノードのドロップダウン リストの **\[詳細\]** をクリックして、詳細テーブルのドロップ タイプを \[詳細\] に変更します。  
  
9. このテーブル ノードを選択し、2 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域にドラッグします。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [方法: 関連するデータを Windows フォーム アプリケーションに表示する](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)