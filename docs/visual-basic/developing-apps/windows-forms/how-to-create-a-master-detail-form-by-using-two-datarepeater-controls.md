---
title: "方法:&2; つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 23789bb11cab17b50928651e1dc00d5d59640c0f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>方法 :&2; つの DataRepeater コントロールを使用してマスター/詳細形式のフォームを作成する (Visual Studio)
2 つ以上を使用して関連データを表示できる<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>マスター/詳細フォームを作成するコントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 いずれかで顧客の一覧を表示するなど、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>、ユーザーは、顧客を選択するときに、1 秒あたり<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>その顧客の注文の一覧を表示および</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 共有から同じマスター テーブル ノードの詳細項目をドラッグして関連データを表示できる、**データ ソース**ウィンドウ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 たとえば、Customers テーブルと関連する Orders テーブルを持つデータ ソースがあれば、両方のテーブルとして表示ツリー ビューで、最上位ノード、**データソース**ウィンドウです。 列が表示されるように、Customers ノードを展開します。 一覧の最後の列は、Orders テーブルを表す展開可能なノードであることを確認します。 このノードは、顧客に関連する注文を表します。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>2 つの DataRepeater コントロールに関連するデータを表示するには  
  
1.  2 つをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを**Visual Basic power Packs**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
2.  コントロールをサイズ変更、サイド バイ サイドの配置へのサイズおよび位置のハンドルをドラッグします。  
  
3.  **[データ]** メニューの **[データ ソースの表示]**をクリックします。  
  
    > [!NOTE]
    >  場合、**データソース**ウィンドウが空で、データ ソースを追加します。 詳細については、次を参照してください。[新しいデータ ソースを追加](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources)します。  
  
4.  **データソース**ウィンドウで、マスター テーブルの最上位ノードを選択します。  
  
5.  クリックして、マスター テーブルのドロップ タイプの詳細に変更**詳細**テーブル ノードのドロップダウン リストにします。  
  
6.  最初の項目テンプレートの領域上にマスター テーブル ノードをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
7.  マスター テーブル ノードを展開し、関連するテーブルの詳細のノードを選択します。  
  
8.  クリックして、[詳細] テーブルのドロップ タイプの詳細に変更**詳細**テーブル ノードのドロップダウン リストにします。  
  
9. このテーブルのノードを選択し、2 番目の項目テンプレートの領域にドラッグ<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [方法: DataRepeater コントロールにバインドされたデータの表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [方法: 関連するデータを Windows フォーム アプリケーションの表示します。](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)   
 [方法: DataRepeater コントロールの外観を変更します。](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
