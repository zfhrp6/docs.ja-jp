---
title: "操作方法: WCF Web サービス アプリケーションの WIF を有効にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 7db69de994770e122dd4a4233b9a44d572c32344
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a><span data-ttu-id="ddc67-102">操作方法: WCF Web サービス アプリケーションの WIF を有効にする</span><span class="sxs-lookup"><span data-stu-id="ddc67-102">How To: Enable WIF for a WCF Web Service Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="ddc67-103">対象</span><span class="sxs-lookup"><span data-stu-id="ddc67-103">Applies To</span></span>  
  
-   <span data-ttu-id="ddc67-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="ddc67-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="ddc67-105">Microsoft® Windows® Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="ddc67-105">Microsoft® Windows® Communication Foundation (WCF)</span></span>  
  
## <a name="summary"></a><span data-ttu-id="ddc67-106">概要</span><span class="sxs-lookup"><span data-stu-id="ddc67-106">Summary</span></span>  
 <span data-ttu-id="ddc67-107">ここでは、WCF Web サービスの WIF を有効にするための詳細な操作手順を示します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-107">This How-To provides detailed step-by-step procedures for enabling WIF in a WCF web service.</span></span> <span data-ttu-id="ddc67-108">また、アプリケーションの実行中に Web サービスが正しくクレームを表示しているかどうかを確認するためにアプリケーションをテストする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-108">It also provides instructions for how to test the application to verify that the web service is correctly presenting claims when the application is run.</span></span> <span data-ttu-id="ddc67-109">ここでは、セキュリティ トークン サービス (STS) を作成するための詳細な手順については説明しません。代わりに、Identity and Access Tool に付属している開発用 STS を使用します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="ddc67-110">開発用 STS はテスト用に用意されたもので、実際の認証は行いません。</span><span class="sxs-lookup"><span data-stu-id="ddc67-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="ddc67-111">このページの内容を完了するには、Identity and Access Tool をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddc67-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="ddc67-112">これは、「[Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="ddc67-113">目次</span><span class="sxs-lookup"><span data-stu-id="ddc67-113">Contents</span></span>  
  
-   <span data-ttu-id="ddc67-114">目的</span><span class="sxs-lookup"><span data-stu-id="ddc67-114">Objectives</span></span>  
  
-   <span data-ttu-id="ddc67-115">概要</span><span class="sxs-lookup"><span data-stu-id="ddc67-115">Overview</span></span>  
  
-   <span data-ttu-id="ddc67-116">手順の要約</span><span class="sxs-lookup"><span data-stu-id="ddc67-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ddc67-117">手順 1 – 簡単な WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="ddc67-117">Step 1 – Create a Simple WCF Service</span></span>  
  
-   <span data-ttu-id="ddc67-118">手順 2 – WCF サービスのクライアント アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="ddc67-118">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
-   <span data-ttu-id="ddc67-119">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="ddc67-119">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="ddc67-120">目的</span><span class="sxs-lookup"><span data-stu-id="ddc67-120">Objectives</span></span>  
  
-   <span data-ttu-id="ddc67-121">発行済みトークンを必要とする WCF サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="ddc67-121">Create a WCF service that requires issued tokens</span></span>  
  
-   <span data-ttu-id="ddc67-122">STS のトークンを要求し、それを WCF サービスに渡す WCF クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="ddc67-122">Create a WCF client that requests a token from an STS and passes it to the WCF service</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ddc67-123">概要</span><span class="sxs-lookup"><span data-stu-id="ddc67-123">Overview</span></span>  
 <span data-ttu-id="ddc67-124">ここでは、WCF サービス開発時に開発者がフェデレーション認証を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-124">This How-To is intended to demonstrate how a developer can use federated authentication when developing WCF services.</span></span> <span data-ttu-id="ddc67-125">WCF サービスでフェデレーションを使用する利点には、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-125">Some of the benefits of using federation in WCF services include:</span></span>  
  
1.  <span data-ttu-id="ddc67-126">WCF サービス コード外の認証ロジックのファクタリング</span><span class="sxs-lookup"><span data-stu-id="ddc67-126">Factoring authentication logic out of WCF service code</span></span>  
  
2.  <span data-ttu-id="ddc67-127">既存の ID 管理ソリューションの再利用</span><span class="sxs-lookup"><span data-stu-id="ddc67-127">Re-using existing identity management solutions</span></span>  
  
3.  <span data-ttu-id="ddc67-128">他の ID ソリューションとの相互運用性</span><span class="sxs-lookup"><span data-stu-id="ddc67-128">Interoperability with other identity solutions</span></span>  
  
