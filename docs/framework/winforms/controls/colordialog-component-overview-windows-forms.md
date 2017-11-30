---
title: "ColorDialog コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f3a25c601e46c18a30755a15131bba03669a2ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog コンポーネントの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.ColorDialog>コンポーネントは、ユーザーがパレットから色を選択し、そのパレットに色を追加できる構成済みのダイアログ ボックス。 このダイアログ ボックスは、他の Windows ベースのアプリケーションで表示される色を選択するためのダイアログ ボックスと同じです。 このコントロールは、独自のダイアログ ボックスを使用しない簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。  
  
 ダイアログ ボックスで選択された色が返される、<xref:System.Windows.Forms.ColorDialog.Color%2A>プロパティです。 場合、<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>プロパティに設定されている`false`、「色」ボタンが無効になり、ユーザーは、パレットで定義済みの色に制限します。 場合、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>プロパティに設定されている`true`ユーザーがディザリングされた色を選択できません。 ダイアログ ボックスを表示するには、呼び出す必要があります、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog コンポーネント](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [ダイアログ ボックス コントロールおよびコンポーネント](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [方法: Windows フォーム ColorDialog コンポーネントの表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
