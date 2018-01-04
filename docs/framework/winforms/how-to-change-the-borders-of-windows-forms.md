---
title: "方法 : Windows フォームの境界線を変更する"
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
helpviewer_keywords: Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e977617f16ef882ad0dcfe1a96a6e8af73d2ae48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="34f61-102">方法 : Windows フォームの境界線を変更する</span><span class="sxs-lookup"><span data-stu-id="34f61-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="34f61-103">Windows フォームの外観や動作を決定する際にはさまざまな境界線スタイルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="34f61-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="34f61-104"><xref:System.Windows.Forms.Form.FormBorderStyle%2A> プロパティを変更して、フォームのサイズ変更動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="34f61-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="34f61-105">また、<xref:System.Windows.Forms.Form.FormBorderStyle%2A> を設定すると、キャプション バーの表示方法や、キャプション バーに表示されるボタンを変更できます。</span><span class="sxs-lookup"><span data-stu-id="34f61-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="34f61-106">詳細については、「<xref:System.Windows.Forms.FormBorderStyle>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34f61-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="34f61-107">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] では、このタスクに対する広範なサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="34f61-107">There is extensive support for this task in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="34f61-108">関連項目[する方法: デザイナーを使用して Windows フォームの境界線を変更](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="34f61-108">See also [How to: Change the Borders of Windows Forms Using the Designer](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="34f61-109">プログラムで Windows フォームの境界線スタイルを設定するには</span><span class="sxs-lookup"><span data-stu-id="34f61-109">To set the border style of Windows Forms programmatically</span></span>  
  
-   <span data-ttu-id="34f61-110"><xref:System.Windows.Forms.Form.FormBorderStyle%2A> プロパティを任意のスタイルに設定します。</span><span class="sxs-lookup"><span data-stu-id="34f61-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="34f61-111">次のコード例は、フォームの境界線スタイルを設定`DlgBx1`に<xref:System.Windows.Forms.FormBorderStyle.FixedDialog>です。</span><span class="sxs-lookup"><span data-stu-id="34f61-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="34f61-112">参照してください[する方法: デザイン時にダイアログ ボックスを作成する](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="34f61-112">Also see [How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span></span>  
  
     <span data-ttu-id="34f61-113">さらに、オプションを提供するフォームの境界線のスタイルを選択したかどうか**最小化**と**最大化**ボタン、これらのボタンを機能させるのには、どちらもをするかどうか指定できます。</span><span class="sxs-lookup"><span data-stu-id="34f61-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="34f61-114">これらのボタンは、ユーザーの操作感を細かく調節する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="34f61-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="34f61-115">**最小化**と**最大化**既定では、ボタンが有効になっているし、その機能を使用して操作が、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="34f61-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f61-116">参照</span><span class="sxs-lookup"><span data-stu-id="34f61-116">See Also</span></span>  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [<span data-ttu-id="34f61-117">Windows フォームについて</span><span class="sxs-lookup"><span data-stu-id="34f61-117">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
