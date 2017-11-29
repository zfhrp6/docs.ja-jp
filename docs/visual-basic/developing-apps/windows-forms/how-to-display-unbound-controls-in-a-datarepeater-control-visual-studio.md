---
title: "方法 : DataRepeater コントロールに非バインド コントロールを表示する (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>方法 : DataRepeater コントロールに非バインド コントロールを表示する (Visual Studio)
だけでなく、バインドされたコントロールを他のコントロールを追加することがあります、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>、静的ラベル内の各項目に繰り返し表示されるイメージなど、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
> [!NOTE]
>  少なくとも 1 つのバインドされたコントロールも必要、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>または実行時に何が表示されます。  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>DataRepeater にバインドされていないコントロールを追加するには  
  
1.  ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。  
  
2.  サイズにサイズ変更および位置のハンドルをドラッグし、コントロールを配置します。  
  
     またサイズし、変更することで、コントロールを配置、**サイズ**と**位置**プロパティ ウィンドウでプロパティです。  
  
3.  少なくとも 1 つのデータ バインド コントロールを追加、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 詳細については、次を参照してください。[する方法: DataRepeater コントロールにバインドされているデータを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)です。  
  
4.  コントロールをドラッグ、**ツールボックス**、項目テンプレート領域の上に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
     コントロールに 2 つの四角形の領域があることに注意してください。 内部の領域は、*項目テンプレート*; 内の各項目のテンプレートに追加されたコントロールは繰り返されます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>実行時にコントロールできます。 外部の領域は、*ビューポート*、ここで、アイテムを表示する以外の場合はこの領域に追加されるコントロールは、実行時に表示されません。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに、バインドされたデータを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [方法: 2 つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成します。](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
