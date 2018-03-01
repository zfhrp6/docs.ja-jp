---
title: "FolderBrowserDialog コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26d2b6294a503edd25b499da2ab67739cdf87174
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="8a3ff-102">FolderBrowserDialog コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="8a3ff-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="8a3ff-103">Windows フォーム<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントは、モーダル ダイアログ ボックスを参照してフォルダーを選択するために使用します。</span><span class="sxs-lookup"><span data-stu-id="8a3ff-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="8a3ff-104">内から新しいフォルダーを作成することも、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="8a3ff-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a3ff-105">フォルダーではなく、ファイルを選択するには、 [OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="8a3ff-105">To select files, instead of folders, use the [OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md) component.</span></span>  
  
 <span data-ttu-id="8a3ff-106"><xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントを使用して実行時に表示されている、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8a3ff-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="8a3ff-107">設定、<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>最上位のフォルダーと、ダイアログ ボックスのツリー ビューに表示されるすべてのサブフォルダーを決定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8a3ff-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="8a3ff-108">ダイアログ ボックスが表示されると、使用できます、<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>プロパティが選択されているフォルダーのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a3ff-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>  
  
 <span data-ttu-id="8a3ff-109">フォームに追加されたとき、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a3ff-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3ff-110">参照</span><span class="sxs-lookup"><span data-stu-id="8a3ff-110">See Also</span></span>  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [<span data-ttu-id="8a3ff-111">方法: Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する</span><span class="sxs-lookup"><span data-stu-id="8a3ff-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)  
 [<span data-ttu-id="8a3ff-112">FolderBrowserDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8a3ff-112">FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
