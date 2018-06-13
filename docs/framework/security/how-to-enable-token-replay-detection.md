---
title: '方法: トークン再生検出を有効にする'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b9c187998b4af41e1a56ed9a64625da7e4f95d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408061"
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="3dbfc-102">方法: トークン再生検出を有効にする</span><span class="sxs-lookup"><span data-stu-id="3dbfc-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="3dbfc-103">対象</span><span class="sxs-lookup"><span data-stu-id="3dbfc-103">Applies To</span></span>  
  
-   <span data-ttu-id="3dbfc-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="3dbfc-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="3dbfc-105">ASP.NET® Web フォーム</span><span class="sxs-lookup"><span data-stu-id="3dbfc-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="3dbfc-106">まとめ</span><span class="sxs-lookup"><span data-stu-id="3dbfc-106">Summary</span></span>  
 <span data-ttu-id="3dbfc-107">ここでは、WIF を使用する ASP.NET アプリケーションでトークン再生検出を有効にするための詳細な操作手順を示します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="3dbfc-108">トークン再生検出が有効になっていることを確認するためにアプリケーションをテストする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="3dbfc-109">ここでは、セキュリティ トークン サービス (STS) を作成するための詳細な手順については説明しません。代わりに、Identity and Access Tool に付属している開発用 STS を使用します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="3dbfc-110">開発用 STS はテスト用に用意されたもので、実際の認証は行いません。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="3dbfc-111">このページの内容を完了するには、Identity and Access Tool をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="3dbfc-112">これは、「[Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="3dbfc-113">目次</span><span class="sxs-lookup"><span data-stu-id="3dbfc-113">Contents</span></span>  
  
-   <span data-ttu-id="3dbfc-114">目的</span><span class="sxs-lookup"><span data-stu-id="3dbfc-114">Objectives</span></span>  
  
-   <span data-ttu-id="3dbfc-115">概要</span><span class="sxs-lookup"><span data-stu-id="3dbfc-115">Overview</span></span>  
  
-   <span data-ttu-id="3dbfc-116">手順の要約</span><span class="sxs-lookup"><span data-stu-id="3dbfc-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="3dbfc-117">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションの作成と再生検出の有効化</span><span class="sxs-lookup"><span data-stu-id="3dbfc-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="3dbfc-118">手順 2 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="3dbfc-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="3dbfc-119">目的</span><span class="sxs-lookup"><span data-stu-id="3dbfc-119">Objectives</span></span>  
  
-   <span data-ttu-id="3dbfc-120">Identity and Access Tool の WIF および開発用 STS を使用する簡単な ASP.NET アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="3dbfc-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="3dbfc-121">トークン再生検出の有効化と動作確認</span><span class="sxs-lookup"><span data-stu-id="3dbfc-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="3dbfc-122">概要</span><span class="sxs-lookup"><span data-stu-id="3dbfc-122">Overview</span></span>  
 <span data-ttu-id="3dbfc-123">再生攻撃は、クライアントが既に使用している STS トークンで証明書利用者に対する認証を試みた場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="3dbfc-124">この攻撃を防ぐために、WIF には、以前に使用された STS トークンの再生検出キャッシュが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="3dbfc-125">有効にすると、再生検出で受信要求のトークンがチェックされ、トークンが以前に使用されているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="3dbfc-126">トークンが既に使用されている場合、要求は拒否され、<xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="3dbfc-127">次の手順では、再生検出を有効にするために必要な構成の変更を示します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="3dbfc-128">手順の要約</span><span class="sxs-lookup"><span data-stu-id="3dbfc-128">Summary of Steps</span></span>  
  
-   <span data-ttu-id="3dbfc-129">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションの作成と再生検出の有効化</span><span class="sxs-lookup"><span data-stu-id="3dbfc-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="3dbfc-130">手順 2 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="3dbfc-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="3dbfc-131">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションの作成と再生検出の有効化</span><span class="sxs-lookup"><span data-stu-id="3dbfc-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="3dbfc-132">この手順では、新しい ASP.NET Web フォーム アプリケーションを作成し、再生検出を有効にするために *Web.config* ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="3dbfc-133">簡単な ASP.NET アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="3dbfc-133">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="3dbfc-134">Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="3dbfc-135">**[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="3dbfc-136">**[名前]** で、「`TestApp`」と入力し、**[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="3dbfc-137">**ソリューション エクスプローラー**で **[TestApp]** プロジェクトを右クリックし、**[Identity and Access]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="3dbfc-138">**[Identity and Access]** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="3dbfc-139">**[Providers]** で **[Test your application with the Local Development STS]** を選択し、**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="3dbfc-140">*Web.config* ファイルに、以下のように **\<system.identityModel>** および **\<identityConfiguration>** 要素のすぐ後に次の **\<tokenReplayDetection>** 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="3dbfc-141">手順 2 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="3dbfc-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="3dbfc-142">この手順では、WIF 対応 ASP.NET アプリケーションをテストし、再生検出が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="3dbfc-143">再生検出のために WIF 対応 ASP.NET アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="3dbfc-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1.  <span data-ttu-id="3dbfc-144">**F5** キーを押して、ソリューションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="3dbfc-145">既定の ASP.NET ホーム ページが開き、ユーザー名 *Terry* (開発用 STS によって返される既定のユーザー) で自動的に認証されます。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="3dbfc-146">ブラウザーの **[戻る]** ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="3dbfc-147">"**'/' アプリケーションでのサーバー エラー**" ページが表示され、"*ID1062: 再生が検出されました: トークン: 'System.IdentityModel.Tokens.SamlSecurityToken'*" という説明の後に *AssertionId* と*発行者*が続きます。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="3dbfc-148">このエラー ページが表示されるのは、トークン再生が検出されたときに <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 型の例外がスローされたためです。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="3dbfc-149">このエラーが発生するのは、トークンが最初に表示されたときに初期 POST 要求を再送信しようとしたためです。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="3dbfc-150">**[戻る]** ボタンを押しても、サーバーへの後続の要求でこのような動作にはなりません。</span><span class="sxs-lookup"><span data-stu-id="3dbfc-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
