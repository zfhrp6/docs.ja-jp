---
title: ホスト インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2bef9e1671b8487a6702cce71106c84a2984317
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436161"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="3f1ba-102">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f1ba-102">Hosting Interfaces</span></span>
<span data-ttu-id="3f1ba-103">このセクションの内容がアンマネージ インターフェイスについて説明しますホストを使用して、共通言語ランタイム (CLR) をアプリケーションに統合します。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="3f1ba-104">.NET Framework version 2.0 のホスト インターフェイスは、.NET Framework version 1.0 および 1.1 インターフェイスに優先します。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="3f1ba-105">インターフェイスの 2 つのセット間に大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="3f1ba-106">両者を混在させると、予期しない動作が発生する可能性があります、お勧めできません。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="3f1ba-107">.NET Framework バージョン 3.0 および 3.5 は .NET Framework version 2.0 のホスト インターフェイスを使用し、ホスティング機能を導入していません。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="3f1ba-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]ホスト インターフェイスは、.NET Framework 2.0 インターフェイスをよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="3f1ba-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3f1ba-109">In This Section</span></span>  
 <span data-ttu-id="3f1ba-110">
  [非推奨の CLR のホスト インターフェイスおよびコクラス](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="3f1ba-110">[Deprecated CLR Hosting Interfaces and Coclasses](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)</span></span>  
 <span data-ttu-id="3f1ba-111">.NET Framework のバージョン 1.0 および 1.1 で導入されたホスト インターフェイスをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="3f1ba-112">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f1ba-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="3f1ba-113">.NET Framework version 2.0 で導入されたホスト インターフェイスをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="3f1ba-114">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f1ba-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="3f1ba-115">導入されたホスティング インターフェイスについて説明します、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="3f1ba-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3f1ba-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f1ba-116">Related Sections</span></span>  
 [<span data-ttu-id="3f1ba-117">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="3f1ba-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 <span data-ttu-id="3f1ba-118">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="3f1ba-118">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>  
  
 [<span data-ttu-id="3f1ba-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="3f1ba-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="3f1ba-120">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="3f1ba-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="3f1ba-121">ホスティング</span><span class="sxs-lookup"><span data-stu-id="3f1ba-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="3f1ba-122">ランタイム ホスト</span><span class="sxs-lookup"><span data-stu-id="3f1ba-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)
