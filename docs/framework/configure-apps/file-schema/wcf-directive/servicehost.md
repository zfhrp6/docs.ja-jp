---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 5498c300ab126bbc4e08cd228e3e7b48e905932e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352545"
---
# <a name="servicehost"></a>@ServiceHost
<span data-ttu-id="52f02-101">サービス ホストの生成に使用されるファクトリを、ホストされるサービスと、.svc ファイルで提供されるホスティング コードのアクセスとコンパイルに必要なその他のプログラミング部分に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="52f02-101">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f02-102">構文</span><span class="sxs-lookup"><span data-stu-id="52f02-102">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="52f02-103">属性</span><span class="sxs-lookup"><span data-stu-id="52f02-103">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="52f02-104">サービス</span><span class="sxs-lookup"><span data-stu-id="52f02-104">Service</span></span>  
 <span data-ttu-id="52f02-105">ホストされるサービスの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="52f02-105">The CLR type name of the service hosted.</span></span> <span data-ttu-id="52f02-106">これは、1 つ以上のサービス コンタクトを実装する型の修飾名にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52f02-106">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="52f02-107">ファクトリ</span><span class="sxs-lookup"><span data-stu-id="52f02-107">Factory</span></span>  
 <span data-ttu-id="52f02-108">サービス ホストのインスタンス化に使用されるサービス ホスト ファクトリの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="52f02-108">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="52f02-109">この属性は省略できます。</span><span class="sxs-lookup"><span data-stu-id="52f02-109">This attribute is optional.</span></span> <span data-ttu-id="52f02-110">未指定の場合は、<xref:System.ServiceModel.Activation.ServiceHostFactory> のインスタンスを返す既定の <xref:System.ServiceModel.ServiceHost> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="52f02-110">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="52f02-111">デバッグ</span><span class="sxs-lookup"><span data-stu-id="52f02-111">Debug</span></span>  
 <span data-ttu-id="52f02-112">Windows Communication Foundation (WCF) サービスをコンパイルするときにデバッグ シンボルを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="52f02-112">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="52f02-113">`true` 場合は、WCF サービスをデバッグ シンボルでコンパイルする必要があります。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="52f02-113">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="52f02-114">言語</span><span class="sxs-lookup"><span data-stu-id="52f02-114">Language</span></span>  
 <span data-ttu-id="52f02-115">ファイル (.svc) 内のすべてのインライン コードをコンパイルするときに使用する言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="52f02-115">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="52f02-116">値は、C#、VB、JS (それぞれ、C#、Visual Basic .NET、および JScript .NET を示す) など、.NET がサポートする任意の言語を表します。</span><span class="sxs-lookup"><span data-stu-id="52f02-116">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="52f02-117">この属性は省略できます。</span><span class="sxs-lookup"><span data-stu-id="52f02-117">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="52f02-118">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="52f02-118">CodeBehind</span></span>  
 <span data-ttu-id="52f02-119">XML Web サービスを実装するクラスが同じファイル内に存在せず、アセンブリとしてコンパイルされずに \Bin ディレクトリに置かれているとき、XML Web サービスを実装するソース ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="52f02-119">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52f02-120">コメント</span><span class="sxs-lookup"><span data-stu-id="52f02-120">Remarks</span></span>  
 <span data-ttu-id="52f02-121"><xref:System.ServiceModel.ServiceHost>サービスをホストするために使用、Windows Communication Foundation (WCF) のプログラミング モデル内の拡張ポイントです。</span><span class="sxs-lookup"><span data-stu-id="52f02-121">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="52f02-122">ファクトリ パターンは、ホスティング環境が直接インスタンス化できないポリモーフィック型の可能性があるため、<xref:System.ServiceModel.ServiceHost> のインスタンス化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="52f02-122">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="52f02-123">既定の実装では <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、<xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52f02-123">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="52f02-124">(1 つを派生ホストを返す)、独自のファクトリを指定するには、ファクトリの実装での CLR 型名を指定することによって、 [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="52f02-124">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="52f02-125">既定のファクトリではなく独自のカスタム サービス ホスト ファクトリに使用する、型の名前を指定だけ、 [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブが次のようにします。</span><span class="sxs-lookup"><span data-stu-id="52f02-125">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="52f02-126">ファクトリ実装はできるだけ軽量に保持してください。</span><span class="sxs-lookup"><span data-stu-id="52f02-126">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="52f02-127">多くのカスタム ロジックがある場合は、それらのロジックをファクトリ内部ではなくホスト内部に置くとコードがさらに再利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="52f02-127">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="52f02-128">例については、AJAX 対応エンドポイントを有効にする`MyService`、指定、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>の値を`Factory`属性で、既定ではなく、<xref:System.ServiceModel.Activation.ServiceHostFactory>で、 [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)としてディレクティブ次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="52f02-128">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52f02-129">例</span><span class="sxs-lookup"><span data-stu-id="52f02-129">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52f02-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="52f02-130">See Also</span></span>  
 [<span data-ttu-id="52f02-131">カスタム サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="52f02-131">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
