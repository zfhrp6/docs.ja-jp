---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 58b372f26fee7dc180d75731fd4855db569c87c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="peersecuritysettings"></a><span data-ttu-id="831be-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="831be-102">PeerSecuritySettings</span></span>
<span data-ttu-id="831be-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="831be-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="831be-104">構文</span><span class="sxs-lookup"><span data-stu-id="831be-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="831be-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="831be-105">Methods</span></span>  
 <span data-ttu-id="831be-106">PeerSecuritySettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="831be-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="831be-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="831be-107">Properties</span></span>  
 <span data-ttu-id="831be-108">PeerSecuritySettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="831be-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="831be-109">モード</span><span class="sxs-lookup"><span data-stu-id="831be-109">Mode</span></span>  
 <span data-ttu-id="831be-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="831be-110">Data type: string</span></span>  
  
 <span data-ttu-id="831be-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="831be-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="831be-112">このバインディングで構成されたエンドポイントによって、メッセージ レベルおよびトランスポート レベルのセキュリティが使用されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="831be-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="831be-113">Transport</span><span class="sxs-lookup"><span data-stu-id="831be-113">Transport</span></span>  
 <span data-ttu-id="831be-114">データ型 : PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="831be-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="831be-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="831be-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="831be-116">トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="831be-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="831be-117">要件</span><span class="sxs-lookup"><span data-stu-id="831be-117">Requirements</span></span>  
  
|<span data-ttu-id="831be-118">MOF</span><span class="sxs-lookup"><span data-stu-id="831be-118">MOF</span></span>|<span data-ttu-id="831be-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="831be-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="831be-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="831be-120">Namespace</span></span>|<span data-ttu-id="831be-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="831be-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="831be-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="831be-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
