---
title: メタデータ ストアのプログラム性
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 6efcb86e29f19a29d6ef382afa336d0ca2ce4306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="6e41c-102">メタデータ ストアのプログラム性</span><span class="sxs-lookup"><span data-stu-id="6e41c-102">Metadata Store Programmability</span></span>
<span data-ttu-id="6e41c-103">メタデータ ストアは、実行時に任意のメタデータを CLR 属性の形式で型に関連付けることができる [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]機能です。</span><span class="sxs-lookup"><span data-stu-id="6e41c-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="6e41c-104">これにより、実行時コンポーネントと対応するデザイン時コンポーネントの間の疎結合、および実行時コンポーネントに影響を与えることなくデザイン時コンポーネントを変更する機能が実現します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="6e41c-105">このサンプルでは、属性を実行時の型に適用することで、メタデータ ストアを使用して制御できないソースをプログラミングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="6e41c-106">通常使用されるこの用語は、ホスト アプリケーションによって型セットのメタデータが登録されることを示します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="6e41c-107">出力内で、追加の予期しない属性に気付くかもしれません<!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> -->`System.Runtime.InteropServices.GUIDAttribute`です。</span><span class="sxs-lookup"><span data-stu-id="6e41c-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="6e41c-108">これはメタデータ API の使用時に追加されるもので、サンプルの実行には影響しません。</span><span class="sxs-lookup"><span data-stu-id="6e41c-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="6e41c-109">このサンプルでは、次の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6e41c-110">使用例</span><span class="sxs-lookup"><span data-stu-id="6e41c-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="6e41c-111">メタデータ ストア API を使用して属性を挿入する方法。</span><span class="sxs-lookup"><span data-stu-id="6e41c-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="6e41c-112">コールバック メカニズムを使用してメタデータの登録を遅らせる方法。</span><span class="sxs-lookup"><span data-stu-id="6e41c-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6e41c-113">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="6e41c-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6e41c-114">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ProgrammingMetadataStore.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6e41c-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6e41c-115">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6e41c-116">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e41c-117">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6e41c-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6e41c-118">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6e41c-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6e41c-119">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="6e41c-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6e41c-120">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6e41c-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`