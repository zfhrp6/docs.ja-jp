---
title: ColorDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526039"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog コンポーネントの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.ColorDialog>コンポーネントは、ユーザーがパレットから色を選択し、そのパレットに色を追加できる構成済みのダイアログ ボックス。 このダイアログ ボックスは、他の Windows ベースのアプリケーションで表示される色を選択するためのダイアログ ボックスと同じです。 このコントロールは、独自のダイアログ ボックスを使用しない簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。  
  
 ダイアログ ボックスで選択された色が返される、<xref:System.Windows.Forms.ColorDialog.Color%2A>プロパティです。 場合、<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>プロパティに設定されている`false`、「色」ボタンが無効になり、ユーザーは、パレットで定義済みの色に制限します。 場合、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>プロパティに設定されている`true`ユーザーがディザリングされた色を選択できません。 ダイアログ ボックスを表示するには、呼び出す必要があります、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog コンポーネント](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [ダイアログ ボックス コントロールおよびコンポーネント](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [方法: Windows フォーム ColorDialog コンポーネントの表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
