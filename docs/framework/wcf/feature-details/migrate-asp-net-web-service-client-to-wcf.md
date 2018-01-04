---
title: "方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: baf43f2bfa2175062c57f73e45835c251ac5769e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="40e23-102">方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する</span><span class="sxs-lookup"><span data-stu-id="40e23-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="40e23-103">次の手順では、ASP.NET Web サービス クライアント コードを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行するために従う必要のある大まかな手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="40e23-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="40e23-104">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="40e23-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="40e23-105">ASP.NET Web サービス クライアント コードを WCF に移行するには</span><span class="sxs-lookup"><span data-stu-id="40e23-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="40e23-106">クライアントの包括的なテスト セットが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="40e23-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="40e23-107">Visual Studio 2005 を使用して、クライアント アプリケーションを .NET 2.0 にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="40e23-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="40e23-108">テスト セットを実行します。</span><span class="sxs-lookup"><span data-stu-id="40e23-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="40e23-109">クライアント プロジェクトから ASP.NET クライアント コードを削除します。</span><span class="sxs-lookup"><span data-stu-id="40e23-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="40e23-110">このコードは、WSDL.exe ツールを使用して生成したモジュールにあります。</span><span class="sxs-lookup"><span data-stu-id="40e23-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="40e23-111">生成[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアント コードを使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="40e23-111">Generate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="40e23-112">このコードをクライアント プロジェクトに追加し、構成の出力をクライアントの既存の構成ファイルにマージします。</span><span class="sxs-lookup"><span data-stu-id="40e23-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="40e23-113">アプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="40e23-113">Compile the application.</span></span> <span data-ttu-id="40e23-114">以前の ASP.NET クライアント型への参照を新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント型への参照に置き換えることで、コンパイル エラーを修正します。</span><span class="sxs-lookup"><span data-stu-id="40e23-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client types.</span></span>  
  
6.  <span data-ttu-id="40e23-115">テスト セットを実行します。</span><span class="sxs-lookup"><span data-stu-id="40e23-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e23-116">参照</span><span class="sxs-lookup"><span data-stu-id="40e23-116">See Also</span></span>  
 [<span data-ttu-id="40e23-117">方法 : ASP.NET Web サービス コードを Windows Communication Foundation に移行する</span><span class="sxs-lookup"><span data-stu-id="40e23-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
