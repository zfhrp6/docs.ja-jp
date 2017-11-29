---
title: "方法 : デザイナーを使用して Windows フォーム コントロールのアクセス キーを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19c47c21526ca6e7aa4046a1853f3d1743438d17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>方法 : デザイナーを使用して Windows フォーム コントロールのアクセス キーを作成する
*アクセス キー*メニューのメニュー項目、または、ボタンなどのコントロールのラベルのテキストに下線付きの文字がします。 "ボタンをクリック"、キーを押すと、ALT の組み合わせで定義済みのアクセス キーを持つユーザーができるようにします。 たとえば、フォームを印刷する手順を実行するボタンおよびその`Text`"P"と、文字に下線を付けるには、"P"、ボタンのテキストの実行時に文字の前に「印刷」アンパサンドを追加する (&)、プロパティを設定します。 ユーザーは、ALT キーを押しながら P キーを押して、ボタンに関連付けられているコマンドを実行できます。 フォーカスを受け取ることができないコントロールのアクセス キーを持つことはできません。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-an-access-key-for-a-control"></a>コントロールのアクセス キーを作成するには  
  
1.  **プロパティ**ウィンドウで、設定、`Text`プロパティ アクセス キーとなる文字の前にアンパサンドを含む文字列 (&)。 たとえば、アクセス キーとして文字"P"を設定するに次のように入力します。**印刷 &**グリッドにします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Button>  
 [方法: Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [方法: Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
