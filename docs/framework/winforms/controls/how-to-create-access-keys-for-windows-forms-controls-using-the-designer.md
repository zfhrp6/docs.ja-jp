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
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="268b0-102">方法 : デザイナーを使用して Windows フォーム コントロールのアクセス キーを作成する</span><span class="sxs-lookup"><span data-stu-id="268b0-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="268b0-103">*アクセス キー*メニューのメニュー項目、または、ボタンなどのコントロールのラベルのテキストに下線付きの文字がします。</span><span class="sxs-lookup"><span data-stu-id="268b0-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="268b0-104">"ボタンをクリック"、キーを押すと、ALT の組み合わせで定義済みのアクセス キーを持つユーザーができるようにします。</span><span class="sxs-lookup"><span data-stu-id="268b0-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="268b0-105">たとえば、フォームを印刷する手順を実行するボタンおよびその`Text`"P"と、文字に下線を付けるには、"P"、ボタンのテキストの実行時に文字の前に「印刷」アンパサンドを追加する (&)、プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="268b0-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="268b0-106">ユーザーは、ALT キーを押しながら P キーを押して、ボタンに関連付けられているコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="268b0-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="268b0-107">フォーカスを受け取ることができないコントロールのアクセス キーを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="268b0-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="268b0-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="268b0-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="268b0-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="268b0-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="268b0-110">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="268b0-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="268b0-111">コントロールのアクセス キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="268b0-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="268b0-112">**プロパティ**ウィンドウで、設定、`Text`プロパティ アクセス キーとなる文字の前にアンパサンドを含む文字列 (&)。</span><span class="sxs-lookup"><span data-stu-id="268b0-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="268b0-113">たとえば、アクセス キーとして文字"P"を設定するに次のように入力します。**印刷 &**グリッドにします。</span><span class="sxs-lookup"><span data-stu-id="268b0-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268b0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="268b0-114">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="268b0-115">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="268b0-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="268b0-116">方法: Windows フォーム コントロールによって表示されるテキストを設定する</span><span class="sxs-lookup"><span data-stu-id="268b0-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="268b0-117">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="268b0-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
