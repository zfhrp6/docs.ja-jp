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
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="c1b7e-102">方法 : Windows フォーム コントロールのアクセス キーを作成する</span><span class="sxs-lookup"><span data-stu-id="c1b7e-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="c1b7e-103">*アクセス キー*メニューのメニュー項目、または、ボタンなどのコントロールのラベルのテキストに下線付きの文字がします。</span><span class="sxs-lookup"><span data-stu-id="c1b7e-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="c1b7e-104">アクセス キーのあるユーザーできます「ボタンをクリック」を定義済みのアクセス キーを持つ組み合わせて ALT キーを押してします。</span><span class="sxs-lookup"><span data-stu-id="c1b7e-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="c1b7e-105">たとえば、フォームを印刷する手順を実行するボタンおよびその`Text`プロパティは、文字"P"により、文字"P"するには実行時に、ボタンのテキストに下線を付ける前にアンパサンドを追加する"Print"に設定します。</span><span class="sxs-lookup"><span data-stu-id="c1b7e-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="c1b7e-106">ユーザーは、ALT キーを押しながら P キーを押して、ボタンに関連付けられているコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c1b7e-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="c1b7e-107">フォーカスを受け取ることができないコントロールのアクセス キーを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="c1b7e-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="c1b7e-108">コントロールのアクセス キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="c1b7e-108">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="c1b7e-109">設定、`Text`ショートカットとなる文字の前にアンパサンドを含む文字列 (&) のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="c1b7e-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
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
    >  <span data-ttu-id="c1b7e-110">アンパサンド キャプションでアクセス キーを作成することがなく、その 2 つのアンパサンド (& &)。</span><span class="sxs-lookup"><span data-stu-id="c1b7e-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="c1b7e-111">単一のアンパサンドがキャプションに表示され、文字に下線を付けるありません。</span><span class="sxs-lookup"><span data-stu-id="c1b7e-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b7e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1b7e-112">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="c1b7e-113">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="c1b7e-113">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="c1b7e-114">方法: Windows フォーム コントロールによって表示されるテキストを設定する</span><span class="sxs-lookup"><span data-stu-id="c1b7e-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="c1b7e-115">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="c1b7e-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
