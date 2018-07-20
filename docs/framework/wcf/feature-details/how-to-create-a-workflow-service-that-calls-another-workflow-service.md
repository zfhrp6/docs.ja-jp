---
title: '方法: 別のワークフロー サービスを呼び出すワークフロー サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: fda5a7286c3d20c7cdc2093e58bfe3fbdcf1d1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497192"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a><span data-ttu-id="19d54-102">方法: 別のワークフロー サービスを呼び出すワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="19d54-102">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>
<span data-ttu-id="19d54-103">ワークフロー サービスでは、別のワークフロー サービスから情報を取得することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="19d54-103">It is sometimes necessary for a workflow service to obtain information from another workflow service.</span></span>  <span data-ttu-id="19d54-104">このトピックでは、別のワークフロー サービスからワークフロー サービスを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="19d54-104">This topic demonstrates how to call one workflow service from another.</span></span> <span data-ttu-id="19d54-105">このトピックでは、2 つのワークフロー サービスを作成します。入力文字列を反転させるメソッドを持つワークフロー サービスと、その最初のサービスを使用して文字列を反転させた後、入力文字列を大文字に変換するワークフロー サービスです。</span><span class="sxs-lookup"><span data-stu-id="19d54-105">In this topic, we’ll create two workflow services; one that has a method that reverses the input string, and another that converts the input string to uppercase after reversing the string that uses the first service.</span></span>  
  
### <a name="to-create-the-reverser-workflow-service"></a><span data-ttu-id="19d54-106">Reverser ワークフロー サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="19d54-106">To create the Reverser workflow service</span></span>  
  
1.  <span data-ttu-id="19d54-107">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を管理者として実行します。</span><span class="sxs-lookup"><span data-stu-id="19d54-107">Run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] as an administrator.</span></span>  
  
2.  <span data-ttu-id="19d54-108">選択**ファイル**、**新しいプロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-108">Select **File**, **New Project**.</span></span> <span data-ttu-id="19d54-109">下にある、**ワークフロー**内のノード、**インストールされたテンプレート**ペインで、 **WCF ワークフロー サービス アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-109">Under the **Workflow** node in the **Installed Templates** pane, select **WCF Workflow Service Application**.</span></span> <span data-ttu-id="19d54-110">ソリューションの名前を付けます`NestedServices` をクリックし、 **ok**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-110">Name the solution `NestedServices` and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="19d54-111">**サーバー**、ことを確認して**ローカル IIS Web サーバー**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="19d54-111">Under **Servers**, make sure that **Use Local IIS Web Server** is selected.</span></span> <span data-ttu-id="19d54-112">をクリックして**仮想ディレクトリを作成**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-112">Click **Create Virtual Directory**.</span></span> <span data-ttu-id="19d54-113">をクリックして**OK**仮想ディレクトリが正常に作成されたことを示すダイアログ ボックスでします。</span><span class="sxs-lookup"><span data-stu-id="19d54-113">Click **OK** in the dialog box stating that the virtual directory was successfully created.</span></span>  
  
4.  <span data-ttu-id="19d54-114">ソリューション エクスプ ローラーで、名前を変更する Service1.xamlx`StringReverserService.xamlx`です。</span><span class="sxs-lookup"><span data-stu-id="19d54-114">In Solution Explorer, rename Service1.xamlx to `StringReverserService.xamlx`.</span></span>  
  
5.  <span data-ttu-id="19d54-115">**プロジェクト プロパティ**、新しいプロジェクトのページで、をクリックして、 **Web**タブです。設定、**開始動作**に**特定のページ**StringReverserService.xamlx を開始するページとしてを選択します。</span><span class="sxs-lookup"><span data-stu-id="19d54-115">On the **Project Properties** page for the new project, click the **Web** tab. Set the **Start Action** to **Specific Page**, and select StringReverserService.xamlx as the page to start.</span></span>  
  
