---
title: "方法 : Visual Basic でアプリケーション設定を読み取る"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="8fed3-102">方法 : Visual Basic でアプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="8fed3-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="8fed3-103">`My.Settings` オブジェクトで設定のプロパティにアクセスすると、ユーザー設定を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="8fed3-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="8fed3-104">`My.Settings` オブジェクトでは、各設定はプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="8fed3-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="8fed3-105">プロパティ名はその設定の名前と同じで、プロパティの型は設定の型と同じです。</span><span class="sxs-lookup"><span data-stu-id="8fed3-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="8fed3-106">プロパティが読み取り専用かどうかは、設定の**スコープ**でわかります。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み取り/書き込みです。</span><span class="sxs-lookup"><span data-stu-id="8fed3-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="8fed3-107">詳細については、「[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fed3-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fed3-108">例</span><span class="sxs-lookup"><span data-stu-id="8fed3-108">Example</span></span>  
 <span data-ttu-id="8fed3-109">次の例は、`Nickname` の設定値を表示します。</span><span class="sxs-lookup"><span data-stu-id="8fed3-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 <span data-ttu-id="8fed3-110">この例を実行するには、アプリケーションで `String` 型の `Nickname` を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8fed3-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="8fed3-111">詳細については、[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fed3-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fed3-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fed3-112">See Also</span></span>  
 [<span data-ttu-id="8fed3-113">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="8fed3-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="8fed3-114">方法: Visual Basic でユーザー設定を変更する</span><span class="sxs-lookup"><span data-stu-id="8fed3-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="8fed3-115">方法: Visual Basic でユーザー設定を永続化する</span><span class="sxs-lookup"><span data-stu-id="8fed3-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="8fed3-116">方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="8fed3-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="8fed3-117">アプリケーションの設定の管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="8fed3-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