4.  <span data-ttu-id="ddc67-129">今後の変更に対する柔軟性と回復力</span><span class="sxs-lookup"><span data-stu-id="ddc67-129">Flexibility and resilience to future changes</span></span>  
  
 <span data-ttu-id="ddc67-130">次の手順に示すように、WIF および関連する Identity and Access Tool を使用すると、フェデレーション認証を使用した WCF サービスの開発およびテストが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="ddc67-130">WIF and the associated Identity and Access tool make it easier to develop and test a WCF service using federated authentication, as the following steps demonstrate.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="ddc67-131">手順の要約</span><span class="sxs-lookup"><span data-stu-id="ddc67-131">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ddc67-132">手順 1 – 簡単な WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="ddc67-132">Step 1 – Create a Simple WCF Service</span></span>  
  
-   <span data-ttu-id="ddc67-133">手順 2 – WCF サービスのクライアント アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="ddc67-133">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
-   <span data-ttu-id="ddc67-134">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="ddc67-134">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-wcf-service"></a><span data-ttu-id="ddc67-135">手順 1 – 簡単な WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="ddc67-135">Step 1 – Create a Simple WCF Service</span></span>  
 <span data-ttu-id="ddc67-136">この手順では、Identity and Access Tool に付属している開発用 STS を使用する新しい WCF サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-136">In this step, you will create a new WCF service that uses the Development STS that is included with the Identity and Access tool.</span></span>  
  
#### <a name="to-create-a-simple-wcf-service"></a><span data-ttu-id="ddc67-137">簡単な WCF サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="ddc67-137">To create a simple WCF service</span></span>  
  
