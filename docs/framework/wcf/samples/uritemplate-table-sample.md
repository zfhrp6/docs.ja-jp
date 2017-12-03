---
title: "UriTemplate テーブル サンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1826157ca2214a7f2fa0201d15bc4b7ca1b255c2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="e1dd1-102">UriTemplate テーブル サンプル</span><span class="sxs-lookup"><span data-stu-id="e1dd1-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="e1dd1-103"><xref:System.UriTemplateTable> クラスには、`UriTemplate` インスタンスのセットを使用するための、ディクショナリに似た結合テーブル構造が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="e1dd1-104">特定の URI (Uniform Resource Identifier) をテーブル内のすべてのテンプレートと効率よく照合でき、照合されたテンプレートに関連付けられたデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="e1dd1-105">このサンプルでは、次の `UriTemplateTable` クラスに関連する重要な概念を示します。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="e1dd1-106">`UriTemplateTable` をインスタンス化する構文</span><span class="sxs-lookup"><span data-stu-id="e1dd1-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="e1dd1-107">`UriTemplateTable` へのキー/値ペアのセットの追加</span><span class="sxs-lookup"><span data-stu-id="e1dd1-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
-   <span data-ttu-id="e1dd1-108"><xref:System.UriTemplateTable.MatchSingle%2A> を使用した候補 URI とテーブルの照合</span><span class="sxs-lookup"><span data-stu-id="e1dd1-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1dd1-109">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="e1dd1-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e1dd1-110">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="e1dd1-111">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e1dd1-112">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e1dd1-113">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e1dd1-114">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1dd1-115">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e1dd1-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="e1dd1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1dd1-116">See Also</span></span>  
 [<span data-ttu-id="e1dd1-117">UriTemplate テーブル ディスパッチャー</span><span class="sxs-lookup"><span data-stu-id="e1dd1-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)  
 [<span data-ttu-id="e1dd1-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e1dd1-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