6.  <span data-ttu-id="19d54-116">デザイナーで StringReverserService.xamlx を開いて、既存の `ReceiveRequest` アクティビティおよび `SendReply` アクティビティを削除し、`ReceiveAndSendReply` アクティビティを既存のシーケンス アクティビティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="19d54-116">Open StringReverserService.xamlx in the designer and delete the existing `ReceiveRequest` and `SendReply` activities, and then drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="19d54-117">設定、 **OperationName** ReverseString にします。</span><span class="sxs-lookup"><span data-stu-id="19d54-117">Set the **OperationName** to ReverseString.</span></span>  
  
    2.  <span data-ttu-id="19d54-118">設定、 **ServiceContractName** [ireversestring] にします。</span><span class="sxs-lookup"><span data-stu-id="19d54-118">Set the **ServiceContractName** to IReverseString.</span></span>  
  
    3.  <span data-ttu-id="19d54-119">選択、 **CanCreateInstance**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="19d54-119">Select the **CanCreateInstance** check box.</span></span>  
  
7.  <span data-ttu-id="19d54-120">選択、 **SequentialService**クリックして、アクティビティ、**変数**デザイナーの下部にあるタブ。</span><span class="sxs-lookup"><span data-stu-id="19d54-120">Select the **SequentialService** activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="19d54-121">StringToReverse と ReversedStringToReturn という文字列型の 2 つの新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="19d54-121">Create two new variables named StringToReverse and ReversedStringToReturn of type String.</span></span>  
  
8.  <span data-ttu-id="19d54-122">クリックして、**定義**内のリンク、**受信**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="19d54-122">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="19d54-123">クリックして、**パラメーター**、型 String StringToReverse に代入する InputString というパラメーターを作成します。</span><span class="sxs-lookup"><span data-stu-id="19d54-123">Click the  **Parameters**, and create a parameter named InputString of type String that assigns to StringToReverse.</span></span>  
  
9. <span data-ttu-id="19d54-124">クリックして、**定義**内のリンク、 **SendReplyToReceive**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="19d54-124">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="19d54-125">クリックして、**パラメーター**文字列の型、ReversedStringToReturn に代入される ReversedString というパラメーターを作成します。</span><span class="sxs-lookup"><span data-stu-id="19d54-125">Click the **Parameters**, and create a parameter named ReversedString of type String, assigned to ReversedStringToReturn.</span></span>  
  
10. <span data-ttu-id="19d54-126">サービスのロジックを実装するには、StringLibrary というプロジェクトで新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="19d54-126">To implement the logic for the service, create a new class in the project called StringLibrary.</span></span>  <span data-ttu-id="19d54-127">クラスの定義を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="19d54-127">Replace the class definition with the following code.</span></span>  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. <span data-ttu-id="19d54-128">入力で ReverseString メソッドを呼び出すには、ドラッグ、 **InvokeMethod**間の空白にアクティビティをツールボックス、**受信**と**SendReply**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="19d54-128">To call the ReverseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="19d54-129">アクティビティのプロパティを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="19d54-129">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="19d54-130">**MethodName**: ReverseString</span><span class="sxs-lookup"><span data-stu-id="19d54-130">**MethodName**: ReverseString</span></span>  
  
    2.  <span data-ttu-id="19d54-131">**結果**: ReversedStringToReturn</span><span class="sxs-lookup"><span data-stu-id="19d54-131">**Result**: ReversedStringToReturn</span></span>  
  
    3.  <span data-ttu-id="19d54-132">**パラメーター**: 新しいパラメーターを作成、**方向**で、**型**文字列の**値**StringToReverse のです。</span><span class="sxs-lookup"><span data-stu-id="19d54-132">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToReverse.</span></span>  
  
    4.  <span data-ttu-id="19d54-133">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="19d54-133">**TargetType**: NestedServices.StringLibrary</span></span>  
  
12. <span data-ttu-id="19d54-134">F5 キーを押して、サービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="19d54-134">Test the service by pressing F5.</span></span> <span data-ttu-id="19d54-135">表示される [WCF テスト クライアント] で、ReverseString() メソッドをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="19d54-135">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="19d54-136">要求ペインで、次のように入力します。 `Sample` 、InputString パラメーターの値。</span><span class="sxs-lookup"><span data-stu-id="19d54-136">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="19d54-137">をクリックして**呼び出す**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-137">Click **Invoke**.</span></span> <span data-ttu-id="19d54-138">サービスにより "elpmaS" が返されます。</span><span class="sxs-lookup"><span data-stu-id="19d54-138">The service should return "elpmaS".</span></span>  
  
### <a name="to-create-the-uppercaser-workflow-service"></a><span data-ttu-id="19d54-139">UpperCaser ワークフロー サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="19d54-139">To create the UpperCaser workflow service</span></span>  
  
