---
title: "My.WebServices オブジェクト"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords: My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9f2c4017a1df8059f2cc57e7c30a96c474cfda0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mywebservices-object"></a><span data-ttu-id="49e08-102">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="49e08-102">My.WebServices Object</span></span>
<span data-ttu-id="49e08-103">作成すると、現在のプロジェクトによって参照される各 XML Web サービスの 1 つのインスタンスにアクセスするには、プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="49e08-103">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49e08-104">コメント</span><span class="sxs-lookup"><span data-stu-id="49e08-104">Remarks</span></span>  
 <span data-ttu-id="49e08-105">`My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="49e08-105">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="49e08-106">各インスタンスは要求に応じてインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="49e08-106">Each instance is instantiated on demand.</span></span> <span data-ttu-id="49e08-107">これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="49e08-107">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="49e08-108">プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="49e08-108">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="49e08-109"><xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。</span><span class="sxs-lookup"><span data-stu-id="49e08-109">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="49e08-110">プロジェクトに Web サービスを追加する方法の詳細については、次を参照してください。[アプリケーション Web サービスのへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="49e08-110">For information about adding Web services to a project, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="49e08-111">`My.WebServices`オブジェクトは、現在のプロジェクトに関連付けられている Web サービスのみを公開します。</span><span class="sxs-lookup"><span data-stu-id="49e08-111">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="49e08-112">参照された Dll で宣言されている Web サービスへのアクセスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="49e08-112">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="49e08-113">DLL を提供する Web サービスにアクセスするには、フォームで Web サービスの修飾名を使用する必要があります*DllName*.*WebServiceName*です。</span><span class="sxs-lookup"><span data-stu-id="49e08-113">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="49e08-114">詳細については、次を参照してください。[アプリケーション Web サービスのへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="49e08-114">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="49e08-115">オブジェクトとそのプロパティでは、Web アプリケーションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="49e08-115">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="49e08-116">プロパティ</span><span class="sxs-lookup"><span data-stu-id="49e08-116">Properties</span></span>  
 <span data-ttu-id="49e08-117">各プロパティ、`My.WebServices`オブジェクトが現在のプロジェクトによって参照される Web サービスのインスタンスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="49e08-117">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="49e08-118">プロパティの名前は、プロパティがアクセスすると、Web サービスの名前と同じとプロパティの型が、Web サービスの型と同じです。</span><span class="sxs-lookup"><span data-stu-id="49e08-118">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49e08-119">Web サービスへのアクセスのプロパティ名には、名前の競合がある場合*RootNamespace*_*Namespace*\_*ServiceName*です。</span><span class="sxs-lookup"><span data-stu-id="49e08-119">If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="49e08-120">たとえば、という 2 つの Web サービス`Service1`です。</span><span class="sxs-lookup"><span data-stu-id="49e08-120">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="49e08-121">ルート名前空間にはこれらのサービスのいずれかのかどうかは`WindowsApplication1`と名前空間に`Namespace1`を使用してそのサービスにアクセスするよう`My.WebServices.WindowsApplication1_Namespace1_Service1`です。</span><span class="sxs-lookup"><span data-stu-id="49e08-121">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="49e08-122">初めてアクセスしたときの 1 つ、`My.WebServices`オブジェクトのプロパティ、その Web サービスの新しいインスタンスを作成および格納します。</span><span class="sxs-lookup"><span data-stu-id="49e08-122">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="49e08-123">そのプロパティのそれ以降のアクセスは、その Web サービスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="49e08-123">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="49e08-124">割り当てることによって、Web サービスの破棄する`Nothing`その Web サービスのプロパティにします。</span><span class="sxs-lookup"><span data-stu-id="49e08-124">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="49e08-125">プロパティ set アクセス操作子が割り当てられます`Nothing`に格納されている値。</span><span class="sxs-lookup"><span data-stu-id="49e08-125">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="49e08-126">以外の任意の値を割り当てる場合`Nothing`プロパティの setter がスローされます、<xref:System.ArgumentException>例外。</span><span class="sxs-lookup"><span data-stu-id="49e08-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="49e08-127">プロパティかどうかをテストすることができます、`My.WebServices`オブジェクトを使用して、Web サービスのインスタンスが格納されて、`Is`または`IsNot`演算子。</span><span class="sxs-lookup"><span data-stu-id="49e08-127">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="49e08-128">これらの演算子を使用するには、プロパティの値をチェックする`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="49e08-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49e08-129">通常、`Is`または`IsNot`オペレーターが、比較を実行するプロパティの値を読み取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="49e08-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="49e08-130">ただし場合、プロパティが現在格納`Nothing`プロパティ、Web サービスの新しいインスタンスを作成し、そのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="49e08-130">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="49e08-131">ただし、Visual Basic コンパイラがのプロパティを処理、`My.WebServices`でき、特別に、オブジェクト、`Is`または`IsNot`演算子をその値を変更することがなく、プロパティの状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="49e08-131">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49e08-132">例</span><span class="sxs-lookup"><span data-stu-id="49e08-132">Example</span></span>  
 <span data-ttu-id="49e08-133">この例では、`FahrenheitToCelsius`のメソッド、 `TemperatureConverter` XML Web サービス、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="49e08-133">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 <span data-ttu-id="49e08-134">この例を実行するは、プロジェクトがという名前の Web サービスを参照する必要があります`Converter`、およびその Web サービスを公開する必要があります、`ConvertTemperature`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="49e08-134">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="49e08-135">詳細については、次を参照してください。[アプリケーション Web サービスのへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="49e08-135">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="49e08-136">このコードは、Web アプリケーション プロジェクトでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="49e08-136">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49e08-137">要件</span><span class="sxs-lookup"><span data-stu-id="49e08-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="49e08-138">プロジェクトの種類別の可用性</span><span class="sxs-lookup"><span data-stu-id="49e08-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="49e08-139">プロジェクトの種類</span><span class="sxs-lookup"><span data-stu-id="49e08-139">Project type</span></span>|<span data-ttu-id="49e08-140">使用可能</span><span class="sxs-lookup"><span data-stu-id="49e08-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="49e08-141">Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="49e08-141">Windows Application</span></span>|<span data-ttu-id="49e08-142">**はい**</span><span class="sxs-lookup"><span data-stu-id="49e08-142">**Yes**</span></span>|  
|<span data-ttu-id="49e08-143">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="49e08-143">Class Library</span></span>|<span data-ttu-id="49e08-144">**はい**</span><span class="sxs-lookup"><span data-stu-id="49e08-144">**Yes**</span></span>|  
|<span data-ttu-id="49e08-145">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="49e08-145">Console Application</span></span>|<span data-ttu-id="49e08-146">**はい**</span><span class="sxs-lookup"><span data-stu-id="49e08-146">**Yes**</span></span>|  
|<span data-ttu-id="49e08-147">Windows コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="49e08-147">Windows Control Library</span></span>|<span data-ttu-id="49e08-148">**はい**</span><span class="sxs-lookup"><span data-stu-id="49e08-148">**Yes**</span></span>|  
|<span data-ttu-id="49e08-149">Web コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="49e08-149">Web Control Library</span></span>|<span data-ttu-id="49e08-150">**はい**</span><span class="sxs-lookup"><span data-stu-id="49e08-150">**Yes**</span></span>|  
|<span data-ttu-id="49e08-151">Windows サービス</span><span class="sxs-lookup"><span data-stu-id="49e08-151">Windows Service</span></span>|<span data-ttu-id="49e08-152">**はい**</span><span class="sxs-lookup"><span data-stu-id="49e08-152">**Yes**</span></span>|  
|<span data-ttu-id="49e08-153">Web サイト</span><span class="sxs-lookup"><span data-stu-id="49e08-153">Web Site</span></span>|<span data-ttu-id="49e08-154">いいえ</span><span class="sxs-lookup"><span data-stu-id="49e08-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49e08-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="49e08-155">See Also</span></span>  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="49e08-156">アプリケーションの Web サービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="49e08-156">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
