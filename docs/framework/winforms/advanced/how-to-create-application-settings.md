---
title: "方法 : アプリケーション設定を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 481239b472ced5ef6251b665dad16e83a170607d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="6d1b8-102">方法 : アプリケーション設定を作成する</span><span class="sxs-lookup"><span data-stu-id="6d1b8-102">How to: Create Application Settings</span></span>
<span data-ttu-id="6d1b8-103">マネージ コードを使用することにより、新しいアプリケーション設定を作成し、フォームまたはフォームのコントロールのプロパティにバインドして、これらの設定が実行時に自動的に読み込まれて保存されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="6d1b8-104">次の手順では、<xref:System.Configuration.ApplicationSettingsBase> から派生するラッパー クラスを手動で作成します。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="6d1b8-105">このクラスには、公開する各アプリケーション設定に対して、パブリックにアクセスできるプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="6d1b8-106">また、Visual Studio デザイナーで最小限のコードを使用してこの手順を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="6d1b8-107">参照してください[する方法: アプリケーション設定を使用して作成デザイナー](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-107">Also see [How to: Create Application Settings Using the Designer](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="6d1b8-108">新しいアプリケーション設定をプログラムで作成するには</span><span class="sxs-lookup"><span data-stu-id="6d1b8-108">To create new Application Settings programmatically</span></span>  
  
1.  <span data-ttu-id="6d1b8-109">プロジェクトに新しいクラスを追加して、名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="6d1b8-110">この手順では、このクラスを呼び出して、`MyUserSettings`です。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="6d1b8-111">クラスの派生元が <xref:System.Configuration.ApplicationSettingsBase> になるようクラス定義を変更します。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2.  <span data-ttu-id="6d1b8-112">必要な各アプリケーション設定のこのラッパー クラスでプロパティを定義し、設定のスコープに応じて、そのプロパティを <xref:System.Configuration.ApplicationScopedSettingAttribute> または <xref:System.Configuration.UserScopedSettingAttribute> のいずれかを使用して適用します。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="6d1b8-113">設定のスコープの詳細については、次を参照してください。[アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-113">For more information about settings scope, see [Application Settings Overview](../../../../docs/framework/winforms/advanced/application-settings-overview.md).</span></span> <span data-ttu-id="6d1b8-114">ここまでで、コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  <span data-ttu-id="6d1b8-115">アプリケーションでこのラッパー クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="6d1b8-116">これは、一般的にはメイン フォームのプライベート メンバーです。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="6d1b8-117">クラスを定義したので、それをプロパティにバインドする必要があります。この場合は、フォームの <xref:System.Windows.Forms.Form.BackColor%2A> プロパティです。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="6d1b8-118">これを実現するには、フォームの `Load`イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="6d1b8-119">実行時に設定を変更する方法を提供する場合は、フォームを閉じるときにユーザーの現在の設定をディスクに保存する必要があります。そうしないと、これらの変更が失われます。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="6d1b8-120">これで、新しいアプリケーション設定を正常に作成し、指定されたプロパティにバインドしました。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6d1b8-121">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6d1b8-121">.NET Framework Security</span></span>  
 <span data-ttu-id="6d1b8-122">既定の設定プロバイダーの <xref:System.Configuration.LocalFileSettingsProvider> は、情報をプレーン テキストとして構成ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="6d1b8-123">これにより、セキュリティがオペレーティング システムが現在のユーザーに対して提供するファイル アクセスのセキュリティに制限されます。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="6d1b8-124">このため、構成ファイルに保存される情報に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="6d1b8-125">たとえば、アプリケーション設定の一般的な用途の 1 つとして、アプリケーションのデータ ストアをポイントする接続文字列を格納します。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="6d1b8-126">ただし、セキュリティの問題があるため、このような文字列にパスワードは含まれません。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="6d1b8-127">接続文字列の詳細については、「<xref:System.Configuration.SpecialSetting>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d1b8-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1b8-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d1b8-128">See Also</span></span>  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [<span data-ttu-id="6d1b8-129">アプリケーション設定の概要</span><span class="sxs-lookup"><span data-stu-id="6d1b8-129">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="6d1b8-130">方法: アプリケーション設定を検証する</span><span class="sxs-lookup"><span data-stu-id="6d1b8-130">How to: Validate Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
