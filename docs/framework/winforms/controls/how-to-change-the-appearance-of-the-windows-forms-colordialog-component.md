---
title: '方法 : Windows フォーム ColorDialog コンポーネントの表示形式を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 816850fa61de97b5f4c251571a74da7e0a70cba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530248"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="23b21-102">方法 : Windows フォーム ColorDialog コンポーネントの表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="23b21-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="23b21-103">Windows フォームの外観を構成する<xref:System.Windows.Forms.ColorDialog>コンポーネントはそのプロパティの数。</span><span class="sxs-lookup"><span data-stu-id="23b21-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="23b21-104">ダイアログ ボックスには、次の 2 つのセクションでは、基本色とユーザーがカスタム カラーを定義できるいずれかを示す 1 つです。</span><span class="sxs-lookup"><span data-stu-id="23b21-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="23b21-105">ほとんどのプロパティは、ユーザーがダイアログ ボックスから選択できる色を制限します。</span><span class="sxs-lookup"><span data-stu-id="23b21-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="23b21-106">場合、<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>プロパティに設定されている`true`ユーザーがカスタム カラーを定義できるようにします。</span><span class="sxs-lookup"><span data-stu-id="23b21-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="23b21-107"><xref:System.Windows.Forms.ColorDialog.FullOpen%2A>プロパティは`true`カスタム カラーを定義する ダイアログ ボックスが展開されている場合それ以外の場合、ユーザー必要があります、"を定義するカスタム カラー ボタンをクリックして"です。</span><span class="sxs-lookup"><span data-stu-id="23b21-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="23b21-108">ときに、<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>プロパティに設定されている`true`、ダイアログ ボックスは、基本色のセットで使用可能なすべての色を表示します。</span><span class="sxs-lookup"><span data-stu-id="23b21-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="23b21-109">場合、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>プロパティに設定されている`true`ユーザーがディザリングされた色を選択できません; を選択する純色のみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="23b21-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="23b21-110">場合、<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>プロパティに設定されている`true`、ダイアログ ボックスで、[ヘルプ] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="23b21-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="23b21-111">ユーザーがヘルプ ボタンをクリックしたときに、<xref:System.Windows.Forms.ColorDialog>コンポーネントの<xref:System.Windows.Forms.CommonDialog.HelpRequest>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="23b21-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="23b21-112">色のダイアログ ボックスの外観を構成するには</span><span class="sxs-lookup"><span data-stu-id="23b21-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="23b21-113">設定、 <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>、 <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>、 <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>、および<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>プロパティを目的の値にします。</span><span class="sxs-lookup"><span data-stu-id="23b21-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="23b21-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="23b21-114">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="23b21-115">ColorDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="23b21-115">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="23b21-116">ColorDialog コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="23b21-116">ColorDialog Component Overview</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
