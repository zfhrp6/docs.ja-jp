---
title: "ImageList コンポーネントの概要 (Windows フォーム)"
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
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a913de1a6808c7e600a4f28ed58dedf93506466b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imagelist-component-overview-windows-forms"></a><span data-ttu-id="730d6-102">ImageList コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="730d6-102">ImageList Component Overview (Windows Forms)</span></span>
<span data-ttu-id="730d6-103">Windows フォーム <xref:System.Windows.Forms.ImageList> コンポーネントは、コントロールで表示するイメージの保存に使用します。</span><span class="sxs-lookup"><span data-stu-id="730d6-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is used to store images, which can then be displayed by controls.</span></span> <span data-ttu-id="730d6-104">イメージ リストでは、一貫性のある 1 つのイメージのカタログのコードを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="730d6-104">An image list allows you to write code for a single, consistent catalog of images.</span></span> <span data-ttu-id="730d6-105">たとえば、ボタンの <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> プロパティまたは <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> プロパティを変更するだけで、<xref:System.Windows.Forms.Button> コントロールによって表示されるイメージを回転できます。</span><span class="sxs-lookup"><span data-stu-id="730d6-105">For example, you can rotate images displayed by a <xref:System.Windows.Forms.Button> control simply by changing the button's <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> or <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> property.</span></span> <span data-ttu-id="730d6-106">同じイメージのリストを複数のコントロールに関連付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="730d6-106">You can also associate the same image list with multiple controls.</span></span> <span data-ttu-id="730d6-107">たとえば、<xref:System.Windows.Forms.ListView> コントロールと <xref:System.Windows.Forms.TreeView> コントロールの両方を使用して同じファイルのリストを表示する場合、イメージのリストでファイルのアイコンを変更すると、新しいアイコンが両方のビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="730d6-107">For example, if you are using both a <xref:System.Windows.Forms.ListView> control and a <xref:System.Windows.Forms.TreeView> control to display the same list of files, changing a file's icon in the image list will cause the new icon to appear in both views.</span></span>  
  
## <a name="using-imagelist-with-controls"></a><span data-ttu-id="730d6-108">コントロールでの ImageList の使用</span><span class="sxs-lookup"><span data-stu-id="730d6-108">Using ImageList with Controls</span></span>  
 <span data-ttu-id="730d6-109">`ImageList` プロパティを持つコントロール (<xref:System.Windows.Forms.ListView> コントロールの場合は <xref:System.Windows.Forms.ListView.SmallImageList%2A> プロパティと <xref:System.Windows.Forms.ListView.LargeImageList%2A> プロパティ) でイメージ リストを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="730d6-109">You can use an image list with any control that has an `ImageList` property — or in the case of the <xref:System.Windows.Forms.ListView> control, <xref:System.Windows.Forms.ListView.SmallImageList%2A> and <xref:System.Windows.Forms.ListView.LargeImageList%2A> properties.</span></span> <span data-ttu-id="730d6-110">イメージ リストに関連付けることができるコントロールは、<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.ToolBar>、<xref:System.Windows.Forms.TabControl>、<xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.CheckBox>、<xref:System.Windows.Forms.RadioButton>、および <xref:System.Windows.Forms.Label> の各コントロールです。</span><span class="sxs-lookup"><span data-stu-id="730d6-110">The controls that can be associated with an image list include: the <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, and <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="730d6-111">イメージ リストをコントロールに関連付けるには、コントロールの `ImageList` プロパティを <xref:System.Windows.Forms.ImageList> コンポーネントの名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="730d6-111">To associate the image list with a control, set the control's `ImageList` property to the name of the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="730d6-112">キー プロパティ</span><span class="sxs-lookup"><span data-stu-id="730d6-112">Key Properties</span></span>  
 <span data-ttu-id="730d6-113"><xref:System.Windows.Forms.ImageList> コンポーネントのキー プロパティは <xref:System.Windows.Forms.ImageList.Images%2A> で、関連付けられたコントロールで使用される画像が含まれています。</span><span class="sxs-lookup"><span data-stu-id="730d6-113">The key property of the <xref:System.Windows.Forms.ImageList> component is <xref:System.Windows.Forms.ImageList.Images%2A>, which contains the pictures to be used by the associated control.</span></span> <span data-ttu-id="730d6-114">各イメージは、そのインデックス値、またはそのキーを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="730d6-114">Each individual image can be accessed by its index value or by its key.</span></span> <span data-ttu-id="730d6-115"><xref:System.Windows.Forms.ImageList.ColorDepth%2A> プロパティは、イメージをレンダリングする際の色の数を決定します。</span><span class="sxs-lookup"><span data-stu-id="730d6-115">The <xref:System.Windows.Forms.ImageList.ColorDepth%2A> property determines the number of colors that the images are rendered with.</span></span> <span data-ttu-id="730d6-116">イメージはすべて同じサイズで表示され、<xref:System.Windows.Forms.ImageList.ImageSize%2A> プロパティによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="730d6-116">The images will all be displayed at the same size, set by the <xref:System.Windows.Forms.ImageList.ImageSize%2A> property.</span></span> <span data-ttu-id="730d6-117">大きなイメージはサイズが合うように縮小されます。</span><span class="sxs-lookup"><span data-stu-id="730d6-117">Images that are larger will be scaled to fit.</span></span>  
  
 <span data-ttu-id="730d6-118">[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] を使用している場合は、アプリケーションで使用する標準のイメージの大規模なライブラリにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="730d6-118">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use in your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730d6-119">参照</span><span class="sxs-lookup"><span data-stu-id="730d6-119">See Also</span></span>  
 <xref:System.Windows.Forms.ImageList>  
 [<span data-ttu-id="730d6-120">方法: Windows フォームの ImageList コンポーネントにイメージを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="730d6-120">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