1.  <span data-ttu-id="19d54-140">NestedServices プロジェクトを右クリックし **追加**、**新しい項目の**します。</span><span class="sxs-lookup"><span data-stu-id="19d54-140">Right-click the NestedServices project and select **Add**, **New Item**.</span></span> <span data-ttu-id="19d54-141">**ワークフロー**ノード、 **WCF ワークフロー サービス**、新しいサービスの名前と`UpperCaserService`です。</span><span class="sxs-lookup"><span data-stu-id="19d54-141">In the **Workflow** node, select **WCF Workflow Service**, and name the new service `UpperCaserService`.</span></span> <span data-ttu-id="19d54-142">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19d54-142">Click **Add**.</span></span> <span data-ttu-id="19d54-143">これにより、UpperCaserService.xamlx という新しいワークフロー サービスがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="19d54-143">This should add a new workflow service called UpperCaserService.xamlx to the project.</span></span>  
  
2.  <span data-ttu-id="19d54-144">デザイナーで UpperCaserService.xamlx を開いて、既存の削除**ReceiveRequest**と`SendReply`アクティビティ、およびドラッグ、`ReceiveAndSendReply`アクティビティを既存のシーケンス アクティビティにします。</span><span class="sxs-lookup"><span data-stu-id="19d54-144">Open UpperCaserService.xamlx in the designer and delete the existing **ReceiveRequest** and `SendReply` activities, and drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="19d54-145">設定、 **OperationName** UpperCaseString にします。</span><span class="sxs-lookup"><span data-stu-id="19d54-145">Set the **OperationName** to UpperCaseString.</span></span>  
  
    2.  <span data-ttu-id="19d54-146">設定、 **ServiceContractName** [iuppercasestring] にします。</span><span class="sxs-lookup"><span data-stu-id="19d54-146">Set the **ServiceContractName** to IUpperCaseString.</span></span>  
  
    3.  <span data-ttu-id="19d54-147">選択、 **CanCreateInstance**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="19d54-147">Select the **CanCreateInstance** check box.</span></span>  
  
3.  <span data-ttu-id="19d54-148">SequentialService アクティビティを選択し、クリックして、**変数**デザイナーの下部にあるタブ。</span><span class="sxs-lookup"><span data-stu-id="19d54-148">Select the SequentialService activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="19d54-149">StringToUpper、StringToReverse、StringToReturn という文字列型の 3 つの新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="19d54-149">Create three new variables named StringToUpper, StringToReverse, and StringToReturn of type String.</span></span>  
  
4.  <span data-ttu-id="19d54-150">クリックして、**定義**内のリンク、**受信**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="19d54-150">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="19d54-151">クリックして、**パラメーター**、型 String StringToUpper に代入する InputString というパラメーターを作成します。</span><span class="sxs-lookup"><span data-stu-id="19d54-151">Click the **Parameters**, and create a parameter named InputString of type String that assigns to StringToUpper.</span></span>  
  
5.  <span data-ttu-id="19d54-152">クリックして、**定義**内のリンク、 **SendReplyToReceive**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="19d54-152">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="19d54-153">クリックして、**パラメーター**文字列型の StringToReturn に代入される ModifiedString というパラメーターを作成します。</span><span class="sxs-lookup"><span data-stu-id="19d54-153">Click the **Parameters**, and create a parameter named ModifiedString of type String, assigned to StringToReturn.</span></span>  
  
6.  <span data-ttu-id="19d54-154">サービスのロジックを実装するには、次のコードを使用して、StringLibrary クラスで新しいメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="19d54-154">To implement the logic for the service, create a new method in the StringLibrary class using the following code.</span></span>  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  <span data-ttu-id="19d54-155">入力で UpperCaseString メソッドを呼び出すには、ドラッグ、 **InvokeMethod**間の空白にアクティビティをツールボックス、**受信**と**SendReply**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="19d54-155">To call the UpperCaseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="19d54-156">アクティビティのプロパティを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="19d54-156">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="19d54-157">**MethodName**: UpperCaseString</span><span class="sxs-lookup"><span data-stu-id="19d54-157">**MethodName**: UpperCaseString</span></span>  
  
    2.  <span data-ttu-id="19d54-158">**結果**: StringToReverse</span><span class="sxs-lookup"><span data-stu-id="19d54-158">**Result**: StringToReverse</span></span>  
  
    3.  <span data-ttu-id="19d54-159">**パラメーター**: 新しいパラメーターを作成、**方向**で、**型**文字列の**値**StringToUpper のです。</span><span class="sxs-lookup"><span data-stu-id="19d54-159">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToUpper.</span></span>  
  
    4.  <span data-ttu-id="19d54-160">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="19d54-160">**TargetType**: NestedServices.StringLibrary</span></span>  
  
