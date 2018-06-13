---
title: Windows フォームの Button コントロールを選択する方法
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 39696be1286efa68fa70b698ba9623911c90e352
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536329"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Windows フォームの Button コントロールを選択する方法
Windows フォームのボタンは、次のように選択できます。  
  
-   マウスを使用して、ボタンをクリックします。  
  
-   呼び出し、ボタンの<xref:System.Windows.Forms.Control.Click>コード内のイベントです。  
  
-   TAB キーを押して、ボタンにフォーカスを移動し、ボタンを選択し、space キーまたは ENTER キーを押して、します。  
  
-   ボタンの (ALT + 下線付き文字) のアクセス キーを押します。 アクセス キーの詳細については、次を参照してください。[する方法: Windows のフォーム コントロールへのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)です。  
  
-   ボタンがフォームの「承認」ボタンの場合は、ENTER キーを押してボタンを選択、他のコントロールにフォーカスがある場合でも、その他のコントロールが別のボタン、複数行テキスト ボックス、または enter キーをトラップするカスタム コントロールの場合を除きます。  
  
-   別のコントロールにフォーカスがある場合でも、esc キーを押して、ボタンがフォームの「キャンセル」ボタンの場合に、ボタンを選択します。  
  
-   呼び出す、<xref:System.Windows.Forms.Button.PerformClick%2A>メソッドをプログラムで、ボタンを選択します。  
  
## <a name="see-also"></a>関連項目  
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [方法: Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
