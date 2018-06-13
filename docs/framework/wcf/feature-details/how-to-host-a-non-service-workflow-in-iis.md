---
title: '方法 : IIS でサービス以外のワークフローをホストする'
ms.date: 03/30/2017
ms.assetid: f362562c-767d-401b-8257-916616568fd4
ms.openlocfilehash: 70fd6aca94f2addd7ee568e897171ae1da86db67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496759"
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a><span data-ttu-id="4999b-102">方法 : IIS でサービス以外のワークフローをホストする</span><span class="sxs-lookup"><span data-stu-id="4999b-102">How to: Host a non-service workflow in IIS</span></span>
<span data-ttu-id="4999b-103">ワークフロー サービスではないワークフローは IIS/WAS でホストできます。</span><span class="sxs-lookup"><span data-stu-id="4999b-103">Workflows that are not workflow services can be hosted under IIS/WAS.</span></span> <span data-ttu-id="4999b-104">これは他の人が作成したワークフローをホストする必要がある場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="4999b-104">This is useful when you need to host a workflow written by somebody else.</span></span> <span data-ttu-id="4999b-105">たとえば、ワークフロー デザイナーを再ホストして、ユーザーが独自のワークフローを作成できるようにする場合がその例です。</span><span class="sxs-lookup"><span data-stu-id="4999b-105">For example, if you rehost the workflow designer and allow users to create their own workflows.</span></span>  <span data-ttu-id="4999b-106">IIS でサービス以外のワークフローをホストすると、プロセス リサイクル、アイドル シャットダウン、処理状況の監視、メッセージ ベースのアクティブ化などの機能をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="4999b-106">Hosting non-service workflows in IIS provides support for features like process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="4999b-107">IIS でホストされるワークフロー サービスには <xref:System.ServiceModel.Activities.Receive> アクティビティが含まれ、IIS がメッセージを受け取るとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="4999b-107">Workflow services hosted in IIS contain <xref:System.ServiceModel.Activities.Receive> activities and are activated when a message is received by IIS.</span></span> <span data-ttu-id="4999b-108">サービス以外のワークフローにはメッセージング アクティビティは含まれないので、既定ではメッセージを送信することによってアクティブ化できません。</span><span class="sxs-lookup"><span data-stu-id="4999b-108">Non-service workflows do not contain messaging activities, and by default cannot be activated by sending a message.</span></span>  <span data-ttu-id="4999b-109"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> からクラスを派生させ、そのワークフローのインスタンスを作成する操作を含むサービス コントラクトを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4999b-109">You must derive a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> and define a service contract that contains operations to create an instance of the workflow.</span></span> <span data-ttu-id="4999b-110">このトピックでは、手順、単純なワークフローを作成、クライアントが、ワークフローをアクティブ化に使用できるサービス コントラクトを定義およびからクラスを派生する<xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>ワークフロー作成のリクエストをリッスンするように、サービス コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="4999b-110">This topic will walk you through creating a simple workflow, defining a service contract a client can use to activate the workflow, and deriving a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> which uses the service contract to listen for workflow creating requests.</span></span>  
  
### <a name="create-a-simple-workflow"></a><span data-ttu-id="4999b-111">単純なワークフローの作成</span><span class="sxs-lookup"><span data-stu-id="4999b-111">Create a simple workflow</span></span>  
  
1.  <span data-ttu-id="4999b-112">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] という名前で、新しい空の `CreationEndpointTest` ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4999b-112">Create a new [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] empty solution called `CreationEndpointTest`.</span></span>  
  
2.  <span data-ttu-id="4999b-113">`SimpleWorkflow` という新しい WCF ワークフロー サービス アプリケーション プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-113">Add a new WCF Workflow Service Application project called `SimpleWorkflow` to the solution.</span></span> <span data-ttu-id="4999b-114">ワークフロー デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="4999b-114">The workflow designer will open.</span></span>  
  
3.  <span data-ttu-id="4999b-115">ReceiveRequest アクティビティと SendResponse アクティビティを削除します。</span><span class="sxs-lookup"><span data-stu-id="4999b-115">Delete the ReceiveRequest and SendResponse activities.</span></span> <span data-ttu-id="4999b-116">ワークフローはこれらのアクティビティによってワークフロー サービスになります。</span><span class="sxs-lookup"><span data-stu-id="4999b-116">These activities are what makes a workflow a workflow service.</span></span> <span data-ttu-id="4999b-117">ここではワークフロー サービスを使用しないので、これらのアクティビティは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4999b-117">Since we are not working with a workflow service, we no longer need them.</span></span>  
  
