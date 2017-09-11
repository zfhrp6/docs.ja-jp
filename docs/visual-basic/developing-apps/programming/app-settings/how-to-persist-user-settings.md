---
title: "方法 : Visual Basic でユーザー設定を永続化する"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Settings object, persisting user settings
- persistence, persisting user settings [Visual Basic]
- user settings, persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: 15
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
ms.openlocfilehash: a5553acd031db7e9be9c87afaeba61aea9bb2111
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="53e95-102">方法 : Visual Basic でユーザー設定を永続化する</span><span class="sxs-lookup"><span data-stu-id="53e95-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="53e95-103">`My.Settings.Save` メソッドを使用して、ユーザー設定の変更を永続化できます。</span><span class="sxs-lookup"><span data-stu-id="53e95-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="53e95-104">通常、アプリケーションでは、ユーザー設定の変更を、アプリケーションのシャットダウン時に永続化するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="53e95-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="53e95-105">これは、複数の要因から、設定の保存に数秒かかることがあるためです。</span><span class="sxs-lookup"><span data-stu-id="53e95-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="53e95-106">詳細については、「[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53e95-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53e95-107">ユーザー スコープ設定の値は実行時に変更および保存できますが、アプリケーション スコープ設定は読み取り専用であり、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="53e95-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="53e95-108">アプリケーション スコープの設定を変更するには、アプリケーションを作成するときに、**プロジェクト デザイナー**を使用するか、アプリケーションの構成ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="53e95-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="53e95-109">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53e95-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53e95-110">例</span><span class="sxs-lookup"><span data-stu-id="53e95-110">Example</span></span>  
 <span data-ttu-id="53e95-111">この例では、`LastChanged` ユーザー設定の値を変更し、`My.Settings.Save` メソッドを呼び出して、その変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="53e95-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 <span data-ttu-id="53e95-112">[!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="53e95-112">[!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]</span></span>  
  
 <span data-ttu-id="53e95-113">この例を動作させるには、アプリケーションに `Date` 型の `LastChanged` ユーザー設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="53e95-113">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="53e95-114">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53e95-114">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e95-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="53e95-115">See Also</span></span>  
 <span data-ttu-id="53e95-116">[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md) </span><span class="sxs-lookup"><span data-stu-id="53e95-116">[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md) </span></span>  
 <span data-ttu-id="53e95-117">[方法: Visual Basic でアプリケーション設定を読み取る](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span><span class="sxs-lookup"><span data-stu-id="53e95-117">[How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span></span>  
 <span data-ttu-id="53e95-118">[方法: Visual Basic でユーザー設定を変更する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="53e95-118">[How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span></span>  
 <span data-ttu-id="53e95-119">[方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="53e95-119">[How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span></span>  
 [<span data-ttu-id="53e95-120">アプリケーションの設定の管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="53e95-120">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)

