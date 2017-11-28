---
title: "Windows フォームのダイアログ ボックス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1660bf08f10a7d4e0db4b7ae8d58fd631986974c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="d41b9-102">Windows フォームのダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="d41b9-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="d41b9-103">ダイアログ ボックスは、ユーザーとのやり取りおよび情報の取得のために使用します。</span><span class="sxs-lookup"><span data-stu-id="d41b9-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="d41b9-104">簡単に言えば、ダイアログ ボックスとは <xref:System.Windows.Forms.FormBorderStyle> 列挙値のプロパティが `FixedDialog` に設定されたフォームのことです。</span><span class="sxs-lookup"><span data-stu-id="d41b9-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="d41b9-105">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の Windows フォーム デザイナーを使用して、独自のカスタム ダイアログ ボックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d41b9-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="d41b9-106">`Label`、`Textbox`、および `Button` などのコントロールを追加し、ダイアログ ボックスを特定のニーズに合わせてカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d41b9-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="d41b9-107">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]もなど定義済みダイアログ ボックスが含まれる**ファイルを開く**とメッセージ ボックスは、独自のアプリケーションに適応させることができます。</span><span class="sxs-lookup"><span data-stu-id="d41b9-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="d41b9-108">詳細については、次を参照してください。 [ ダイアログ ボックス コントロールおよびコンポーネント](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="d41b9-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d41b9-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d41b9-109">In This Section</span></span>  
 [<span data-ttu-id="d41b9-110">方法: Windows フォームのダイアログ ボックスを表示する</span><span class="sxs-lookup"><span data-stu-id="d41b9-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="d41b9-111">ダイアログ ボックスを表示する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="d41b9-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="d41b9-112">[方法: 選択的に複数のプロパティを使用してダイアログ ボックスの情報の取得](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d41b9-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d41b9-113">[方法: ダイアログ ボックスの親フォームから情報を取得](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d41b9-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d41b9-114">[ダイアログ ボックスにユーザー入力](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d41b9-114">[User Input to Dialog Boxes](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d41b9-115">[方法: ダイアログ ボックスの結果の取得](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d41b9-115">[How to: Retrieve the Result for Dialog Boxes](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d41b9-116">[チュートリアル: オブジェクトによるダイアログ ボックスの情報を取得します。](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d41b9-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d41b9-117">[方法: ダイアログ ボックスを閉じるし、ユーザー入力を保持](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d41b9-117">[How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d41b9-118">[方法: デザイン時にダイアログ ボックスの作成](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d41b9-118">[How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d41b9-119">[方法: メッセージ ボックスを表示](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d41b9-119">[How to: Display Message Boxes](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d41b9-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d41b9-120">Related Sections</span></span>  
 [<span data-ttu-id="d41b9-121">ダイアログ ボックス コントロールおよびコンポーネント</span><span class="sxs-lookup"><span data-stu-id="d41b9-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="d41b9-122">定義済みダイアログ ボックス コントロールの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="d41b9-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="d41b9-123">Windows フォームの表示形式の変更</span><span class="sxs-lookup"><span data-stu-id="d41b9-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="d41b9-124">Windows フォーム アプリケーションの外観を変更する方法について説明したトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="d41b9-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="d41b9-125">TabControl コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="d41b9-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="d41b9-126">ダイアログ ボックスにタブ コントロールを組み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d41b9-126">Explains how you incorporate the tab control into a dialog box.</span></span>
