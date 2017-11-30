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
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="a3cb4-102">ColorDialog コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="a3cb4-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="a3cb4-103">Windows フォーム<xref:System.Windows.Forms.ColorDialog>コンポーネントは、ユーザーがパレットから色を選択し、そのパレットに色を追加できる構成済みのダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="a3cb4-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="a3cb4-104">このダイアログ ボックスは、他の Windows ベースのアプリケーションで表示される色を選択するためのダイアログ ボックスと同じです。</span><span class="sxs-lookup"><span data-stu-id="a3cb4-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="a3cb4-105">このコントロールは、独自のダイアログ ボックスを使用しない簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。</span><span class="sxs-lookup"><span data-stu-id="a3cb4-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="a3cb4-106">ダイアログ ボックスで選択された色が返される、<xref:System.Windows.Forms.ColorDialog.Color%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a3cb4-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="a3cb4-107">場合、<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>プロパティに設定されている`false`、「色」ボタンが無効になり、ユーザーは、パレットで定義済みの色に制限します。</span><span class="sxs-lookup"><span data-stu-id="a3cb4-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="a3cb4-108">場合、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>プロパティに設定されている`true`ユーザーがディザリングされた色を選択できません。</span><span class="sxs-lookup"><span data-stu-id="a3cb4-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="a3cb4-109">ダイアログ ボックスを表示するには、呼び出す必要があります、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a3cb4-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3cb4-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3cb4-110">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="a3cb4-111">ColorDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a3cb4-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="a3cb4-112">ダイアログ ボックス コントロールおよびコンポーネント</span><span class="sxs-lookup"><span data-stu-id="a3cb4-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [<span data-ttu-id="a3cb4-113">方法: Windows フォーム ColorDialog コンポーネントの表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="a3cb4-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
