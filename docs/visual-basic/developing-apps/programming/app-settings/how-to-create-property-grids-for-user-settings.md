---
title: "方法 : Visual Basic でユーザー設定のためのプロパティ グリッドを作成する"
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
- My.Settings object, creating property grids for user settings
- user settings, creating property grids
- property grids, creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: 13
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
ms.openlocfilehash: c21b458f9c28f4d25e5b0d8099b9a5255f31ac52
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="5b530-102">方法 : Visual Basic でユーザー設定のためのプロパティ グリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="5b530-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="5b530-103"><xref:System.Windows.Forms.PropertyGrid> コントロールに `My.Settings` オブジェクトのユーザー設定プロパティを設定すると、ユーザー設定のためのプロパティ グリッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5b530-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b530-104">この例を使用するには、アプリケーションのユーザー設定を構成することが必要です。</span><span class="sxs-lookup"><span data-stu-id="5b530-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="5b530-105">詳細については、[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b530-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="5b530-106">`My.Settings` オブジェクトでは、各設定はプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="5b530-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="5b530-107">プロパティ名はその設定の名前と同じで、プロパティの型は設定の型と同じです。</span><span class="sxs-lookup"><span data-stu-id="5b530-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="5b530-108">プロパティが読み取り専用かどうかは、設定の**スコープ**でわかります。つまり、**アプリケーション**スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー**スコープの設定のプロパティは読み取り/書き込みです。</span><span class="sxs-lookup"><span data-stu-id="5b530-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="5b530-109">詳細については、「[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b530-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b530-110">アプリケーション スコープの設定値を実行時に変更または保存することはできません。</span><span class="sxs-lookup"><span data-stu-id="5b530-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="5b530-111">アプリケーション スコープの設定は、アプリケーションを作成するときに**プロジェクト デザイナー**を使用するか、アプリケーションの構成ファイルを編集するかのいずれかの方法でしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="5b530-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="5b530-112">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b530-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="5b530-113">この例では、<xref:System.Windows.Forms.PropertyGrid> コントロールを使用して、`My.Settings` オブジェクトのユーザー設定プロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="5b530-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="5b530-114">既定では、<xref:System.Windows.Forms.PropertyGrid> には `My.Settings` オブジェクトのすべてのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b530-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="5b530-115">一方、ユーザー設定プロパティは <xref:System.Configuration.UserScopedSettingAttribute> 属性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="5b530-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="5b530-116">この例では、<xref:System.Windows.Forms.PropertyGrid> の <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> プロパティを <xref:System.Configuration.UserScopedSettingAttribute> に設定して、ユーザー設定プロパティのみを表示します。</span><span class="sxs-lookup"><span data-stu-id="5b530-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="5b530-117">ユーザー設定のプロパティ グリッドを追加するには</span><span class="sxs-lookup"><span data-stu-id="5b530-117">To add a user setting property grid</span></span>  
  
1.  <span data-ttu-id="5b530-118">アプリケーションのデザイン サーフェイス (ここでは `Form1` とする) に、[**ツールボックス**] から [**PropertyGrid**] コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="5b530-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="5b530-119">プロパティ グリッド コントロールの既定の名前は `PropertyGrid1` です。</span><span class="sxs-lookup"><span data-stu-id="5b530-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2.  <span data-ttu-id="5b530-120">`Form1` のデザイン サーフェイスをダブルクリックして、フォーム読み込みのイベント ハンドラーのコードを開きます。</span><span class="sxs-lookup"><span data-stu-id="5b530-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3.  <span data-ttu-id="5b530-121">`My.Settings` オブジェクトをプロパティ グリッド用に選択されたオブジェクトとして設定します。</span><span class="sxs-lookup"><span data-stu-id="5b530-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     <span data-ttu-id="5b530-122">[!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5b530-122">[!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]</span></span>  
  
4.  <span data-ttu-id="5b530-123">ユーザー設定のみを表示するように、プロパティ グリッドを構成します。</span><span class="sxs-lookup"><span data-stu-id="5b530-123">Configure the property grid to show only the user settings.</span></span>  
  
     <span data-ttu-id="5b530-124">[!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5b530-124">[!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5b530-125">アプリケーション スコープの設定のみを表示するには、<xref:System.Configuration.UserScopedSettingAttribute> ではなく <xref:System.Configuration.ApplicationScopedSettingAttribute> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="5b530-125">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5b530-126">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="5b530-126">Robust Programming</span></span>  
 <span data-ttu-id="5b530-127">アプリケーションがユーザー設定を保存するのは、アプリケーションの終了時です。</span><span class="sxs-lookup"><span data-stu-id="5b530-127">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="5b530-128">設定をすぐに保存するには、`My.Settings.Save` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5b530-128">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="5b530-129">詳細については、「[方法: Visual Basic でユーザー設定を永続化する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b530-129">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b530-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b530-130">See Also</span></span>  
 <span data-ttu-id="5b530-131">[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md) </span><span class="sxs-lookup"><span data-stu-id="5b530-131">[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md) </span></span>  
 <span data-ttu-id="5b530-132">[方法: Visual Basic でアプリケーション設定を読み取る](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span><span class="sxs-lookup"><span data-stu-id="5b530-132">[How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span></span>  
 <span data-ttu-id="5b530-133">[方法: Visual Basic でユーザー設定を変更する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="5b530-133">[How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span></span>  
 <span data-ttu-id="5b530-134">[方法: Visual Basic でユーザー設定を永続化する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="5b530-134">[How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span></span>  
 [<span data-ttu-id="5b530-135">アプリケーションの設定の管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="5b530-135">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)

