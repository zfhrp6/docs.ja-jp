---
title: "WCF モニカーの COM クライアントと組み合わせての使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbda85f056d7e8a465127bff948dcaaaf41094d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="9ef86-102">WCF モニカーの COM クライアントと組み合わせての使用</span><span class="sxs-lookup"><span data-stu-id="9ef86-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="9ef86-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス モニカーを使用して、COM ベースの開発環境 (Microsoft Office Visual Basic for Applications (Office VBA) や Visual Basic 6.0 など) に Web サービスを統合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-103">This sample demonstrates how to use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="9ef86-104">このサンプルは、Windows スクリプト ホストのクライアント (.vbs)、サポート クライアント ライブラリ (.dll)、およびインターネット インフォメーション サービス (IIS) でホストされるサービス ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="9ef86-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="9ef86-105">このサービスは電卓サービスの 1 つであり、COM クライアントはサービスの算術演算 (Add、Subtract、Multiply、および Divide) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="9ef86-106">クライアント アクティビティは、メッセージ ボックス ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ef86-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ef86-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ef86-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9ef86-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9ef86-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ef86-110">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="9ef86-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ef86-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="9ef86-112">サービスは、次に示すコード例で定義される `ICalculator` コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
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
```  
  
 <span data-ttu-id="9ef86-113">このサンプルでは、モニカーを使用するための次の 3 つの代替方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
-   <span data-ttu-id="9ef86-114">型指定のあるコントラクト - クライアント コンピューターで COM から参照できる型として登録されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
-   <span data-ttu-id="9ef86-115">WSDL コントラクト - WSDL ドキュメントという形で供給されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="9ef86-116">Metadata Exchange コントラクト – 実行時に Metadata Exchange (MEX) エンドポイントから取得されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="9ef86-117">型指定のあるコントラクト</span><span class="sxs-lookup"><span data-stu-id="9ef86-117">Typed Contract</span></span>  
 <span data-ttu-id="9ef86-118">型指定のあるコントラクトと共にモニカーを使用するには、属性が適切に設定されているサービス コントラクトの型を COM に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="9ef86-119">使用してクライアントを生成する必要があります最初に、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef86-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="9ef86-120">次のコマンドをクライアント ディレクトリでコマンド プロンプトから実行して、型指定のあるプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="9ef86-121">このクラスはプロジェクトに含まれている必要があり、そのプロジェクトは、COM から参照できる署名付きのアセンブリをコンパイル時に生成するように構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="9ef86-122">AssemblyInfo.cs ファイルには次の属性を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```  
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="9ef86-123">プロジェクトをビルドしたら、次の例で示すように `regasm` を使用して、COM から参照できる型を登録します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="9ef86-124">作成されたアセンブリは、グローバル アセンブリ キャッシュに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="9ef86-125">必要性は強くありませんが、これによってアセンブリを検索するランタイムのプロセスが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="9ef86-126">グローバル アセンブリ キャッシュにアセンブリを追加するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="9ef86-127">サービス モニカーで必要なのは型の登録だけであり、サービスと通信するためのプロキシは使用されません。</span><span class="sxs-lookup"><span data-stu-id="9ef86-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="9ef86-128">ComCalcClient.vbs クライアント アプリケーションは、サービス モニカーの構文を使用してサービスのアドレス、バインディング、およびコントラクトを指定し、`GetObject` 関数を使用してサービスのプロキシを構築します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="9ef86-129">モニカーが使用するパラメーターでの指定: </span><span class="sxs-lookup"><span data-stu-id="9ef86-129">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="9ef86-130">サービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="9ef86-130">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="9ef86-131">エンドポイントとの接続にクライアントが使用する必要のあるバインディング。</span><span class="sxs-lookup"><span data-stu-id="9ef86-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="9ef86-132">クライアントの構成ファイルにはカスタム バインディングを定義できますが、この場合はシステム定義の wsHttpBinding を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="9ef86-133">Windows スクリプト ホストで使用する場合、カスタム バインディングは、Cscript.exe と同じディレクトリにある Cscript.exe.config で定義されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
-   <span data-ttu-id="9ef86-134">エンドポイントでサポートされるコントラクトの型。</span><span class="sxs-lookup"><span data-stu-id="9ef86-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="9ef86-135">これは上の手順で生成され、登録された型です。</span><span class="sxs-lookup"><span data-stu-id="9ef86-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="9ef86-136">Visual Basic スクリプトには厳密に型指定された COM 環境がないので、コントラクトの識別子を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="9ef86-137">この GUID は CalcProxy.tlb からの `interfaceID` で、OLE/COM オブジェクト ビューアー (OleView.exe) などの COM ツールを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="9ef86-138">Office VBA や Visual Basic 6.0 などの厳密に型指定された環境では、コントラクト パラメーターを使用する代わりに、タイプ ライブラリへの明示的な参照を追加してプロキシ オブジェクトの型を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="9ef86-139">これにより、クライアント アプリケーションの開発中に IntelliSense のサポートも提供されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="9ef86-140">サービス モニカーを使用してプロキシ インスタンスを構築しておくと、クライアント アプリケーションはプロキシでメソッドを呼び出すことができます。これにより、対応するサービス操作を呼び出すサービス モニカー インフラストラクチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 サンプルを実行すると、操作の応答が Windows スクリプト ホストのメッセージ ボックス ウィンドウに表示されます。 ここでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと通信する型指定のあるモニカーを使用して、COM の呼び出しを行う COM クライアントを示します。 <span data-ttu-id="9ef86-143">クライアント アプリケーションでは COM が使用されますが、サービスとの通信は Web サービス呼び出しのみで構成されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="9ef86-144">WSDL コントラクト</span><span class="sxs-lookup"><span data-stu-id="9ef86-144">WSDL Contract</span></span>  
 <span data-ttu-id="9ef86-145">WSDL コントラクトと共にモニカーを使用するには、クライアント ライブラリを登録する必要はありません。ただし、ブラウサを使用してサービスの WSDL エンドポイントにアクセスするなど、帯域外機構を通じてサービスの WSDL コントラクトを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="9ef86-146">これにより、モニカーは実行時にそのコントラクトにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="9ef86-147">ComCalcClient.vbs クライアント アプリケーションは、次のように `FileSystemObject` を使用してローカルに保存されている WSDL ファイルにアクセスし、その後 `GetObject` 関数を再度使用してサービスのプロキシを構築します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="9ef86-148">モニカーが使用するパラメーターでの指定: </span><span class="sxs-lookup"><span data-stu-id="9ef86-148">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="9ef86-149">サービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="9ef86-149">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="9ef86-150">そのエンドポイントと接続するためにクライアントが使用する必要があるバインディングと、そのバインディングが定義されている名前空間。</span><span class="sxs-lookup"><span data-stu-id="9ef86-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="9ef86-151">この場合、`wsHttpBinding_ICalculator` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="9ef86-152">コントラクトを定義する WSDL。</span><span class="sxs-lookup"><span data-stu-id="9ef86-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="9ef86-153">この場合は、サービスの Wsdl.xml ファイルから読み取られた文字列です。</span><span class="sxs-lookup"><span data-stu-id="9ef86-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
