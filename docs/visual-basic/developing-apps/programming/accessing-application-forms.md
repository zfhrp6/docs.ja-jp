---
title: "アプリケーション フォームへのアクセス (Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- forms, communicating between
- application forms, accessing
- forms, accessing one from another
- My.Forms object
- forms, accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 37c8aa78d945a4d13ce00239d6b0707977f2571e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="69657-102">アプリケーション フォームへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69657-102">Accessing Application Forms (Visual Basic)</span></span>
<span data-ttu-id="69657-103">`My.Forms` オブジェクトは、アプリケーションのプロジェクトで宣言された各 Windows フォームのインスタンスに簡単にアクセスする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="69657-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="69657-104">`My.Application` オブジェクトのプロパティを利用し、アプリケーションのスプラッシュ スクリーンとメイン フォームにアクセスし、アプリケーションのオープン フォームの一覧を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="69657-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="69657-105">タスク</span><span class="sxs-lookup"><span data-stu-id="69657-105">Tasks</span></span>  
 <span data-ttu-id="69657-106">次の表に示すのは、アプリケーションのフォームにアクセスする方法を示す例です。</span><span class="sxs-lookup"><span data-stu-id="69657-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="69657-107">目的</span><span class="sxs-lookup"><span data-stu-id="69657-107">To</span></span>|<span data-ttu-id="69657-108">参照トピック</span><span class="sxs-lookup"><span data-stu-id="69657-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="69657-109">アプリケーションのあるフォームから別のフォームにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="69657-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="69657-110">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="69657-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="69657-111">アプリケーションのすべてのオープン フォームのタイトルを表示します。</span><span class="sxs-lookup"><span data-stu-id="69657-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="69657-112">アプリケーションの起動時に状態情報でスプラッシュ スクリーンを更新します。</span><span class="sxs-lookup"><span data-stu-id="69657-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="69657-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="69657-113">See Also</span></span>  
 <span data-ttu-id="69657-114"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></span><span class="sxs-lookup"><span data-stu-id="69657-114"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></span></span>   
 <span data-ttu-id="69657-115"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A></span><span class="sxs-lookup"><span data-stu-id="69657-115"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A></span></span>   
 [<span data-ttu-id="69657-116">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="69657-116">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)

