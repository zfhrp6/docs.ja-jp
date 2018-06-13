---
title: マルチ ドキュメント インターフェイス (MDI) アプリケーション
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 3fa6f2517b52ecaaf4ad9db4f0de55908eac4c96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523969"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="d1bd2-102">マルチ ドキュメント インターフェイス (MDI) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="d1bd2-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="d1bd2-103">マルチ ドキュメント インターフェイス (MDI) アプリケーションでは、独自のウィンドウに表示される各ドキュメントに、同時に複数のドキュメントを表示できます。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="d1bd2-104">MDI アプリケーションには、多くの場合、ウィンドウまたはドキュメントを切り替えるためのサブメニューのあるウィンドウのメニュー項目があります。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1bd2-105">いくつかの動作の違い MDI フォームとシングル ドキュメント インターフェイス (SDI) windows と Windows フォームがあります。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="d1bd2-106">`Opacity`プロパティでは MDI 子フォームの外観には影響しません。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="d1bd2-107">さらに、<xref:System.Windows.Forms.Form.CenterToParent%2A>メソッドでは MDI 子フォームの動作には影響しません。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1bd2-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d1bd2-108">In This Section</span></span>  
 [<span data-ttu-id="d1bd2-109">方法: MDI 親フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="d1bd2-109">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="d1bd2-110">MDI アプリケーション内で複数のドキュメントのコンテナーを作成するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="d1bd2-111">方法: MDI 子フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="d1bd2-111">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="d1bd2-112">MDI 親フォーム内で動作する 1 つまたは複数のウィンドウを作成するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="d1bd2-113">方法: アクティブな MDI 子フォームを特定する</span><span class="sxs-lookup"><span data-stu-id="d1bd2-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="d1bd2-114">フォーカスがある子ウィンドウを確認するための手順を示します (とその内容をクリップボードに送信する)。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="d1bd2-115">方法: アクティブな MDI 子フォームにデータを送信する</span><span class="sxs-lookup"><span data-stu-id="d1bd2-115">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="d1bd2-116">アクティブな子ウィンドウに情報を転送するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="d1bd2-117">方法: MDI 子フォームを配置する</span><span class="sxs-lookup"><span data-stu-id="d1bd2-117">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="d1bd2-118">並べて表示、重ねて表示したり、または MDI アプリケーションの子ウィンドウの配置の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="d1bd2-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
