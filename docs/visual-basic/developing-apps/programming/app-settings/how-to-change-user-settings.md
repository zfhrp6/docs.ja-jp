---
title: "方法 : Visual Basic でユーザー設定を変更する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db35a5d63938fcc508c23af5588957d8dc518676
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="32b32-102">方法 : Visual Basic でユーザー設定を変更する</span><span class="sxs-lookup"><span data-stu-id="32b32-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="32b32-103">ユーザー設定を変更するには、`My.Settings` オブジェクトにある設定のプロパティに新しい値を代入します。</span><span class="sxs-lookup"><span data-stu-id="32b32-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="32b32-104">`My.Settings` オブジェクトでは、各設定はプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="32b32-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="32b32-105">プロパティ名はその設定の名前と同じで、プロパティの型は設定の型と同じです。</span><span class="sxs-lookup"><span data-stu-id="32b32-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="32b32-106">プロパティが読み取り専用かどうかは、設定の**スコープ**でわかります。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み取り/書き込みです。</span><span class="sxs-lookup"><span data-stu-id="32b32-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="32b32-107">詳細については、「[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32b32-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32b32-108">ユーザー スコープ設定の値は実行時に変更および保存できますが、アプリケーション スコープ設定は読み取り専用であり、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="32b32-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="32b32-109">アプリケーション スコープの設定を変更するには、アプリケーションを作成するときに、**プロジェクト デザイナー**を使用するか、アプリケーションの構成ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="32b32-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="32b32-110">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32b32-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32b32-111">例</span><span class="sxs-lookup"><span data-stu-id="32b32-111">Example</span></span>  
 <span data-ttu-id="32b32-112">この例では、`Nickname` ユーザー設定の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="32b32-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 <span data-ttu-id="32b32-113">この例を動作させるには、アプリケーションに `String` 型の `Nickname` ユーザー設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="32b32-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="32b32-114">アプリケーションがユーザー設定を保存するのは、アプリケーションの終了時です。</span><span class="sxs-lookup"><span data-stu-id="32b32-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="32b32-115">設定をすぐに保存するには、`My.Settings.Save` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="32b32-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="32b32-116">詳細については、「[方法: Visual Basic でユーザー設定を永続化する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32b32-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b32-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="32b32-117">See Also</span></span>  
 [<span data-ttu-id="32b32-118">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="32b32-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="32b32-119">方法: Visual Basic でアプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="32b32-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="32b32-120">方法: Visual Basic でユーザー設定を永続化する</span><span class="sxs-lookup"><span data-stu-id="32b32-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="32b32-121">方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="32b32-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="32b32-122">アプリケーションの設定の管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="32b32-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
