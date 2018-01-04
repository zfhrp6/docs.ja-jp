---
title: "バイトストリーム エンコーダー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de6d5fd64046a72eb6a21b43dd977463f5619850
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="bytestream-encoder"></a><span data-ttu-id="acd36-102">バイトストリーム エンコーダー</span><span class="sxs-lookup"><span data-stu-id="acd36-102">ByteStream Encoder</span></span>
<span data-ttu-id="acd36-103">このサンプルでは、バイト ストリーム エンコーダーの機能を示す `ByteStreamHttpBinding` である <xref:System.ServiceModel.Channels.Binding> を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="acd36-103">This sample demonstrates how to create a `ByteStreamHttpBinding`, a <xref:System.ServiceModel.Channels.Binding> that demonstrates the functionality of the byte stream encoder.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="acd36-104">説明</span><span class="sxs-lookup"><span data-stu-id="acd36-104">Discussion</span></span>  
 <span data-ttu-id="acd36-105">このサンプルでは、標準のバインディング要素 <xref:System.ServiceModel.Channels.Binding> および <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> を使用して、標準の <xref:System.ServiceModel.Channels.HttpTransportBindingElement> を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="acd36-105">This sample demonstrates how to create a standard <xref:System.ServiceModel.Channels.Binding> using the standard binding elements <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span> <span data-ttu-id="acd36-106">このサンプルでは、バイト ストリーム エンコーダーを使用して、画像をアップロードおよびダウンロードする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="acd36-106">This sample shows how to use the byte stream encoder to upload and download an image.</span></span> <span data-ttu-id="acd36-107">バイト ストリーム エンコーダーの機能は、HTTP トランスポートのみサポートし、信頼できるメッセージングやセキュリティなどの機能はサポートしません。</span><span class="sxs-lookup"><span data-stu-id="acd36-107">The byte stream encoder feature only supports the HTTP transport and it does not support features such as reliable messaging or security.</span></span> <span data-ttu-id="acd36-108">唯一サポートされる <xref:System.ServiceModel.Channels.MessageVersion> は <xref:System.ServiceModel.Channels.MessageVersion.None%2A> です。</span><span class="sxs-lookup"><span data-stu-id="acd36-108">The only <xref:System.ServiceModel.Channels.MessageVersion> supported is <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="acd36-109">このサンプルを [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] または [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)] で実行している場合は、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] をシステム特権で実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="acd36-109">If you are running this sample in [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] or [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ensure that you are running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with elevated privileges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="acd36-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="acd36-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="acd36-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="acd36-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="acd36-112">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="acd36-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="acd36-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="acd36-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="acd36-114">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="acd36-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="acd36-115">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で ByteStreamHttpBinding.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="acd36-115">Open the ByteStreamHttpBinding.sln file in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="acd36-116">ソリューション エクスプ ローラーでプロジェクトを右クリックして、ByteStreamHttpBindingServer プロジェクトの新しいインスタンスを開始**デバッグ**、し**新しいインスタンスを開始**コンテキスト メニュー。</span><span class="sxs-lookup"><span data-stu-id="acd36-116">Start a new instance of the ByteStreamHttpBindingServer project by right-clicking the project in the Solution Explorer and selecting **Debug**, and then **Start new instance** from the context menu.</span></span>  
  
3.  <span data-ttu-id="acd36-117">ソリューション エクスプ ローラーでプロジェクトを右クリックして、ByteStreamHttpBindingClient プロジェクトの新しいインスタンスを開始**デバッグ**、**新しいインスタンスを開始**コンテキスト メニュー。</span><span class="sxs-lookup"><span data-stu-id="acd36-117">Start a new instance of the ByteStreamHttpBindingClient project by right-clicking the project in the Solution Explorer and selecting **Debug**, **Start new instance** from the context menu.</span></span>
