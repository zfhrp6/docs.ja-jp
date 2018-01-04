---
title: "方法 : Windows Communication Foundation サービス コントラクトを定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: "58"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c69f79d8629acee80a2e59346032e7733ec37dea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="7a094-102">方法 : Windows Communication Foundation サービス コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="7a094-102">How to: Define a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="7a094-103">これは、基本的な [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションの作成に必要な 6 つのタスクのうちの最初のタスクです。</span><span class="sxs-lookup"><span data-stu-id="7a094-103">This is the first of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="7a094-104">タスクの 6 つのすべての概要については、次を参照してください。、[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="7a094-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="7a094-105">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを作成する場合、まずサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="7a094-105">When creating a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service, the first task is to define a service contract.</span></span> <span data-ttu-id="7a094-106">サービス コントラクトは、サービスがサポートする操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a094-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="7a094-107">操作は Web サービス メソッドと見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="7a094-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="7a094-108">コントラクトは C++、C#、または Visual Basic (VB) インターフェイスを定義することで作成します。</span><span class="sxs-lookup"><span data-stu-id="7a094-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="7a094-109">インターフェイスの各メソッドは、特定のサービス操作に対応しています。</span><span class="sxs-lookup"><span data-stu-id="7a094-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="7a094-110">各インターフェイスには <xref:System.ServiceModel.ServiceContractAttribute> が適用されており、各操作には <xref:System.ServiceModel.OperationContractAttribute> 属性が適用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a094-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="7a094-111"><xref:System.ServiceModel.ServiceContractAttribute> 属性を持つインターフェイス内のメソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性がない場合、そのメソッドはサービスによって公開されません。</span><span class="sxs-lookup"><span data-stu-id="7a094-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>  
  
 <span data-ttu-id="7a094-112">手順の後に、このタスクに使用するコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="7a094-112">The code used for this task is provided in the example following the procedure.</span></span>  
  
### <a name="to-define-a-service-contract"></a><span data-ttu-id="7a094-113">サービス コントラクトを定義するには</span><span class="sxs-lookup"><span data-stu-id="7a094-113">To define a service contract</span></span>  
  
1.  <span data-ttu-id="7a094-114">開いている[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]でプログラムを右クリックして、管理者として、**開始**メニューを選択して**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="7a094-114">Open  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] as an administrator by right-clicking the program in the **Start** menu and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="7a094-115">クリックして、WCF サービス ライブラリ プロジェクトを作成、**ファイル**メニューを選択して**新規**、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="7a094-115">Create a WCF Service Library project by clicking the **File** menu and selecting **New**, **Project**.</span></span> <span data-ttu-id="7a094-116">**新しいプロジェクト**ダイアログ ボックスで、ダイアログ ボックスの左側にある展開**Visual c#** c# プロジェクトまたは**他の言語**し**Visual Basic** Visual Basic プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="7a094-116">In the **New Project** dialog, on the left-hand side of the dialog expand **Visual C#** for a C# project or **Other Languages** and then **Visual Basic** for a Visual Basic project.</span></span> <span data-ttu-id="7a094-117">選択した言語を選択**WCF**とプロジェクト テンプレートの一覧がダイアログの中央のセクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a094-117">Under the language selected select **WCF** and a list of project templates will be displayed on the center section of the dialog.</span></span> <span data-ttu-id="7a094-118">選択**WCF サービス ライブラリ**、および種類`GettingStartedLib`で、**名前** テキスト ボックスと`GettingStarted`で、**ソリューション名**ダイアログの下部にあるテキスト ボックス。</span><span class="sxs-lookup"><span data-stu-id="7a094-118">Select **WCF Service Library**, and type `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>  
  
3.  <span data-ttu-id="7a094-119">Visual Studio により、IService1.cs (または IService1.vb)、Service1.cs (または Service1.vb)、App.config の 3 つのファイルを含むプロジェクトが作成されます。IService1 ファイルには、既定のサービス コントラクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7a094-119">Visual Studio will create the project which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config.  The IService1 file contains a default service contract.</span></span>  <span data-ttu-id="7a094-120">Service1 ファイルには、サービス コントラクトの既定の実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7a094-120">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="7a094-121">App.config ファイルには、Visual Studio WCF サービス ホストに既定のサービスを読み込むために必要な構成が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7a094-121">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="7a094-122">WCF サービス ホスト ツールの詳細については、次を参照してください[WCF サービス ホスト (WcfSvcHost.exe)。](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="7a094-122">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>  
  
4.  <span data-ttu-id="7a094-123">IService1.cs または IService1.vb ファイルを開き、名前空間の宣言を残したまま、名前空間宣言内のコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="7a094-123">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration leaving the namespace declaration.</span></span> <span data-ttu-id="7a094-124">次のコードに示すように、名前空間宣言内に新しいインターフェイス `ICalculator` を定義します。</span><span class="sxs-lookup"><span data-stu-id="7a094-124">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
            public interface ICalculator  
            {  
                [OperationContract]  
                double Add(double n1, double n2);  
                [OperationContract]  
                double Subtract(double n1, double n2);  
                [OperationContract]  
                double Multiply(double n1, double n2);  
                [OperationContract]  
                double Divide(double n1, double n2);  
            }  
    }  
    ```  
  
    ```  
    ‘IService.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
        Public Interface ICalculator  
  
            <OperationContract()> _  
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
        End Interface  
    End Namespace  
    ```  
  
     <span data-ttu-id="7a094-125">このコントラクトは、オンライン電卓を定義します。</span><span class="sxs-lookup"><span data-stu-id="7a094-125">This contract defines an online calculator.</span></span> <span data-ttu-id="7a094-126">`ICalculator` インターフェイスは <xref:System.ServiceModel.ServiceContractAttribute> 属性でマークされています。</span><span class="sxs-lookup"><span data-stu-id="7a094-126">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="7a094-127">この属性は、コントラクト名を区別するために使用される名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="7a094-127">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="7a094-128">各電卓操作は <xref:System.ServiceModel.OperationContractAttribute> 属性でマークされています。</span><span class="sxs-lookup"><span data-stu-id="7a094-128">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a094-129">属性を使用してインターフェイス、メンバー、またはクラスに注釈を付けるときは、属性名から "Attribute" 部分を削除できます。</span><span class="sxs-lookup"><span data-stu-id="7a094-129">When using attributes to annotate an interface, member, or class, you can drop the "Attribute" part from the attribute name.</span></span> <span data-ttu-id="7a094-130">したがって、<xref:System.ServiceModel.ServiceContractAttribute> は、C# では `[ServiceContract]`、Visual Basic では `<ServiceContract>` になります。</span><span class="sxs-lookup"><span data-stu-id="7a094-130">So <xref:System.ServiceModel.ServiceContractAttribute> becomes `[ServiceContract]` in C#, or `<ServiceContract>` in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a094-131">参照</span><span class="sxs-lookup"><span data-stu-id="7a094-131">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="7a094-132">方法: サービス コントラクトを実装する</span><span class="sxs-lookup"><span data-stu-id="7a094-132">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="7a094-133">はじめに</span><span class="sxs-lookup"><span data-stu-id="7a094-133">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="7a094-134">自己ホスト</span><span class="sxs-lookup"><span data-stu-id="7a094-134">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
