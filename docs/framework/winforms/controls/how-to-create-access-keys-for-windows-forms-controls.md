---
title: '方法 : Windows フォーム コントロールのアクセス キーを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 53ffd3632ff3e1179a72f1e2bfe4ea366e28b0f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530950"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>方法 : Windows フォーム コントロールのアクセス キーを作成する
*アクセス キー*メニューのメニュー項目、または、ボタンなどのコントロールのラベルのテキストに下線付きの文字がします。 アクセス キーのあるユーザーできます「ボタンをクリック」を定義済みのアクセス キーを持つ組み合わせて ALT キーを押してします。 たとえば、フォームを印刷する手順を実行するボタンおよびその`Text`プロパティは、文字"P"により、文字"P"するには実行時に、ボタンのテキストに下線を付ける前にアンパサンドを追加する"Print"に設定します。 ユーザーは、ALT キーを押しながら P キーを押して、ボタンに関連付けられているコマンドを実行できます。 フォーカスを受け取ることができないコントロールのアクセス キーを持つことはできません。  
  
### <a name="to-create-an-access-key-for-a-control"></a>コントロールのアクセス キーを作成するには  
  
1.  設定、`Text`ショートカットとなる文字の前にアンパサンドを含む文字列 (&) のプロパティです。  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  アンパサンド キャプションでアクセス キーを作成することがなく、その 2 つのアンパサンド (& &)。 単一のアンパサンドがキャプションに表示され、文字に下線を付けるありません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Button>  
 [方法: Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [方法: Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