1.  <span data-ttu-id="ddc67-138">システム特権のあるモードで管理者として Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-138">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="ddc67-139">Visual Studio で、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-139">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="ddc67-140">**[新しいプロジェクト]** ウィンドウで、**[WCF サービス アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-140">In the **New Project** window, click **WCF Service Application**.</span></span>  
  
4.  <span data-ttu-id="ddc67-141">**[名前]** で、「`TestService`」と入力し、**[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-141">In **Name**, enter `TestService` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="ddc67-142">**ソリューション エクスプローラー**で **[TestService]** プロジェクトを右クリックし、**[Identity and Access]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-142">Right-click the **TestService** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="ddc67-143">**[Identity and Access]** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-143">The **Identity and Access** window appears.</span></span> <span data-ttu-id="ddc67-144">**[Providers]** で **[Test your application with the Local Development STS]** を選択し、**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-144">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span> <span data-ttu-id="ddc67-145">Identity and Access Tool は、サービスが WIF を使用し、*Web.config* ファイルに構成要素を追加することによって認証をローカル開発用の STS (**LocalSTS**) に外部委託するように構成します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-145">The Identity and Access Tool configures the service to use WIF and to outsource authentication to the local development STS (**LocalSTS**) by adding configuration elements to the *Web.config* file.</span></span>  
  
7.  <span data-ttu-id="ddc67-146">*Service1.svc.cs* ファイルで、**System.Security.Claims** 名前空間に `using` ディレクティブを追加し、既存のコードを次のコードに置き換え、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-146">In the *Service1.svc.cs* file, add a `using` directive for the **System.Security.Claims** namespace and replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    public class Service1 : IService1  
    {  
        public string ComputeResponse(string input)  
        {  
            // Get the caller's identity from ClaimsPrincipal.Current  
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;  
  
            // Start generating the output  
            StringBuilder builder = new StringBuilder();  
            builder.AppendLine("Computed by ClaimsAwareWebService");  
            builder.AppendLine("Input received from client:" + input);  
  
            if (claimsPrincipal != null)  
            {  
                // Display the claims from the caller. Do not use this code in a production application.  
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;  
                builder.AppendLine("Client Name:" + identity.Name);  
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);  
                builder.AppendLine("The service received the following issued claims of the client:");  
  
                // Iterate over the caller’s claims and append to the output  
                foreach (Claim claim in claimsPrincipal.Claims)  
                {  
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);  
                }  
            }  
  
            return builder.ToString();  
        }  
    }  
    ```  
  
     <span data-ttu-id="ddc67-147">`ComputeResponse` メソッドでは、**LocalSTS** が発行するさまざまなクレームのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-147">The `ComputeResponse` method displays the properties of various claims that are issued by **LocalSTS**.</span></span>  
  
8.  <span data-ttu-id="ddc67-148">*IService1.cs* ファイルでは、既存のコードを次のコードに置き換え、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-148">In the *IService1.cs* file, replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. <span data-ttu-id="ddc67-149">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-149">Build the project.</span></span>  
  
10. <span data-ttu-id="ddc67-150">デバッガーを起動せずにサービスを実行するには、**Ctrl-F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-150">Press **Ctrl-F5** to run the service without starting the debugger.</span></span> <span data-ttu-id="ddc67-151">Web ページが開き、サービスが表示されます。通知領域 (システム トレイ) を見ると、**LocalSTS** が実行中であることが確認できます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-151">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ddc67-152">次の手順でクライアント アプリケーションにサービス参照を追加するときに、**TestService** と **LocalSTS** の両方が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddc67-152">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client application in the next step.</span></span>  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a><span data-ttu-id="ddc67-153">手順 2 – WCF サービスのクライアント アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="ddc67-153">Step 2 – Create a Client Application for the WCF Service</span></span>  
 <span data-ttu-id="ddc67-154">この手順では、前の手順で作成した WCF サービスとの認証に開発用 STS を使用するコンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-154">In this step, you will create a console application that uses the Development STS to authenticate with the WCF service you created in the previous step.</span></span>  
  
#### <a name="to-create-a-client-application"></a><span data-ttu-id="ddc67-155">クライアント アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="ddc67-155">To create a client application</span></span>  
  
1.  <span data-ttu-id="ddc67-156">Visual Studio でソリューションを右クリックし、**[追加]** をクリックしてから **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-156">In Visual Studio, right-click on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="ddc67-157">**[新しいプロジェクトの追加]** ウィンドウで、**[Visual C#]** テンプレート一覧から **[コンソール アプリケーション]** を選択し、「`Client`」と入力して **[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-157">In the **Add New Project** window, select **Console Application** from the **Visual C#** templates list, enter `Client`, and then press **OK**.</span></span> <span data-ttu-id="ddc67-158">新しいプロジェクトがソリューション フォルダーに作成されます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-158">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="ddc67-159">**[Client]** プロジェクトの下の **[参照設定]** を右クリックし、**[サービス参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-159">Right-click on **References** under the **Client** project, and then click **Add Service Reference**.</span></span>  
  
4.  <span data-ttu-id="ddc67-160">**[サービス参照の追加]** ウィンドウで、**[探索]** ボタンのドロップダウン矢印をクリックし、**[ソリューションのサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-160">In the **Add Service Reference** window, click the drop-down arrow on the **Discover** button and click **Services in Solution**.</span></span> <span data-ttu-id="ddc67-161">**[アドレス]** には、前の手順で作成した WCF サービスが自動的に入力されます。**[名前空間]** は、**[ServiceReference1]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-161">The **Address** will automatically populate with the WCF service you created earlier, and the **Namespace** will be set to **ServiceReference1**.</span></span> <span data-ttu-id="ddc67-162">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-162">Click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ddc67-163">クライアントにサービス参照を追加するときに、**TestService** と **LocalSTS** の両方が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddc67-163">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client.</span></span>  
  
5.  <span data-ttu-id="ddc67-164">Visual Studio は、WCF サービスのプロキシ クラスを生成し、必要なリファレンス情報をすべて追加します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-164">Visual Studio will generate proxy classes for the WCF service, and add all of the necessary reference information.</span></span> <span data-ttu-id="ddc67-165">また、*App.config* ファイルに要素を追加して、サービスでの認証のために STS からトークンを取得するようにクライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-165">It will also add elements to the *App.config* file to configure the client to get a token from the STS to authenticate with the service.</span></span> <span data-ttu-id="ddc67-166">このプロセスが完了したら、**Program.cs** ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-166">When this process is finished, the **Program.cs** file will open.</span></span> <span data-ttu-id="ddc67-167">**System.ServiceModel** と **Client.ServiceReference1** それぞれに `using` ディレクティブを追加し、**Main** メソッドを次のコードに置き換えて、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-167">Add a `using` directive for **System.ServiceModel** and another for **Client.ServiceReference1**, replace the **Main** method with the following code, then save the file:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the client for the service  
        Service1Client client = new Service1Client();  
        Console.WriteLine("-------------WCF Client Application--------------\n");  
  
        while (!ShouldQuitApplication())  
        {  
            try  
            {  
                Console.WriteLine(client.ComputeResponse("Hello World"));  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
                Console.WriteLine(e.StackTrace);  
                Exception ex = e.InnerException;  
                while (ex != null)  
                {  
                    Console.WriteLine("===========================");  
                    Console.WriteLine(ex.Message);  
                    Console.WriteLine(ex.StackTrace);  
                    ex = ex.InnerException;  
                }  
            }  
            catch (TimeoutException)  
            {  
                Console.WriteLine("Timed out...");  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("An unexpected exception occurred.");  
                Console.WriteLine(e.StackTrace);  
            }  
        }  
  
        client.Close();  
  
        if (client != null)  
        {  
            client.Abort();  
        }  
    }  
  
    static bool ShouldQuitApplication()  
    {  
        Console.WriteLine("---------------------------------------------------------------------");  
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");  
        Console.WriteLine("----------------------------------------------------------------------");  
  
        ConsoleKeyInfo keyInfo = Console.ReadKey();  
        if (keyInfo.Key == ConsoleKey.Enter)  
            return false;  
        return true;  
    }  
    ```  
  
