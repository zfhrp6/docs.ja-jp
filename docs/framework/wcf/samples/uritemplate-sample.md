---
title: UriTemplate サンプル
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 53ce296eadf03d7f9f46d36cb0130c9b502f4893
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502375"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="981a1-102">UriTemplate サンプル</span><span class="sxs-lookup"><span data-stu-id="981a1-102">UriTemplate Sample</span></span>
<span data-ttu-id="981a1-103"><xref:System.UriTemplate> クラスには、共通構造を共有する URI のセットを使用するためのメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="981a1-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="981a1-104">このサンプルでは、次の `UriTemplate` に関連する重要な概念を示します。</span><span class="sxs-lookup"><span data-stu-id="981a1-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
-   <span data-ttu-id="981a1-105">テンプレートを作成するための構文</span><span class="sxs-lookup"><span data-stu-id="981a1-105">Syntax for creating templates.</span></span>  
  
-   <span data-ttu-id="981a1-106">`UriTemplate` および <xref:System.UriTemplate.BindByName%2A> を使用した、<xref:System.UriTemplate.BindByPosition%2A> からの URI のインスタンス化</span><span class="sxs-lookup"><span data-stu-id="981a1-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
-   <span data-ttu-id="981a1-107"><xref:System.UriTemplateTable.Match%2A> および `BindByName` の逆の操作である `BindByPosition`</span><span class="sxs-lookup"><span data-stu-id="981a1-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="981a1-108">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="981a1-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="981a1-109">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="981a1-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="981a1-110">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="981a1-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="981a1-111">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="981a1-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="981a1-112">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="981a1-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="981a1-113">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="981a1-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="981a1-114">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="981a1-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="981a1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="981a1-115">See Also</span></span>  
 [<span data-ttu-id="981a1-116">UriTemplate テーブル</span><span class="sxs-lookup"><span data-stu-id="981a1-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="981a1-117">UriTemplate テーブル ディスパッチャー</span><span class="sxs-lookup"><span data-stu-id="981a1-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