4.  <span data-ttu-id="4999b-118">DisplayName を"Sequential Workflow"にシーケンス アクティビティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4999b-118">Set the DisplayName for the sequence activity to "Sequential Workflow".</span></span>  
  
5.  <span data-ttu-id="4999b-119">Service1.xamlx を Workflow1.xamlx という名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="4999b-119">Rename Service1.xamlx to Workflow1.xamlx.</span></span>  
  
6.  <span data-ttu-id="4999b-120">シーケンス アクティビティの外でデザイナーをクリックし、Name プロパティと ConfigurationName プロパティを"Workflow1"に設定</span><span class="sxs-lookup"><span data-stu-id="4999b-120">Click the designer outside of the sequence activity, and set the Name and ConfigurationName properties to "Workflow1"</span></span>  
  
7.  <span data-ttu-id="4999b-121"><xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4999b-121">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence>.</span></span> <span data-ttu-id="4999b-122"><xref:System.Activities.Statements.WriteLine>アクティビティは含まれて、**プリミティブ**ツールボックスのセクションです。</span><span class="sxs-lookup"><span data-stu-id="4999b-122">The <xref:System.Activities.Statements.WriteLine> activity can be found in the **Primitives** section of the toolbox.</span></span> <span data-ttu-id="4999b-123">設定、<xref:System.Activities.Statements.WriteLine.Text%2A>のプロパティ、<xref:System.Activities.Statements.WriteLine>アクティビティに「こんにちは, world」です。</span><span class="sxs-lookup"><span data-stu-id="4999b-123">Set the <xref:System.Activities.Statements.WriteLine.Text%2A> property of the <xref:System.Activities.Statements.WriteLine> activity to "Hello, world".</span></span>  
  
     <span data-ttu-id="4999b-124">この時点で、ワークフローは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="4999b-124">The workflow should now look like the following diagram.</span></span>  
  
     <span data-ttu-id="4999b-125">![単純なワークフロー](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span><span class="sxs-lookup"><span data-stu-id="4999b-125">![A simple workflow](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span></span>  
  
### <a name="create-the-workflow-creation-service-contract"></a><span data-ttu-id="4999b-126">ワークフロー作成サービス コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="4999b-126">Create the workflow creation service contract</span></span>  
  
1.  <span data-ttu-id="4999b-127">`Shared` に `CreationEndpointTest` という新しいクラス ライブラリ プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-127">Add a new class library project called `Shared` to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="4999b-128">System.ServiceModel.dll、System.Configuration、および System.ServiceModel.Activities への参照を `Shared` プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-128">Add a reference to System.ServiceModel.dll, System.Configuration, and System.ServiceModel.Activities to the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="4999b-129">Class1.cs ファイルの名前を IWorkflowCreation.cs に変更し、次のコードをそのファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-129">Rename the Class1.cs file to IWorkflowCreation.cs and the following code to the file.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     <span data-ttu-id="4999b-130">このコントラクトは 2 つの操作を定義します。どちらも作成したサービス以外のワークフローの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4999b-130">This contract defines two operations both create a new instance of the non-service workflow you just created.</span></span> <span data-ttu-id="4999b-131">1 つは生成されたインスタンス ID を持つ新しいインスタンスを作成し、もう 1 つは新しいワークフロー インスタンスのインスタンス ID を指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4999b-131">One creates a new instance with a generated instance ID and the other allows you to specify the instance ID for the new workflow instance.</span></span>  <span data-ttu-id="4999b-132">どちらの方法でも、新しいワークフロー インスタンスにパラメーターを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4999b-132">Both methods allow you to pass in parameters to the new workflow instance.</span></span> <span data-ttu-id="4999b-133">このコントラクトによって公開される、<xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>にクライアントがサービス以外のワークフローの新しいインスタンスを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4999b-133">This contract will be exposed by the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to allow clients to create new instances of a non-service workflow.</span></span>  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a><span data-ttu-id="4999b-134">WorkflowHostingEndpoint からのクラスの派生</span><span class="sxs-lookup"><span data-stu-id="4999b-134">Derive a class from WorkflowHostingEndpoint</span></span>  
  
1.  <span data-ttu-id="4999b-135">いう新しいクラスを追加`CreationEndpoint`から派生した<xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>を`Shared`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="4999b-135">Add a new class called `CreationEndpoint` derived from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to the `Shared` project.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="4999b-136"><xref:System.Uri> というローカルの静的 `defaultBaseUri` 変数を `CreationEndpoint` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-136">Add a local static <xref:System.Uri> variable called `defaultBaseUri` to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  <span data-ttu-id="4999b-137">`CreationEndpoint` クラスに次のコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-137">Add the following constructor to the `CreationEndpoint` class.</span></span> <span data-ttu-id="4999b-138">基本コンストラクターへの呼び出しに `IWorkflowCreation` サービス コントラクトを指定することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4999b-138">Notice we specify the `IWorkflowCreation` service contract in the call to the base constructor.</span></span>  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  <span data-ttu-id="4999b-139">`CreationEndpoint` クラスに次の既定のコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-139">Add the following default constructor to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  <span data-ttu-id="4999b-140">`DefaultBaseUri` という静的プロパティを `CreationEndpoint` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-140">Add a static `DefaultBaseUri` property to the `CreationEndpoint` class.</span></span> <span data-ttu-id="4999b-141">このプロパティは既定のベース URI の保持に使用されます (指定されない場合)。</span><span class="sxs-lookup"><span data-stu-id="4999b-141">This property will be used to hold a default base URI if one is not provided.</span></span>  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  <span data-ttu-id="4999b-142">作成エンドポイントに使用する既定のバインディングを取得するための次のメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="4999b-142">Create the following method to get the default binding to use for the creation endpoint.</span></span>  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  <span data-ttu-id="4999b-143"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> メソッドをオーバーライドしてワークフロー インスタンス ID を返します。</span><span class="sxs-lookup"><span data-stu-id="4999b-143">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> method to return the workflow instance ID.</span></span> <span data-ttu-id="4999b-144">場合、`Action`場合、ヘッダーが"Create"では空の GUID を返します、`Action`ヘッダーが"CreateWithInstanceId"return メソッドに渡す GUID で終了します。</span><span class="sxs-lookup"><span data-stu-id="4999b-144">If the `Action` header ends with "Create" return an empty GUID, if the `Action` header ends with "CreateWithInstanceId" return the GUID passed into the method.</span></span> <span data-ttu-id="4999b-145">それ以外の場合は、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4999b-145">Otherwise, throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="4999b-146">これらの `Action` ヘッダーは `IWorkflowCreation` サービス コントラクトで定義した 2 つの操作に対応しています。</span><span class="sxs-lookup"><span data-stu-id="4999b-146">These `Action` headers correspond to the two operations defined in the `IWorkflowCreation` service contract.</span></span>  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  <span data-ttu-id="4999b-147"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> メソッドをオーバーライドして <xref:System.ServiceModel.Activities.WorkflowCreationContext> を作成し、ワークフローに引数があれば追加し、クライアントにインスタンス ID を送信して、<xref:System.ServiceModel.Activities.WorkflowCreationContext> を返します。</span><span class="sxs-lookup"><span data-stu-id="4999b-147">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> method to create a <xref:System.ServiceModel.Activities.WorkflowCreationContext> and add any arguments for the workflow, send the instance ID to the client, and then return the <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span></span>  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a><span data-ttu-id="4999b-148">WorkflowCreationEndpoint の構成を可能にする標準エンドポイント要素の作成</span><span class="sxs-lookup"><span data-stu-id="4999b-148">Create a standard endpoint element to allow you to configure the WorkflowCreationEndpoint</span></span>  
  
1.  <span data-ttu-id="4999b-149">`CreationEndpoint` プロジェクトの Shared への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-149">Add a reference to Shared in the `CreationEndpoint` project</span></span>  
  
2.  <span data-ttu-id="4999b-150">`CreationEndpointElement` という <xref:System.ServiceModel.Configuration.StandardEndpointElement> から派生された新しいクラスを `CreationEndpoint` プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-150">Add a new class called `CreationEndpointElement`, derived from <xref:System.ServiceModel.Configuration.StandardEndpointElement> to the `CreationEndpoint` project.</span></span> <span data-ttu-id="4999b-151">このクラスは web.config ファイル内の `CreationEndpoint` を表します。</span><span class="sxs-lookup"><span data-stu-id="4999b-151">This class will represent a `CreationEndpoint` in a web.config file.</span></span>  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  <span data-ttu-id="4999b-152">エンドポイントの型を返すために `EndpointType` というプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-152">Add a property called `EndpointType` to return the type of the endpoint.</span></span>  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  <span data-ttu-id="4999b-153"><xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> メソッドをオーバーライドし、`CreationEndpoint` を返します。</span><span class="sxs-lookup"><span data-stu-id="4999b-153">Override the <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> method and return a new `CreationEndpoint`.</span></span>  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  <span data-ttu-id="4999b-154"><xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>、<xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>、<xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>、および <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> の各メソッドをオーバーロードします。</span><span class="sxs-lookup"><span data-stu-id="4999b-154">Overload the <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, and <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> methods.</span></span> <span data-ttu-id="4999b-155">これらのメソッドは定義する必要があるだけで、コードを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4999b-155">These methods just need to be defined, you do not need to add any code to them.</span></span>  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  <span data-ttu-id="4999b-156">`CreationEndpoint` のコレクション クラスを `CreationEndpoint` プロジェクト内の CreationEndpointElement.cs ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-156">Add the collection class for `CreationEndpoint` to the CreationEndpointElement.cs file in the `CreationEndpoint` project.</span></span> <span data-ttu-id="4999b-157">このクラスは構成によって使用され、web.config ファイル内に `CreationEndpoint` のインスタンス数を格納します。</span><span class="sxs-lookup"><span data-stu-id="4999b-157">This class is used by configuration to hold a number of `CreationEndpoint` instances in a web.config file.</span></span>  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  <span data-ttu-id="4999b-158">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="4999b-158">Build the solution.</span></span>  
  
### <a name="host-the-workflow-in-iis"></a><span data-ttu-id="4999b-159">IIS でのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="4999b-159">Host the workflow in IIS</span></span>  
  
1.  <span data-ttu-id="4999b-160">IIS 内に `MyCreationEndpoint` という新しいアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4999b-160">Create a new application called `MyCreationEndpoint` in IIS.</span></span>  
  
2.  <span data-ttu-id="4999b-161">ワークフロー デザイナーによって生成された workflow1.xaml というファイルをアプリケーション ディレクトリにコピーして、その名前を workflow1.xamlx に変更します。</span><span class="sxs-lookup"><span data-stu-id="4999b-161">Copy the workflow1.xaml file generated by the workflow designer to the application directory and rename it to workflow1.xamlx.</span></span>  
  
3.  <span data-ttu-id="4999b-162">shared.dll と CreationEndpoint.dll というファイルをアプリケーションの bin ディレクトリにコピーします (bin ディレクトリは存在しなければ作成します)。</span><span class="sxs-lookup"><span data-stu-id="4999b-162">Copy the shared.dll and CreationEndpoint.dll files to the application’s bin directory (create the bin directory if it is not present).</span></span>  
  
4.  <span data-ttu-id="4999b-163">`CreationEndpoint` プロジェクト内の Web.config ファイルの内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4999b-163">Replace the contents of the Web.config file in the `CreationEndpoint` project with the following code.</span></span>  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  <span data-ttu-id="4999b-164">`<system.web>` 要素の後に、次の構成コードを追加して、`CreationEndpoint` を登録します。</span><span class="sxs-lookup"><span data-stu-id="4999b-164">After the `<system.web>` element, register `CreationEndpoint` by adding the following configuration code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="4999b-165">これによって、`CreationEndpointCollection` クラスが登録され、web.config ファイル内で `CreationEndpoint` を構成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4999b-165">This registers the `CreationEndpointCollection` class so you can configure a `CreationEndpoint` in a web.config file.</span></span>  
  
6.  <span data-ttu-id="4999b-166">追加、`<service>`要素 (後、 \</extensions > タグ) と、`CreationEndpoint`受信メッセージをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="4999b-166">Add a `<service>` element (after the \</extensions> tag) with a `CreationEndpoint` which will listen for incoming messages.</span></span>  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  <span data-ttu-id="4999b-167">追加、\<動作 > 要素 (後、 \</サービス > タグ) をサービス メタデータを有効にします。</span><span class="sxs-lookup"><span data-stu-id="4999b-167">Add a \<behaviors> element (after the \</services> tag) to enable service metadata.</span></span>  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  <span data-ttu-id="4999b-168">web.config ファイルを IIS アプリケーション ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="4999b-168">Copy the web.config to your IIS application directory.</span></span>  
  
9. <span data-ttu-id="4999b-169">作成エンドポイントが機能して Internet Explorer を起動しを参照するかどうかを確認するテストhttp://localhost/MyCreationEndpoint/Workflow1.xamlxです。</span><span class="sxs-lookup"><span data-stu-id="4999b-169">Test to see if the creation endpoint is working by starting Internet Explorer and browsing to http://localhost/MyCreationEndpoint/Workflow1.xamlx.</span></span> <span data-ttu-id="4999b-170">Internet Explorer には次のような画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4999b-170">Internet Explorer should display the following screen:</span></span>  
  
     <span data-ttu-id="4999b-171">![サービスのテスト](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span><span class="sxs-lookup"><span data-stu-id="4999b-171">![Testing the service](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span></span>  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a><span data-ttu-id="4999b-172">CreationEndpoint を呼び出すクライアントの作成</span><span class="sxs-lookup"><span data-stu-id="4999b-172">Create a client that will call the CreationEndpoint.</span></span>  
  
1.  <span data-ttu-id="4999b-173">新しいコンソール アプリケーションを `CreationEndpointTest` ソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-173">Add a new Console application to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="4999b-174">System.ServiceModel.dll、System.ServiceModel.Activities、および `Shared` プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="4999b-174">Add references to System.ServiceModel.dll, System.ServiceModel.Activities, and the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="4999b-175">`Main`メソッドを作成、<xref:System.ServiceModel.ChannelFactory%601>型の`IWorkflowCreation`を呼び出すと<xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>です。</span><span class="sxs-lookup"><span data-stu-id="4999b-175">In the `Main` method create a <xref:System.ServiceModel.ChannelFactory%601> of type `IWorkflowCreation` and call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span></span> <span data-ttu-id="4999b-176">これはプロキシを返します。</span><span class="sxs-lookup"><span data-stu-id="4999b-176">This will return a proxy.</span></span> <span data-ttu-id="4999b-177">次に、そのプロキシの `Create` を呼び出して、IIS でホストされるワークフロー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4999b-177">You can then call `Create` on that proxy to create the workflow instance hosted under IIS:</span></span>  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="4999b-178">CreationEndpointClient を実行します。</span><span class="sxs-lookup"><span data-stu-id="4999b-178">Run the CreationEndpointClient.</span></span> <span data-ttu-id="4999b-179">出力の内容は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4999b-179">The output should look like the following:</span></span>  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4999b-180">ワークフローの出力は表示されません。これはコンソール出力を持たない IIS を使って実行しているためです。</span><span class="sxs-lookup"><span data-stu-id="4999b-180">You will not see the output of the workflow because it is running under IIS which has no console output.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4999b-181">例</span><span class="sxs-lookup"><span data-stu-id="4999b-181">Example</span></span>  
 <span data-ttu-id="4999b-182">以下はこのサンプルの完全なコードです。</span><span class="sxs-lookup"><span data-stu-id="4999b-182">The following is the complete code for this sample.</span></span>  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
```  
  
 <span data-ttu-id="4999b-183">この例では `IWorkflowCreation` を実装するサービスを実装しないので、わかりにくい可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4999b-183">This example may seem confusing because you never implement a service that implements `IWorkflowCreation`.</span></span> <span data-ttu-id="4999b-184">これは、`CreationEndpoint` がユーザーに代わって実装するためです。</span><span class="sxs-lookup"><span data-stu-id="4999b-184">This is because the `CreationEndpoint` does this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4999b-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="4999b-185">See Also</span></span>  
 [<span data-ttu-id="4999b-186">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="4999b-186">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="4999b-187">インターネット インフォメーション サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="4999b-187">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="4999b-188">インターネット インフォメーション サービス ホスティングのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="4999b-188">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="4999b-189">インターネット インフォメーション サービスのホスティング手順</span><span class="sxs-lookup"><span data-stu-id="4999b-189">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="4999b-190">Windows Workflow のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="4999b-190">Windows Workflow Architecture</span></span>](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [<span data-ttu-id="4999b-191">WorkflowHostingEndpoint 再開ブックマーク</span><span class="sxs-lookup"><span data-stu-id="4999b-191">WorkflowHostingEndpoint Resume Bookmark</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [<span data-ttu-id="4999b-192">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="4999b-192">Rehosting the Workflow Designer</span></span>](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="4999b-193">Windows Workflow の概要</span><span class="sxs-lookup"><span data-stu-id="4999b-193">Windows Workflow Overview</span></span>](../../../../docs/framework/windows-workflow-foundation/overview.md)