6.  <span data-ttu-id="ddc67-168">*App.config* ファイルを開き、`<system.serviceModel>` 要素の下に最初の子要素として次の XML を追加し、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-168">Open the *App.config* file and add the following XML as the first child element under the `<system.serviceModel>` element, then save the file:</span></span>  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
         <behavior>  
           <clientCredentials>  
             <serviceCertificate>  
               <authentication certificateValidationMode="None"/>  
             </serviceCertificate>  
           </clientCredentials>  
         </behavior>  
       </endpointBehaviors>  
     </behaviors>  
    ```  
  
     <span data-ttu-id="ddc67-169">これにより、証明書の検証が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ddc67-169">This disables certificate validation.</span></span>  
  
7.  <span data-ttu-id="ddc67-170">**[TestService]** ソリューションを右クリックし、**[スタートアップ プロジェクトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-170">Right-click the **TestService** solution and click on **Set StartUp Projects**.</span></span> <span data-ttu-id="ddc67-171">**[スタートアップ プロジェクト]** プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-171">The **Startup Project** property page opens.</span></span> <span data-ttu-id="ddc67-172">**[スタートアップ プロジェクト]** プロパティ ページで、**[マルチ スタートアップ プロジェクト]** を選択します。次に、各プロジェクトの **[アクション]** フィールドをクリックし、ドロップダウン メニューから **[開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-172">In the **Startup Project** property page, select **Multiple startup projects** then click in the **Action** field for each project and select **Start** from the drop-down menu.</span></span> <span data-ttu-id="ddc67-173">**[OK]** をクリックして設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-173">Click **OK** to save the settings.</span></span>  
  
8.  <span data-ttu-id="ddc67-174">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ddc67-174">Build the solution.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="ddc67-175">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="ddc67-175">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="ddc67-176">この手順では、WIF 対応 WCF アプリケーションをテストし、クレームが表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-176">In this step you will test your WIF-enabled WCF application and verify that claims are presented.</span></span>  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a><span data-ttu-id="ddc67-177">WIF 対応 WCF アプリケーションをテストしてクレームを確認するには</span><span class="sxs-lookup"><span data-stu-id="ddc67-177">To test your WIF-enabled WCF application for claims</span></span>  
  
1.  <span data-ttu-id="ddc67-178">**F5** キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="ddc67-178">Press **F5** to build and run the application.</span></span> <span data-ttu-id="ddc67-179">コンソール ウィンドウが開き、"**Press Enter key to invoke service, any other key to quit application:**" というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-179">You should be presented with a console window, and the following text: **Press Enter key to invoke service, any other key to quit application:**</span></span>  
  
2.  <span data-ttu-id="ddc67-180">**Enter** キーを押すと、コンソールに以下のクレーム情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-180">Press **Enter**, and the following claims information should appear in the console:</span></span>  
  
    ```  
    Computed by Service1  
    Input received from client: Hello World  
    Client Name: Terry  
    IsAuthenticated: True  
    The service received the following issued claims of the client:  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry  
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams  
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ddc67-181">**Enter** キーを押す前に **TestService** と **LocalSTS** の両方が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddc67-181">Both **TestService** and **LocalSTS** must be running before you press **Enter**.</span></span> <span data-ttu-id="ddc67-182">Web ページが開き、サービスが表示されます。通知領域 (システム トレイ) を見ると、**LocalSTS** が実行中であることが確認できます。</span><span class="sxs-lookup"><span data-stu-id="ddc67-182">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
3.  <span data-ttu-id="ddc67-183">これらのクレームがコンソールに表示されている場合、WCF サービスのクレームを表示するための STS での認証が正常に完了しています。</span><span class="sxs-lookup"><span data-stu-id="ddc67-183">If these claims appear in the console, you have successfully authenticated with the STS to display claims from the WCF service.</span></span>
