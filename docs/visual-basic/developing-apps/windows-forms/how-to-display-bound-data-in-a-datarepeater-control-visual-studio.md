---
title: "方法: DataRepeater コントロール (Visual Studio) にバインドされたデータを表示 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
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
ms.openlocfilehash: 9bf8f2f5fcc4dfa2b29e368a4e26bf112e08149e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>方法 : DataRepeater コントロールにバインドされたデータを表示する (Visual Studio)
最も一般的な用途、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールでは、データベースやその他のデータ ソースからバインドされたデータを表示します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
 バインドされたコントロールだけでなく静的ラベルなどの各アイテムに対して繰り返されるイメージの他のコントロールに追加することがあります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 詳細については、次を参照してください。[方法: DataRepeater コントロールにバインドされていないコントロールを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)します。  
  
 バインドすることできますもデータ ソースに実行時に設定して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティを`True`とするデータ ソースを割り当て、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>プロパティ</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>。 この場合は、データ ソースのすべての対話を管理する必要があります。 詳細については、次を参照してください。 [DataRepeater コントロールでの仮想モード](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)します。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>データ バインド DataRepeater を作成するには  
  
1.  ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールから、 **Visual Basic power Packs**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
2.  サイズにサイズと位置のハンドルをドラッグし、コントロールを配置します。  
  
     コントロールに&2; つの四角形の領域があることに注意してください。 上の領域は、*項目テンプレート*; 内の各項目で、テンプレートに追加されたコントロールが繰り返されます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>実行時にコントロールできます</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 下部の領域は、*ビューポート*項目が表示されます。  
  
     サイズし、変更することで、コントロールまたは項目テンプレートを配置できます、**サイズ**と**位置**のプロパティ ウィンドウでプロパティです。  
  
3.  **[データ]** メニューの **[データ ソースの表示]**をクリックします。  
  
    > [!NOTE]
    >  場合、**データソース**ウィンドウが空で、データ ソースを追加します。 詳細については、次を参照してください。[新しいデータ ソースを追加](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources)します。  
  
4.  **データソース** ウィンドウをバインドするデータを含むテーブルの最上位ノードを選択します。  
  
5.  テーブルのドロップ タイプを変更する`Details`をクリックして`Details`テーブル ノードのドロップダウン リストにします。  
  
6.  テーブル ノードを選択し、項目テンプレートの領域にドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
     コントロールの種類は各フィールドに表示を指定することができます。 詳細については、次を参照してください。[データ ソース ウィンドウからドラッグしたときに作成されるコントロールを設定](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [方法: DataRepeater コントロールでコントロールが画面にバインドされていません。](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [方法:&2; つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [方法: DataRepeater コントロールの外観を変更します。](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
