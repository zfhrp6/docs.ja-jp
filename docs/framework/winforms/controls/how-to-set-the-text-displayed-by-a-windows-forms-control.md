---
title: "方法 : Windows フォーム コントロールによって表示されるテキストを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a81c2202400968b4d4c95b40de7476fbd68d6182
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="57d13-102">方法 : Windows フォーム コントロールによって表示されるテキストを設定する</span><span class="sxs-lookup"><span data-stu-id="57d13-102">How to: Set the Text Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="57d13-103">Windows フォーム コントロールは、通常、コントロールの主な機能に関連するいくつかのテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="57d13-103">Windows Forms controls usually display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="57d13-104">たとえば、<xref:System.Windows.Forms.Button> コントロールは、通常、ボタンがクリックされたときにどのようなアクションを実行するかを示すキャプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="57d13-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed when the button is clicked.</span></span> <span data-ttu-id="57d13-105">すべてのコントロールに対して、<xref:System.Windows.Forms.Control.Text%2A> プロパティを使用してテキストを設定または返すことができます。</span><span class="sxs-lookup"><span data-stu-id="57d13-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="57d13-106"><xref:System.Windows.Forms.Control.Font%2A> プロパティを使用して、フォントを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="57d13-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span> <span data-ttu-id="57d13-107">また、デザイナーを使用してテキストを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="57d13-107">You can also set the text using the designer.</span></span>  <span data-ttu-id="57d13-108">参照してください[する方法: 作成アクセス キーの Windows フォーム コントロールを使用して、デザイナー](http://msdn.microsoft.com/library/ms233673\(v=vs.110\))、[する方法: デザイナーを使用して Windows フォーム コントロールによって表示されるテキストを設定](http://msdn.microsoft.com/library/ms233665\(v=vs.110\))、[する方法: イメージを設定によって表示される Windows フォーム デザイナーを使用してコントロール](http://msdn.microsoft.com/library/ms233656\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="57d13-108">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a><span data-ttu-id="57d13-109">コントロールによって表示されるテキストをプログラムで設定するには</span><span class="sxs-lookup"><span data-stu-id="57d13-109">To set the text displayed by a control programmatically</span></span>  
  
1.  <span data-ttu-id="57d13-110"><xref:System.Windows.Forms.Control.Text%2A> プロパティを文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="57d13-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>  
  
     <span data-ttu-id="57d13-111">下線付きのアクセス キーを作成するには、アクセス キーにする文字の前にアンパサンド (&) を含めます。</span><span class="sxs-lookup"><span data-stu-id="57d13-111">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>  
  
2.  <span data-ttu-id="57d13-112"><xref:System.Windows.Forms.Control.Font%2A> プロパティを型 <xref:System.Drawing.Font> のオブジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="57d13-112">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="57d13-113">エスケープ文字を使用すると、メニュー項目など、通常は別の解釈がなされるユーザー インターフェイス要素の特殊文字を表示できます。</span><span class="sxs-lookup"><span data-stu-id="57d13-113">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="57d13-114">たとえば、次のコード行は、メニュー項目のテキストが "& Now For Something Completely Different" と読めるように設定します。</span><span class="sxs-lookup"><span data-stu-id="57d13-114">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="57d13-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="57d13-115">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="57d13-116">方法: Windows フォーム コントロールのアクセス キーを作成する</span><span class="sxs-lookup"><span data-stu-id="57d13-116">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [<span data-ttu-id="57d13-117">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="57d13-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
