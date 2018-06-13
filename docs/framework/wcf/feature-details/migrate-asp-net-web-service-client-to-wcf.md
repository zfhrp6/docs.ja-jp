---
title: '方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する'
ms.date: 03/30/2017
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
ms.openlocfilehash: cb60f9cb2e8f35ee703b049eae9e3d99c1ec7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491131"
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="3d51e-102">方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する</span><span class="sxs-lookup"><span data-stu-id="3d51e-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="3d51e-103">次の手順では、ASP.NET Web サービス クライアント コードを WCF に移行後にする必要のある大まかな手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="3d51e-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to WCF.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="3d51e-104">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3d51e-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="3d51e-105">ASP.NET Web サービス クライアント コードを WCF に移行するには</span><span class="sxs-lookup"><span data-stu-id="3d51e-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="3d51e-106">クライアントの包括的なテスト セットが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="3d51e-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="3d51e-107">Visual Studio 2005 を使用して、クライアント アプリケーションを .NET 2.0 にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="3d51e-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="3d51e-108">テスト セットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3d51e-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="3d51e-109">クライアント プロジェクトから ASP.NET クライアント コードを削除します。</span><span class="sxs-lookup"><span data-stu-id="3d51e-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="3d51e-110">このコードは、WSDL.exe ツールを使用して生成したモジュールにあります。</span><span class="sxs-lookup"><span data-stu-id="3d51e-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="3d51e-111">WCF クライアントを使用してコードを生成、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d51e-111">Generate WCF client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="3d51e-112">このコードをクライアント プロジェクトに追加し、構成の出力をクライアントの既存の構成ファイルにマージします。</span><span class="sxs-lookup"><span data-stu-id="3d51e-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="3d51e-113">アプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3d51e-113">Compile the application.</span></span> <span data-ttu-id="3d51e-114">新しい WCF クライアント型への参照を以前の ASP.NET クライアント型への参照を置き換えることで、コンパイル エラーを修復します。</span><span class="sxs-lookup"><span data-stu-id="3d51e-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new WCF client types.</span></span>  
  
6.  <span data-ttu-id="3d51e-115">テスト セットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3d51e-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d51e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d51e-116">See Also</span></span>  
 [<span data-ttu-id="3d51e-117">方法 : ASP.NET Web サービス コードを Windows Communication Foundation に移行する</span><span class="sxs-lookup"><span data-stu-id="3d51e-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
