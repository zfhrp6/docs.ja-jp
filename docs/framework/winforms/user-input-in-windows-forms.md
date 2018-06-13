---
title: Windows フォームでのユーザー入力
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- Windows Forms, user input
- mouse input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
ms.assetid: 1486075f-1e06-4c9e-82c6-f948331db6d6
ms.openlocfilehash: 2a618dae8d5f2f5ea6a6581fff2758fe8419f511
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537734"
---
# <a name="user-input-in-windows-forms"></a><span data-ttu-id="9de79-102">Windows フォームでのユーザー入力</span><span class="sxs-lookup"><span data-stu-id="9de79-102">User Input in Windows Forms</span></span>
<span data-ttu-id="9de79-103">Windows フォームには、関連する Windows メッセージの処理中に発生するイベントに基づくユーザーの入力モデルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9de79-103">Windows Forms includes a user input model based on events that are raised while processing related Windows messages.</span></span> <span data-ttu-id="9de79-104">特定のタスクを実行する方法を示すコード例を含む、マウスとキーボードのユーザー入力については、このセクションのトピックで説明します。</span><span class="sxs-lookup"><span data-stu-id="9de79-104">The topics in this section provide information on mouse and keyboard user input, including code examples that demonstrate how to perform specific tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9de79-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9de79-105">In This Section</span></span>  
 [<span data-ttu-id="9de79-106">Windows フォーム アプリケーションにおけるユーザー入力</span><span class="sxs-lookup"><span data-stu-id="9de79-106">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="9de79-107">ユーザーの入力イベント、および Windows メッセージを処理するメソッドの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="9de79-107">Provides an overview of user input events and the methods that process Windows messages.</span></span>  
  
 [<span data-ttu-id="9de79-108">Windows フォーム アプリケーションにおけるキーボード入力</span><span class="sxs-lookup"><span data-stu-id="9de79-108">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="9de79-109">キーボードのメッセージ処理、様々な種類のキー、およびキーボード イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9de79-109">Provides information on keyboard message handling, the different types of keys, and the keyboard events.</span></span>  
  
 [<span data-ttu-id="9de79-110">Windows フォーム アプリケーションにおけるマウス入力</span><span class="sxs-lookup"><span data-stu-id="9de79-110">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="9de79-111">マウスのカーソルとマウスのキャプチャなど、マウス イベントやその他のマウスに関連する機能の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="9de79-111">Provides information on the mouse events and other mouse-related features, including mouse cursors and mouse capture.</span></span>  
  
 [<span data-ttu-id="9de79-112">方法: マウス イベントとキーボード イベントをコードでシミュレートする</span><span class="sxs-lookup"><span data-stu-id="9de79-112">How to: Simulate Mouse and Keyboard Events in Code</span></span>](../../../docs/framework/winforms/how-to-simulate-mouse-and-keyboard-events-in-code.md)  
 <span data-ttu-id="9de79-113">プログラムでマウスおよびキーボード入力をシミュレートするいくつかの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9de79-113">Demonstrates several different ways to programmatically simulate mouse and keyboard input.</span></span>  
  
 [<span data-ttu-id="9de79-114">方法: Windows フォーム コントロールでユーザー入力イベントを処理する</span><span class="sxs-lookup"><span data-stu-id="9de79-114">How to: Handle User Input Events in Windows Forms Controls</span></span>](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md)  
 <span data-ttu-id="9de79-115">ほとんどのユーザーの入力イベントを処理し、各イベントに関する情報をレポートするコード例を表示します。</span><span class="sxs-lookup"><span data-stu-id="9de79-115">Presents a code example that handles most user input events and reports information about each event.</span></span>  
  
 [<span data-ttu-id="9de79-116">Windows フォームでのユーザー入力の検証</span><span class="sxs-lookup"><span data-stu-id="9de79-116">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 <span data-ttu-id="9de79-117">Windows フォーム アプリケーションでユーザー入力を検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9de79-117">Describes the methods to validate user input in Windows Forms applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9de79-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9de79-118">Related Sections</span></span>  
 <span data-ttu-id="9de79-119">参照してください[Windows フォームでのイベント ハンドラーの作成](http://msdn.microsoft.com/library/dacysss4\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="9de79-119">Also see [Creating Event Handlers in Windows Forms](http://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span></span>