-   <span data-ttu-id="9ef86-154">コントラクトの名前と名前空間。</span><span class="sxs-lookup"><span data-stu-id="9ef86-154">The name and namespace of the contract.</span></span> <span data-ttu-id="9ef86-155">WSDL に複数のコントラクトが含まれている場合があるので、識別情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="9ef86-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9ef86-156">既定では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、使用される名前空間ごとに異なる WSDL ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-156">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="9ef86-157">これらのファイルは、WSDL インポート コンストラクターを使用してリンクされます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="9ef86-158">モニカーでは単一の WSDL 定義が想定されているので、サービスはこのサンプルで示すように単一の名前空間を使用するか、または別のファイルを手動でマージする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="9ef86-159">サービス モニカーを使用してプロキシ インスタンスを構築しておくと、クライアント アプリケーションはプロキシでメソッドを呼び出すことができます。これにより、対応するサービス操作を呼び出すサービス モニカー インフラストラクチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 サンプルを実行すると、操作の応答が Windows スクリプト ホストのメッセージ ボックス ウィンドウに表示されます。 <span data-ttu-id="9ef86-161">ここでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと通信するモニカーを WSDL コントラクトと共に使用して、COM の呼び出しを行う COM クライアントを示します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="9ef86-162">Metadata Exchange コントラクト</span><span class="sxs-lookup"><span data-stu-id="9ef86-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="9ef86-163">MEX コントラクトと共にモニカーを使用するには、WSDL コントラクトと同様、クライアント登録は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9ef86-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="9ef86-164">サービスのコントラクトは、実行時に Metadata Exchange を内部使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="9ef86-165">ComCalcClient.vbs クライアント アプリケーションは次のように `GetObject` 関数を再度使用して、サービスのプロキシを構築します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="9ef86-166">モニカーが使用するパラメーターでの指定: </span><span class="sxs-lookup"><span data-stu-id="9ef86-166">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="9ef86-167">サービスの Metadata Exchange エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="9ef86-167">The address of the service metadata exchange endpoint.</span></span>  
  