8.  <span data-ttu-id="19d54-161">ここで、修正済みの文字列で最初のサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="19d54-161">We’ll now call the first service on the modified string.</span></span> <span data-ttu-id="19d54-162">プロジェクトを右クリックし **サービス参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-162">Right-click the project and select **Add Service Reference**.</span></span> <span data-ttu-id="19d54-163">サービスにサービス参照の追加 http://localhost/NestedServices/StringReverserService.xamlx 最初の Web サービスにアクセスするカスタム アクティビティを作成するプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="19d54-163">Add a service reference to the service at http://localhost/NestedServices/StringReverserService.xamlx and build the project to create a custom activity to access the first Web service.</span></span>  
  
9. <span data-ttu-id="19d54-164">新しいアクティビティのインスタンス、ワークフローにドラッグ間、 **InvokeMethod**アクティビティおよび**SendReplyToReceive**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="19d54-164">Drag an instance of the new activity onto the workflow, between the **InvokeMethod** activity and the **SendReplyToReceive** activities.</span></span> <span data-ttu-id="19d54-165">変数 StringToReverse を新しいアクティビティの InputString プロパティに、変数 StringToReturn を StringToReturn プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="19d54-165">Assign the variable StringToReverse to the InputString property of the new activity, and the variable StringToReturn to the StringToReturn property.</span></span>  
  
10. <span data-ttu-id="19d54-166">NestedServices プロジェクトのプロパティ ページを開き、変更、**特定ページ**で、 **Web**を UpperCaserService.xamlx にタブです。</span><span class="sxs-lookup"><span data-stu-id="19d54-166">Open the Properties page for the NestedServices project, and change the **Specific Page** in the **Web** tab to UpperCaserService.xamlx.</span></span>  
  
11. <span data-ttu-id="19d54-167">F5 キーを押して、サービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="19d54-167">Test the service by pressing F5.</span></span> <span data-ttu-id="19d54-168">表示される [WCF テスト クライアント] で、ReverseString() メソッドをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="19d54-168">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="19d54-169">要求ペインで、次のように入力します。 `Sample` 、InputString パラメーターの値。</span><span class="sxs-lookup"><span data-stu-id="19d54-169">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="19d54-170">をクリックして**呼び出す**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-170">Click **Invoke**.</span></span> <span data-ttu-id="19d54-171">サービスにより "ELPMAS" が返されます。</span><span class="sxs-lookup"><span data-stu-id="19d54-171">The service should return "ELPMAS".</span></span>  
  
### <a name="to-create-a-client-to-call-the-services"></a><span data-ttu-id="19d54-172">サービスを呼び出すクライアントを作成するには</span><span class="sxs-lookup"><span data-stu-id="19d54-172">To create a client to call the services</span></span>  
  
1.  <span data-ttu-id="19d54-173">クライアントという新しいコンソール アプリケーション プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="19d54-173">Add a new Console application project called Client to the solution.</span></span>  
  
2.  <span data-ttu-id="19d54-174">クライアント プロジェクトを右クリックし **サービス参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-174">Right-click the Client project and select **Add Service Reference**.</span></span> <span data-ttu-id="19d54-175">表示されるウィンドウで  **Discover**です。</span><span class="sxs-lookup"><span data-stu-id="19d54-175">In the window that appears, click **Discover**.</span></span> <span data-ttu-id="19d54-176">StringReverserService.xamlx を選択し、名前空間として「ReverseService」と入力します。</span><span class="sxs-lookup"><span data-stu-id="19d54-176">Select StringReverserService.xamlx, and enter ReverseService as the namespace.</span></span>  <span data-ttu-id="19d54-177">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19d54-177">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="19d54-178">Program.cs の Main メソッドを次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="19d54-178">Replace the Main method in Program.cs with the following code.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
