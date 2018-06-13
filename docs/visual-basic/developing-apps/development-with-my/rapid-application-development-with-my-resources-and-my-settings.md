---
title: My.Resources と My.Settings による Rapid Application Development (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 808e02510d4f0a237ad4354b2edac8fa024b5f83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582273"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="0ea68-102">My.Resources と My.Settings による Rapid Application Development (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ea68-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="0ea68-103">`My.Resources`オブジェクトは、アプリケーションのリソースへのアクセスを提供し、アプリケーションのリソースを動的に取得することができます。</span><span class="sxs-lookup"><span data-stu-id="0ea68-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="0ea68-104">リソースの取得</span><span class="sxs-lookup"><span data-stu-id="0ea68-104">Retrieving Resources</span></span>  
 <span data-ttu-id="0ea68-105">使用して取得できるオーディオ ファイル、アイコン、イメージ、および文字列などのリソースの数、`My.Resources`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0ea68-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="0ea68-106">たとえば、アプリケーションのカルチャに固有のリソース ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="0ea68-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="0ea68-107">次の例は、という名前のアイコンをフォームのアイコンを設定`Form1Icon`アプリケーションのリソース ファイルに格納します。</span><span class="sxs-lookup"><span data-stu-id="0ea68-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="0ea68-108">`My.Resources`オブジェクトはグローバル リソースのみを公開します。</span><span class="sxs-lookup"><span data-stu-id="0ea68-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="0ea68-109">フォームに関連付けられているリソース ファイルへのアクセスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="0ea68-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="0ea68-110">フォームからフォーム リソースにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ea68-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="0ea68-111">同様に、`My.Settings`オブジェクトがアプリケーションの設定にアクセスできるようにし、動的に格納およびプロパティの設定と、アプリケーションの他の情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="0ea68-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="0ea68-112">詳細については、次を参照してください。 [My.Resources オブジェクト](../../../visual-basic/language-reference/objects/my-resources-object.md)と[My.Settings オブジェクト](../../../visual-basic/language-reference/objects/my-settings-object.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ea68-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea68-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ea68-113">See Also</span></span>  
 [<span data-ttu-id="0ea68-114">My.Resources オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0ea68-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [<span data-ttu-id="0ea68-115">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0ea68-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="0ea68-116">アプリケーション設定へのアクセス</span><span class="sxs-lookup"><span data-stu-id="0ea68-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
