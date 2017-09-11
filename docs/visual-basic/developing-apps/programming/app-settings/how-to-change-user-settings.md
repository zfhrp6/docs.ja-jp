---
title: "方法 : Visual Basic でユーザー設定を変更する"
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
- user settings, changing in Visual Basic
- user settings
- My.Settings object, changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: 18
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
ms.openlocfilehash: bfc5e5959d691e6a5f77fcffdb61c99bafa29aac
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="9fb7d-102">方法 : Visual Basic でユーザー設定を変更する</span><span class="sxs-lookup"><span data-stu-id="9fb7d-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="9fb7d-103">ユーザー設定を変更するには、`My.Settings` オブジェクトにある設定のプロパティに新しい値を代入します。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="9fb7d-104">`My.Settings` オブジェクトでは、各設定はプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="9fb7d-105">プロパティ名はその設定の名前と同じで、プロパティの型は設定の型と同じです。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="9fb7d-106">プロパティが読み取り専用かどうかは、設定の**スコープ**でわかります。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み取り/書き込みです。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="9fb7d-107">詳細については、「[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fb7d-108">ユーザー スコープ設定の値は実行時に変更および保存できますが、アプリケーション スコープ設定は読み取り専用であり、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="9fb7d-109">アプリケーション スコープの設定を変更するには、アプリケーションを作成するときに、**プロジェクト デザイナー**を使用するか、アプリケーションの構成ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="9fb7d-110">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fb7d-111">例</span><span class="sxs-lookup"><span data-stu-id="9fb7d-111">Example</span></span>  
 <span data-ttu-id="9fb7d-112">この例では、`Nickname` ユーザー設定の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 <span data-ttu-id="9fb7d-113">[!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9fb7d-113">[!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]</span></span>  
  
 <span data-ttu-id="9fb7d-114">この例を動作させるには、アプリケーションに `String` 型の `Nickname` ユーザー設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-114">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="9fb7d-115">アプリケーションがユーザー設定を保存するのは、アプリケーションの終了時です。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-115">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="9fb7d-116">設定をすぐに保存するには、`My.Settings.Save` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-116">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="9fb7d-117">詳細については、「[方法: Visual Basic でユーザー設定を永続化する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fb7d-117">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb7d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fb7d-118">See Also</span></span>  
 <span data-ttu-id="9fb7d-119">[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md) </span><span class="sxs-lookup"><span data-stu-id="9fb7d-119">[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md) </span></span>  
 <span data-ttu-id="9fb7d-120">[方法: Visual Basic でアプリケーション設定を読み取る](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span><span class="sxs-lookup"><span data-stu-id="9fb7d-120">[How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span></span>  
 <span data-ttu-id="9fb7d-121">[方法: Visual Basic でユーザー設定を永続化する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="9fb7d-121">[How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span></span>  
 <span data-ttu-id="9fb7d-122">[方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="9fb7d-122">[How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span></span>  
 [<span data-ttu-id="9fb7d-123">アプリケーションの設定の管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="9fb7d-123">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)

