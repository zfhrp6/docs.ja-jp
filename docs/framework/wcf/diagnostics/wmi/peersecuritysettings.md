---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48a9cc5a7a05b47a5589d1bf9a730184fb7f0543
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="2e4aa-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2e4aa-102">PeerSecuritySettings</span></span>
<span data-ttu-id="2e4aa-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2e4aa-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e4aa-104">構文</span><span class="sxs-lookup"><span data-stu-id="2e4aa-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2e4aa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2e4aa-105">Methods</span></span>  
 <span data-ttu-id="2e4aa-106">PeerSecuritySettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="2e4aa-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2e4aa-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2e4aa-107">Properties</span></span>  
 <span data-ttu-id="2e4aa-108">PeerSecuritySettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2e4aa-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="2e4aa-109">モード</span><span class="sxs-lookup"><span data-stu-id="2e4aa-109">Mode</span></span>  
 <span data-ttu-id="2e4aa-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="2e4aa-110">Data type: string</span></span>  
  
 <span data-ttu-id="2e4aa-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2e4aa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e4aa-112">このバインディングで構成されたエンドポイントによって、メッセージ レベルおよびトランスポート レベルのセキュリティが使用されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="2e4aa-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="2e4aa-113">Transport</span><span class="sxs-lookup"><span data-stu-id="2e4aa-113">Transport</span></span>  
 <span data-ttu-id="2e4aa-114">データ型 : PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2e4aa-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="2e4aa-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2e4aa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e4aa-116">トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="2e4aa-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e4aa-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="2e4aa-117">Requirements</span></span>  
  
|<span data-ttu-id="2e4aa-118">MOF</span><span class="sxs-lookup"><span data-stu-id="2e4aa-118">MOF</span></span>|<span data-ttu-id="2e4aa-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="2e4aa-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2e4aa-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="2e4aa-120">Namespace</span></span>|<span data-ttu-id="2e4aa-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="2e4aa-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e4aa-122">参照</span><span class="sxs-lookup"><span data-stu-id="2e4aa-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
