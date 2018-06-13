---
title: Button コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 88255882d3255eff112b9048a906182b64d75084
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526023"
---
# <a name="button-control-overview-windows-forms"></a>Button コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.Button> コントロールを使用すると、ユーザーはそれをクリックしてアクションを実行できます。 ボタンをクリックすると、ボタンを実際に押して離したかのように表示されます。 ユーザーがクリックされるたびに、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーが呼び出されます。 内のコードを配置する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーを選択したアクションを実行します。  
  
 ボタンに表示されるテキストが含まれている、<xref:System.Windows.Forms.Control.Text%2A>プロパティです。 テキストは、ボタンの幅を超えている場合は、次の行に折り返されます。 ただし、コントロールが全体の高さに対応できない場合、クリップされます。 詳細については、次を参照してください。[する方法: Windows フォーム コントロールによって表示されるテキストを設定](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)です。 <xref:System.Windows.Forms.Control.Text%2A>プロパティは、これにより、ユーザーはアクセス キー、ALT キーを押すとコントロールを「クリックして」をアクセス キーを含めることができます。 詳細については、「[する方法: Windows のフォーム コントロールへのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)です。 によって、テキストの外観を制御、<xref:System.Windows.Forms.Control.Font%2A>プロパティおよび<xref:System.Windows.Forms.ButtonBase.TextAlign%2A>プロパティです。  
  
 <xref:System.Windows.Forms.Button>コントロールできますを使用してイメージを表示しても、<xref:System.Windows.Forms.ButtonBase.Image%2A>と<xref:System.Windows.Forms.ButtonBase.ImageList%2A>プロパティです。 詳細については、次を参照してください。[する方法: Windows フォーム コントロールによってイメージの表示設定](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Button>  
 [方法: Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [方法: デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [方法: デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
