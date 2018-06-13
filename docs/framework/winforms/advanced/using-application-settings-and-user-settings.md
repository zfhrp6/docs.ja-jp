---
title: アプリケーション設定とユーザー設定の使用
ms.date: 03/30/2017
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: f5231ecc9fb3898d60241ea8a53b509daced8a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523843"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="0392f-102">アプリケーション設定とユーザー設定の使用</span><span class="sxs-lookup"><span data-stu-id="0392f-102">Using Application Settings and User Settings</span></span>
<span data-ttu-id="0392f-103">.NET Framework 2.0 以降で作成し、アプリケーション実行セッション間で保持される値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0392f-103">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="0392f-104">これらの値と呼ばれる*設定*です。</span><span class="sxs-lookup"><span data-stu-id="0392f-104">These values are called *settings*.</span></span> <span data-ttu-id="0392f-105">設定は、ユーザー設定を表すことができるか、貴重な情報をアプリケーションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0392f-105">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="0392f-106">たとえば、一連のアプリケーションの画面の配色に関するユーザー設定を保存している設定を作成する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0392f-106">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="0392f-107">または、アプリケーションを使用するデータベースを指定する接続文字列を格納する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0392f-107">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="0392f-108">設定は、個々 のユーザーの設定を保存するプロファイルを作成して、コードの外部のアプリケーションにとって重要な情報を永続化両方を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0392f-108">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="0392f-109">このセクションのトピックでは、デザイン時の設定を使用して、時間を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0392f-109">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0392f-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0392f-110">In This Section</span></span>  
 [<span data-ttu-id="0392f-111">方法: 設計時に新しい設定を作成する</span><span class="sxs-lookup"><span data-stu-id="0392f-111">How To: Create a New Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="0392f-112">Visual Studio を使用して、アプリケーションの新しい設定を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0392f-112">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="0392f-113">方法: 設計時に既存の設定の値を変更する</span><span class="sxs-lookup"><span data-stu-id="0392f-113">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="0392f-114">Visual Studio を使用して、既存の設定の値を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0392f-114">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="0392f-115">方法: アプリケーション セッション間で設定値を変更する</span><span class="sxs-lookup"><span data-stu-id="0392f-115">How To: Change the Value of a Setting Between Application Sessions</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="0392f-116">アプリケーション セッション間でコンパイル済みのアプリケーション設定の値を変更する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="0392f-116">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="0392f-117">方法: 実行時に設定を C# で読み取る</span><span class="sxs-lookup"><span data-stu-id="0392f-117">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="0392f-118">C# を使用して設定を読み込むコードを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0392f-118">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="0392f-119">方法: 実行時にユーザー設定を C# で書き込む</span><span class="sxs-lookup"><span data-stu-id="0392f-119">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="0392f-120">コードを使用して作成し、c# を使用してユーザー設定の値を保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0392f-120">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="0392f-121">方法: C# のアプリケーションに複数の設定セットを追加する</span><span class="sxs-lookup"><span data-stu-id="0392f-121">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="0392f-122">C# のアプリケーションに複数セットの設定を追加する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="0392f-122">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0392f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0392f-123">See Also</span></span>  
 [<span data-ttu-id="0392f-124">Windows フォームのアプリケーション設定</span><span class="sxs-lookup"><span data-stu-id="0392f-124">Application Settings for Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/application-settings-for-windows-forms.md)
