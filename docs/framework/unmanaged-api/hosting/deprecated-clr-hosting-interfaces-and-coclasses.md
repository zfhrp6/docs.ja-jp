---
title: "サポートされなくなった CLR のホスト インターフェイスおよびコクラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a4410814669ed329e477fbad13dac60103b1ac0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="67d1e-102">サポートされなくなった CLR のホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="67d1e-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="67d1e-103">このセクションの内容がアンマネージ インターフェイスについて説明しますホストを使用して、共通言語ランタイム (CLR) 統合 .NET Framework version 1.0 および 1.1 でのアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="67d1e-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="67d1e-104">これらのインターフェイスは、ホストを構成して、ランタイムをプロセスに読み込むのためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="67d1e-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67d1e-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="67d1e-105">In This Section</span></span>  
 <span data-ttu-id="67d1e-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="67d1e-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="67d1e-107">ホストを構成するためのメソッドを提供する<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="67d1e-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="67d1e-108">ICeeFileGen クラス</span><span class="sxs-lookup"><span data-stu-id="67d1e-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="67d1e-109">(非推奨)ネイティブ ポータブル実行可能 (PE) ファイルを作成するための機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="67d1e-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="67d1e-110">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67d1e-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="67d1e-111">ホストが CLR の設定を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="67d1e-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="67d1e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="67d1e-112">Related Sections</span></span>  
 [<span data-ttu-id="67d1e-113">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67d1e-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="67d1e-114">ホストに以降のバージョンと .NET Framework version 2.0 で提供されるインターフェイスを説明するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="67d1e-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
