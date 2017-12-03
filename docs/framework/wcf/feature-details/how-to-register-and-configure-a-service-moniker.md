---
title: "方法 : サービス モニカーを登録および構成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 32cb95eebbc5738204b063f1cf5f8264e775791f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="d3051-102">方法 : サービス モニカーを登録および構成する</span><span class="sxs-lookup"><span data-stu-id="d3051-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="d3051-103">COM アプリケーションの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス モニカーを型付きコントラクトで使うには、必要な属性を備えた型を COM に登録し、COM アプリケーションとモニカーに、必要なバインディング設定を組み込まなければなりません。</span><span class="sxs-lookup"><span data-stu-id="d3051-103">Before using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="d3051-104">必要な属性を備えた型を COM に登録するには</span><span class="sxs-lookup"><span data-stu-id="d3051-104">To register the required attributed types with COM</span></span>  
  
1.  <span data-ttu-id="d3051-105">使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)からコントラクトのメタデータを取得するツール、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス。</span><span class="sxs-lookup"><span data-stu-id="d3051-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="d3051-106">これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリに組み込むソース コードと、クライアント アプリケーションの構成ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d3051-106">This generates the source code for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly and a client application configuration file.</span></span>  
  
2.  <span data-ttu-id="d3051-107">アセンブリ内で定義されている型に `ComVisible` という設定をします。</span><span class="sxs-lookup"><span data-stu-id="d3051-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="d3051-108">Visual Studio プロジェクトで、AssemblyInfo.cs ファイルに次の属性を追加してください。</span><span class="sxs-lookup"><span data-stu-id="d3051-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  <span data-ttu-id="d3051-109">マネージ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを、厳密な名前のアセンブリとしてコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d3051-109">Compile the managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as a strong-named assembly.</span></span> <span data-ttu-id="d3051-110">そのためには暗号キー ペアで署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3051-110">This requires signing with a cryptographic key pair.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="d3051-111">[厳密な名前でアセンブリに署名](http://go.microsoft.com/fwlink/?LinkId=94874).NET 開発者ガイド 』 でします。</span><span class="sxs-lookup"><span data-stu-id="d3051-111"> [Signing an Assembly with a Strong Name](http://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4.  <span data-ttu-id="d3051-112">アセンブリ登録 (Regasm.exe) ツールに `/tlb` オプションを指定して、アセンブリで定義されている型を COM に登録します。</span><span class="sxs-lookup"><span data-stu-id="d3051-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5.  <span data-ttu-id="d3051-113">グローバル アセンブリ キャッシュ ツール (Gacutil.exe) で、グローバル アセンブリ キャッシュにアセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3051-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3051-114">アセンブリへの署名とグローバル アセンブリ キャッシュへの追加は、必須ではありません。しかしこれを済ませておくと、実行時には、適切な場所からアセンブリを読み込むための手順が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="d3051-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="d3051-115">COM アプリケーションとモニカーに必要なバインディングを設定するには</span><span class="sxs-lookup"><span data-stu-id="d3051-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
-   <span data-ttu-id="d3051-116">バインディングの定義を配置 (によって生成された、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成されたクライアント アプリケーション構成ファイルに) クライアント アプリケーションの構成ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="d3051-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="d3051-117">たとえば、Visual Basic 6.0 で開発した実行可能ファイルの名前が CallCenterClient.exe の場合、これと同じディレクトリに、CallCenterConfig.exe.config という名前で構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3051-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="d3051-118">するとクライアント アプリケーションはモニカーを使えるようになります。</span><span class="sxs-lookup"><span data-stu-id="d3051-118">The client application can now use the moniker.</span></span> <span data-ttu-id="d3051-119">なお、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に組み込まれている標準のバインディング型を使うのであれば、バインディングの設定は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d3051-119">Note that the binding configuration is not required if using one of the standard binding types provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
     <span data-ttu-id="d3051-120">次の型が登録されています。</span><span class="sxs-lookup"><span data-stu-id="d3051-120">The following type is registered.</span></span>  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="d3051-121">このアプリケーションは、`wsHttpBinding` バインディングを使用して公開されています。</span><span class="sxs-lookup"><span data-stu-id="d3051-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="d3051-122">このような型とアプリケーション設定であれば、次のようなモニカー文字列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3051-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="d3051-123">`IMathService` 型を定義するアセンブリへの参照を追加すれば、次のコード例のように、Visual Basic 6.0 アプリケーションに上記のモニカー文字列 (どちらの形式でも可) を記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d3051-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="d3051-124">この例で、バインディング構成 `Binding1` の定義は、クライアント アプリケーションごとに、vb6appname.exe.config など該当する名前の構成ファイルに記述します。</span><span class="sxs-lookup"><span data-stu-id="d3051-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3051-125">同様のコードを C#、C++、およびその他の .NET 言語アプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3051-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3051-126">モニカーの形式が正しくないか、サービスを使用できない場合は、`GetObject` を呼び出すと、"構文が無効です" というエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="d3051-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="d3051-127">このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d3051-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="d3051-128">このトピックでは、主に VB 6.0 コードからサービス モニカーを使用する方法について説明していますが、他の言語からサービス モニカーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3051-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="d3051-129">C++ コードからモニカーを使用している場合、次のコードに示すように、Svcutil.exe によって生成されたアセンブリを、"no_namespace named_guids raw_interfaces_only" と共にインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3051-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="d3051-130">これにより、インポートされたインターフェイス定義は、すべてのメソッドが `HResult` を返すように変更されます。</span><span class="sxs-lookup"><span data-stu-id="d3051-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="d3051-131">他の戻り値は、出力パラメーターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="d3051-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="d3051-132">メソッドの実行全体は、同じままです。</span><span class="sxs-lookup"><span data-stu-id="d3051-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="d3051-133">このために、プロキシでメソッドを呼び出したときの例外の原因を特定できます。</span><span class="sxs-lookup"><span data-stu-id="d3051-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="d3051-134">この機能は C++ コードからのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3051-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3051-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3051-135">See Also</span></span>  
 [<span data-ttu-id="d3051-136">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d3051-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
