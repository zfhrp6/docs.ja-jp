---
title: "方法 : Windows フォーム コントロールに表示するテキストをデザイナーで設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59d66df2c6f18ad28ad4b912c00e35f786d773da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="3ec6d-102">方法 : Windows フォーム コントロールに表示するテキストをデザイナーで設定する</span><span class="sxs-lookup"><span data-stu-id="3ec6d-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="3ec6d-103">Windows フォーム コントロールは、通常、コントロールの主な機能に関連するいくつかのテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="3ec6d-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="3ec6d-104">たとえば、<xref:System.Windows.Forms.Button>コントロールには、通常、ボタンがクリックされたときに実行するアクションを示すキャプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3ec6d-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="3ec6d-105">すべてのコントロールに対して、<xref:System.Windows.Forms.Control.Text%2A> プロパティを使用してテキストを設定または返すことができます。</span><span class="sxs-lookup"><span data-stu-id="3ec6d-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="3ec6d-106"><xref:System.Windows.Forms.Control.Font%2A> プロパティを使用して、フォントを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="3ec6d-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="3ec6d-107">テキストと、デザイナーでのフォントを設定するには</span><span class="sxs-lookup"><span data-stu-id="3ec6d-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="3ec6d-108">[プロパティ] ウィンドウで、設定、<xref:System.Windows.Forms.Control.Text%2A>適切な文字列をコントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="3ec6d-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="3ec6d-109">下線付きのショートカット キーを作成する、アンパサンドが含まれています (&) は、ショートカット キーとなる文字の前にします。</span><span class="sxs-lookup"><span data-stu-id="3ec6d-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="3ec6d-110">[プロパティ] ウィンドウで、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、<xref:System.Windows.Forms.Control.Font%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3ec6d-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="3ec6d-111">標準のフォント ダイアログ ボックスで、フォント、フォント スタイル、サイズ、(取り消し線、下線) などの効果とスクリプトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3ec6d-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ec6d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ec6d-112">See Also</span></span>  
 [<span data-ttu-id="3ec6d-113">方法: Windows フォーム コントロールによって表示されるテキストを設定する</span><span class="sxs-lookup"><span data-stu-id="3ec6d-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="3ec6d-114">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="3ec6d-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="3ec6d-115">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="3ec6d-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
