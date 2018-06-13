---
title: 基本的な XAML 専用サービス
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: aa6b6ec6930ac90fe95b1cdfcd4cb027de8e5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517200"
---
# <a name="basic-xaml-only-service"></a><span data-ttu-id="58aa5-102">基本的な XAML 専用サービス</span><span class="sxs-lookup"><span data-stu-id="58aa5-102">Basic XAML only Service</span></span>
<span data-ttu-id="58aa5-103">このサンプルでは、XAML 専用サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="58aa5-103">This sample demonstrates how to create a XAML only service.</span></span> <span data-ttu-id="58aa5-104">このシナリオは自動車関連の問題に対する診断サービスです。</span><span class="sxs-lookup"><span data-stu-id="58aa5-104">The scenario is a diagnostics service for car-related problems.</span></span> <span data-ttu-id="58aa5-105">このサービスは、顧客に一連の質問をして問題を診断するワークフローとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="58aa5-105">The service is implemented as a workflow that asks the client a series of questions to diagnose the problem.</span></span> <span data-ttu-id="58aa5-106">このサービスで診断できる問題は 2 種類です (車のエンジンがかからない、または空調装置が動作しない)。</span><span class="sxs-lookup"><span data-stu-id="58aa5-106">There are two types of issues the service can diagnose (car does not start or air conditioning not working).</span></span> <span data-ttu-id="58aa5-107">ワークフローでは、デザイナーの要求/応答テンプレートを使用して、3 つの簡単なサービス操作を公開します。</span><span class="sxs-lookup"><span data-stu-id="58aa5-107">The workflow uses Request/Reply template from the designer to expose three simple service operations.</span></span> <span data-ttu-id="58aa5-108">サービスは、IIS に仮想ディレクトリを作成し、service1.xamlx ファイルおよび Web.config ファイルをその仮想ディレクトリにコピーすることによって IIS でホストされます。コンパイルされたコードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="58aa5-108">The service is hosted in IIS by creating a virtual directory in IIS and copying the service1.xamlx and Web.config files into the virtual directory, no compiled code is required.</span></span> <span data-ttu-id="58aa5-109">既定ではこのサンプルは自動的に必要なファイルにコピー WCF および WF のサンプルのセットアップ手順をたどるときに作成された仮想ディレクトリ: [WindowsCommunicationFoundationサンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Visual Studio 2010 でのビルド時にします。</span><span class="sxs-lookup"><span data-stu-id="58aa5-109">By default this sample will automatically copy the needed files into the virtual directory created when you follow the setup instructions for the WCF and WF samples: [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) when built in Visual Studio 2010.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="58aa5-110">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="58aa5-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="58aa5-111">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="58aa5-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="58aa5-112">[ソリューションの基本ディレクトリ]\Client\bin\debug に生成されたクライアント アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="58aa5-112">Run the Client application generated in [solution base directory]\Client\bin\debug.</span></span>  
  
3.  <span data-ttu-id="58aa5-113">オプションが出力されるので、オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="58aa5-113">The application prints out options, selects an option.</span></span> <span data-ttu-id="58aa5-114">質問が表示されたら、はいかいいえで (Y キーまたは N キーを使用して) 回答します。</span><span class="sxs-lookup"><span data-stu-id="58aa5-114">The application then asks some questions, answer them yes or no (using Y/N keys).</span></span> <span data-ttu-id="58aa5-115">サービスによる問題の診断が完了すると、診断結果が出力されます。</span><span class="sxs-lookup"><span data-stu-id="58aa5-115">When the service is done diagnosing the issues, the application prints out a diagnosis.</span></span>  
  
4.  <span data-ttu-id="58aa5-116">オプションが再度表示されます。</span><span class="sxs-lookup"><span data-stu-id="58aa5-116">The application goes back to the options.</span></span> <span data-ttu-id="58aa5-117">もう一度問題を診断することも、アプリケーションを終了することもできます。</span><span class="sxs-lookup"><span data-stu-id="58aa5-117">You can diagnose another problem or exit the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58aa5-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="58aa5-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58aa5-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="58aa5-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="58aa5-120">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="58aa5-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58aa5-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="58aa5-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`