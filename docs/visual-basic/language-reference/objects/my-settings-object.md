---
title: "My.Settings オブジェクト |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
dev_langs:
- VB
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4d6ee6d2d54c0e3a4af3b7cdec5f81166ce3ddce
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="mysettings-object"></a><span data-ttu-id="2eb09-102">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="2eb09-102">My.Settings Object</span></span>
<span data-ttu-id="2eb09-103">アプリケーションの設定へのアクセスのプロパティとメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2eb09-104">コメント</span><span class="sxs-lookup"><span data-stu-id="2eb09-104">Remarks</span></span>  
 <span data-ttu-id="2eb09-105">`My.Settings`オブジェクトでは、アプリケーションの設定にアクセスし、動的に格納およびプロパティの設定と、アプリケーションの他の情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="2eb09-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="2eb09-106">詳細については、次を参照してください。[を管理するアプリケーションの設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-106">For more information, see [Managing Application Settings (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2eb09-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2eb09-107">Properties</span></span>  
 <span data-ttu-id="2eb09-108">プロパティ、`My.Settings`オブジェクトは、アプリケーションの設定にアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="2eb09-109">を追加または削除の設定を使用して、**設定デザイナー**します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="2eb09-110">各設定では、**名**、**型**、**スコープ**、および**値**、これらの設定は、各設定にアクセスするプロパティを表示する方法を決定し、`My.Settings`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2eb09-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
-   <span data-ttu-id="2eb09-111">**名前**プロパティの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-111">**Name** determines the name of the property.</span></span>  
  
-   <span data-ttu-id="2eb09-112">**型**プロパティの種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-112">**Type** determines the type of the property.</span></span>  
  
-   <span data-ttu-id="2eb09-113">**スコープ**プロパティは読み取り専用のかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="2eb09-114">値の場合**アプリケーション**、プロパティは読み取り専用です。 値の場合**ユーザー**、プロパティが読み取り/書き込みです。</span><span class="sxs-lookup"><span data-stu-id="2eb09-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
-   <span data-ttu-id="2eb09-115">**値**プロパティの既定値です。</span><span class="sxs-lookup"><span data-stu-id="2eb09-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2eb09-116">メソッド</span><span class="sxs-lookup"><span data-stu-id="2eb09-116">Methods</span></span>  
  
|<span data-ttu-id="2eb09-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="2eb09-117">Method</span></span>|<span data-ttu-id="2eb09-118">説明</span><span class="sxs-lookup"><span data-stu-id="2eb09-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="2eb09-119">最後に保存されている値からユーザーの設定を再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="2eb09-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="2eb09-120">現在のユーザー設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="2eb09-121">`My.Settings`オブジェクトは、高度なプロパティと<xref:System.Configuration.ApplicationSettingsBase>クラス</xref:System.Configuration.ApplicationSettingsBase>から継承されたメソッドにも提供</span><span class="sxs-lookup"><span data-stu-id="2eb09-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="2eb09-122">タスク</span><span class="sxs-lookup"><span data-stu-id="2eb09-122">Tasks</span></span>  
 <span data-ttu-id="2eb09-123">次の表に、関連するタスクの例については、`My.Settings`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="2eb09-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="2eb09-124">目的</span><span class="sxs-lookup"><span data-stu-id="2eb09-124">To</span></span>|<span data-ttu-id="2eb09-125">参照トピック</span><span class="sxs-lookup"><span data-stu-id="2eb09-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="2eb09-126">アプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="2eb09-126">Read an application setting</span></span>|[<span data-ttu-id="2eb09-127">方法: Visual Basic でのアプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="2eb09-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="2eb09-128">ユーザー設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-128">Change a user setting</span></span>|[<span data-ttu-id="2eb09-129">方法: Visual Basic でのユーザー設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="2eb09-130">ユーザー設定します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-130">Persist user settings</span></span>|[<span data-ttu-id="2eb09-131">方法: Visual Basic でのユーザー設定</span><span class="sxs-lookup"><span data-stu-id="2eb09-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="2eb09-132">ユーザー設定のプロパティ グリッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="2eb09-133">方法: Visual Basic でのユーザー設定のプロパティ グリッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="2eb09-134">例</span><span class="sxs-lookup"><span data-stu-id="2eb09-134">Example</span></span>  
 <span data-ttu-id="2eb09-135">この例の値を表示、`Nickname`設定します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 <span data-ttu-id="2eb09-136">[!code-vb[VbVbalrMyResources&#14;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2eb09-136">[!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]</span></span>  
  
 <span data-ttu-id="2eb09-137">この例を実行するには、アプリケーションが必要な`Nickname`型の設定`String`します。</span><span class="sxs-lookup"><span data-stu-id="2eb09-137">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb09-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="2eb09-138">See Also</span></span>  
 <span data-ttu-id="2eb09-139"><xref:System.Configuration.ApplicationSettingsBase></xref:System.Configuration.ApplicationSettingsBase></span><span class="sxs-lookup"><span data-stu-id="2eb09-139"><xref:System.Configuration.ApplicationSettingsBase></span></span>   
<span data-ttu-id="2eb09-140"> [方法: Visual Basic でのアプリケーション設定を読み取る](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span><span class="sxs-lookup"><span data-stu-id="2eb09-140"> [How to: Read Application Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span></span>  
<span data-ttu-id="2eb09-141"> [方法: Visual Basic でのユーザー設定を変更します。](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="2eb09-141"> [How to: Change User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span></span>  
<span data-ttu-id="2eb09-142"> [方法: Visual Basic でのユーザー設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="2eb09-142"> [How to: Persist User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span></span>  
<span data-ttu-id="2eb09-143"> [方法: Visual Basic でのユーザー設定のプロパティ グリッドを作成します。](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="2eb09-143"> [How to: Create Property Grids for User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span></span>  
<span data-ttu-id="2eb09-144"> [アプリケーションの設定の管理 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)</span><span class="sxs-lookup"><span data-stu-id="2eb09-144"> [Managing Application Settings (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)</span></span>