-   <span data-ttu-id="9ef86-168">サービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="9ef86-168">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="9ef86-169">そのエンドポイントと接続するためにクライアントが使用する必要があるバインディングと、そのバインディングが定義されている名前空間。</span><span class="sxs-lookup"><span data-stu-id="9ef86-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="9ef86-170">この場合、`wsHttpBinding_ICalculator` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="9ef86-171">コントラクトの名前と名前空間。</span><span class="sxs-lookup"><span data-stu-id="9ef86-171">The name and namespace of the contract.</span></span> <span data-ttu-id="9ef86-172">WSDL に複数のコントラクトが含まれている場合があるので、識別情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="9ef86-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="9ef86-173">サービス モニカーを使用してプロキシ インスタンスを構築しておくと、クライアント アプリケーションはプロキシでメソッドを呼び出すことができます。これにより、対応するサービス操作を呼び出すサービス モニカー インフラストラクチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 サンプルを実行すると、操作の応答が Windows スクリプト ホストのメッセージ ボックス ウィンドウに表示されます。 <span data-ttu-id="9ef86-175">ここでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと通信するモニカーを MEX コントラクトと共に使用して、COM の呼び出しを行う COM クライアントを示します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="9ef86-176">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="9ef86-176">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="9ef86-177">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef86-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9ef86-178">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9ef86-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9ef86-179">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] コマンド プロンプトで、言語固有のフォルダーにある \client\bin\ フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-179">From a [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] command prompt, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9ef86-180">[!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[lserver](../../../../includes/lserver-md.md)]、Windows 7、または Windows Server 2008 R2 を使用している場合は、コマンド プロンプトを管理者権限で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef86-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="9ef86-181">入力`tlbexp.exe client.dll /out:CalcProxy.tlb`dll を tlb ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="9ef86-182">"タイプ ライブラリ エクスポーターの警告" が表示されることが予想されますが、ジェネリック型は不要なので問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="9ef86-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5.  <span data-ttu-id="9ef86-183">入力`regasm.exe /tlb:CalcProxy.tlb client.dll`型を COM に登録</span><span class="sxs-lookup"><span data-stu-id="9ef86-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="9ef86-184">"タイプ ライブラリ エクスポーターの警告" が表示されることが予想されますが、ジェネリック型は不要なので問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="9ef86-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6.  <span data-ttu-id="9ef86-185">入力`gacutil.exe /i client.dll`アセンブリをグローバル アセンブリ キャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="9ef86-186">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="9ef86-186">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="9ef86-187">次のアドレスを入力して、ブラウザーを使用して、サービスにアクセスできるテスト:`http://localhost/servicemodelsamples/service.svc`です。</span><span class="sxs-lookup"><span data-stu-id="9ef86-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="9ef86-188">これに応答して、確認ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-188">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="9ef86-189">言語固有のフォルダーの下の \client にある ComCalcClient.vbs を実行します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="9ef86-190">クライアント アクティビティがメッセージ ボックス ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-190">Client activity is displayed in message box windows.</span></span>  
  
3.  <span data-ttu-id="9ef86-191">クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ef86-191">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9ef86-192">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="9ef86-192">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="9ef86-193">サービス コンピューターで、ServiceModelSamples という仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="9ef86-194">サンプルに含まれている Setupvroot.bat スクリプトを使用して、ディスク ディレクトリと仮想ディレクトリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2.  <span data-ttu-id="9ef86-195">サービス プログラム ファイルを %SystemDrive%\Inetpub\wwwroot\servicemodelsamples からサービス コンピューターの ServiceModelSamples 仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="9ef86-196">\bin ディレクトリのファイルが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9ef86-196">Be sure to include the files in the \bin directory.</span></span>  
  
3.  <span data-ttu-id="9ef86-197">クライアント スクリプト ファイルを、言語固有のフォルダーにある \client フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4.  <span data-ttu-id="9ef86-198">このスクリプト ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="9ef86-199">アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5.  <span data-ttu-id="9ef86-200">WSDL ファイルをクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="9ef86-201">WSDL ファイルのサービスの Wsdl.xml で、アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9ef86-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6.  <span data-ttu-id="9ef86-202">Client.dll ライブラリを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="9ef86-203">コマンド プロンプトで、クライアント コンピューターのコピー先ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="9ef86-204">[!INCLUDE[wv](../../../../includes/wv-md.md)] または [!INCLUDE[lserver](../../../../includes/lserver-md.md)] を使用する場合は、コマンド プロンプトを管理者として実行してください。</span><span class="sxs-lookup"><span data-stu-id="9ef86-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8.  <span data-ttu-id="9ef86-205">入力`tlbexp.exe client.dll /out:CalcProxy.tlb`dll を tlb ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="9ef86-206">"タイプ ライブラリ エクスポーターの警告" が表示されることが予想されますが、ジェネリック型は不要なので問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="9ef86-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="9ef86-207">入力`regasm.exe /tlb:CalcProxy.tlb client.dll`型を COM に登録</span><span class="sxs-lookup"><span data-stu-id="9ef86-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="9ef86-208">そのパスが含まれているフォルダーに設定されていることを確認`regasm.exe`コマンドを実行する前にします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="9ef86-209">入力`gacutil.exe /i client.dll`アセンブリをグローバル アセンブリ キャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="9ef86-210">そのパスが含まれているフォルダーに設定されていることを確認`gacutil.exe`コマンドを実行する前にします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="9ef86-211">ブラウザーを使用して、サービスにクライアント コンピューターからアクセスできるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="9ef86-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="9ef86-212">クライアント コンピューターで ComCalcClient.vbs を起動します。</span><span class="sxs-lookup"><span data-stu-id="9ef86-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="9ef86-213">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="9ef86-213">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="9ef86-214">セキュリティの目的で、サンプルの使用が終わったら、このセットアップで付与された仮想ディレクトリの定義とアクセス許可を削除してください。</span><span class="sxs-lookup"><span data-stu-id="9ef86-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef86-215">参照</span><span class="sxs-lookup"><span data-stu-id="9ef86-215">See Also</span></span>
