---
title: "マルチ ドキュメント インターフェイス (MDI) アプリケーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74735afcb1d6be319ad5d497615a3b725a4d5574
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="72b78-102">マルチ ドキュメント インターフェイス (MDI) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="72b78-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="72b78-103">マルチ ドキュメント インターフェイス (MDI) アプリケーションでは、独自のウィンドウに表示される各ドキュメントに、同時に複数のドキュメントを表示できます。</span><span class="sxs-lookup"><span data-stu-id="72b78-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="72b78-104">MDI アプリケーションには、多くの場合、ウィンドウまたはドキュメントを切り替えるためのサブメニューのあるウィンドウのメニュー項目があります。</span><span class="sxs-lookup"><span data-stu-id="72b78-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72b78-105">いくつかの動作の違い MDI フォームとシングル ドキュメント インターフェイス (SDI) windows と Windows フォームがあります。</span><span class="sxs-lookup"><span data-stu-id="72b78-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="72b78-106">`Opacity`プロパティでは MDI 子フォームの外観には影響しません。</span><span class="sxs-lookup"><span data-stu-id="72b78-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="72b78-107">さらに、<xref:System.Windows.Forms.Form.CenterToParent%2A>メソッドでは MDI 子フォームの動作には影響しません。</span><span class="sxs-lookup"><span data-stu-id="72b78-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72b78-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="72b78-108">In This Section</span></span>  
 [<span data-ttu-id="72b78-109">方法: MDI 親フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="72b78-109">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="72b78-110">MDI アプリケーション内で複数のドキュメントのコンテナーを作成するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="72b78-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="72b78-111">方法: MDI 子フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="72b78-111">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="72b78-112">MDI 親フォーム内で動作する 1 つまたは複数のウィンドウを作成するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="72b78-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="72b78-113">方法: アクティブな MDI 子フォームを特定する</span><span class="sxs-lookup"><span data-stu-id="72b78-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="72b78-114">フォーカスがある子ウィンドウを確認するための手順を示します (とその内容をクリップボードに送信する)。</span><span class="sxs-lookup"><span data-stu-id="72b78-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="72b78-115">方法: アクティブな MDI 子フォームにデータを送信する</span><span class="sxs-lookup"><span data-stu-id="72b78-115">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="72b78-116">アクティブな子ウィンドウに情報を転送するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="72b78-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="72b78-117">方法: MDI 子フォームを配置する</span><span class="sxs-lookup"><span data-stu-id="72b78-117">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="72b78-118">並べて表示、重ねて表示したり、または MDI アプリケーションの子ウィンドウの配置の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="72b78-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
