---
title: '方法 : 定型入力を設定する'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 6f554c239e3444db5f6ac84f7994108ac70df0a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537042"
---
# <a name="how-to-set-the-input-mask"></a>方法 : 定型入力を設定する
マスクされたテキスト ボックス コントロールは、承認または拒否するユーザー入力の宣言の構文をサポートする高度なテキスト ボックス コントロールです。 マスクのプロパティの設定によって、アプリケーションで任意のカスタム検証ロジックを記述することがなく、許容されるユーザー入力を指定できます。 詳細については、の「解説」セクションを参照してください、<xref:System.Windows.Forms.MaskedTextBox>クラスです。  
  
## <a name="setting-the-mask-property-manually"></a>手動で、マスクのプロパティを設定  
 Mask プロパティをサポートする文字に精通場合は、手動で入力することができます。 概要については、マスクのプロパティをサポートする文字のの「解説」セクションを参照してください、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティです。  
  
#### <a name="to-set-the-mask-property-manually"></a>手動で、マスクのプロパティを設定するには  
  
1.  **デザイン**ビューで、<xref:System.Windows.Forms.MaskedTextBox>です。  
  
2.  **プロパティ**ウィンドウで、検索、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティです。  
  
3.  設定するマスクを入力します。 たとえば、「`###`です。  
  
## <a name="using-the-input-mask-dialog-box"></a>[定型入力] ダイアログ ボックスを使用します。  
 [定型入力] ダイアログ ボックスでは、いくつかの定義済みの入力マスクを提供します。 定義済みのマスクを変更したり、独自のマスクを手動で入力できます。  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>[定型入力] ダイアログ ボックスを開く  
  
1.  **デザイン**ビューで、<xref:System.Windows.Forms.MaskedTextBox>です。  
  
    1.  開くには、スマート タグをクリックして、 **MaskedTextBox タスク**パネルです。  
  
    2.  をクリックして**マスクを設定する**です。  
  
     \- または -  
  
    1.  **プロパティ**ウィンドウで、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティです。  
  
    2.  プロパティ値 列にある省略記号ボタンをクリックします。  
  
     **定型入力** ダイアログ ボックスが表示されます。  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>[定型入力] ダイアログ ボックスを使用するには  
  
1.  (省略可能)一覧で定義済みのマスクのいずれかをクリックします。  
  
2.  (省略可能)定義済みのマスクを編集、**マスク**ボックス。  
  
3.  (省略可能)新しいマスクを入力、**マスク**ボックス。 定義済みのマスクのいずれかを使用する必要はありません。  
  
    > [!NOTE]
    >  [プレビュー] ボックスでユーザーに表示される文字が表示されます、<xref:System.Windows.Forms.MaskedTextBox>です。 これらの文字に役立つガイドをユーザーがデータを正しく入力します。  
  
4.  オンまたはオフにして、**使用 ValidatingType**チェック ボックスをオンします。 **使用 ValidatingType**  チェック ボックスは、データ型は、ユーザーがデータ入力の検証に使用するかどうかを指定します。 詳細については、<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> プロパティを参照してください。  
  
5.  **[OK]** をクリックします。  
  
     マスクは、入力、**マスク**プロパティに、**プロパティ**ウィンドウです。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: MaskedTextBox コントロールの使用](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
